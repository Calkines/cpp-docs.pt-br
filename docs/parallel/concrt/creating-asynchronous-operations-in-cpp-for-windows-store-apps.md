---
title: Criando operações assíncronas no C++ para aplicativos UWP
ms.date: 11/19/2018
helpviewer_keywords:
- Windows 8.x apps, creating C++ async operations
- Creating C++ async operations
ms.assetid: a57cecf4-394a-4391-a957-1d52ed2e5494
ms.openlocfilehash: e3a5b634eb22a6860fe8af5b3b737a8e649e03c2
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631734"
---
# <a name="creating-asynchronous-operations-in-c-for-uwp-apps"></a>Criando operações assíncronas no C++ para aplicativos UWP

Este documento descreve alguns dos principais pontos a serem considerados quando você usa a classe Task para produzir operações assíncronas baseadas em ThreadPool do Windows em um aplicativo UWP (Universal Windows Runtime).

O uso da programação assíncrona é um componente fundamental do modelo de aplicativo Windows Runtime porque permite que os aplicativos permaneçam responsivos à entrada do usuário. Você pode iniciar uma tarefa de execução longa sem bloquear o thread da interface do usuário e pode receber os resultados da tarefa mais tarde. Você também pode cancelar tarefas e receber notificações de progresso conforme as tarefas são executadas em segundo plano. A [programação assíncrona de C++ documentos no](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) fornece uma visão geral do padrão assíncrono que está disponível no Visual C++ para criar aplicativos UWP. Esse documento ensina como consumir e criar cadeias de operações de Windows Runtime assíncronas. Esta seção descreve como usar os tipos em ppltasks. h para produzir operações assíncronas que podem ser consumidas por outro componente Windows Runtime e como controlar como o trabalho assíncrono é executado. Considere também a leitura de [padrões de programação assíncrona e dicas em Hilo ( C++ aplicativos da Windows Store usando e XAML)](/previous-versions/windows/apps/jj160321(v=win.10)) para saber como usamos a classe Task para implementar operações assíncronas no C++ Hilo, um aplicativo Windows Runtime usando o e o XAML.

> [!NOTE]
>  Você pode usar a PPL ( [biblioteca de padrões paralelos](../../parallel/concrt/parallel-patterns-library-ppl.md) ) e a [biblioteca de agentes assíncronos](../../parallel/concrt/asynchronous-agents-library.md) em um aplicativo UWP. No entanto, você não pode usar o Agendador de Tarefas ou o Gerenciador de recursos. Este documento descreve os recursos adicionais que a PPL fornece que estão disponíveis apenas para um aplicativo UWP, e não para um aplicativo de desktop.

## <a name="key-points"></a>Pontos-chave

- Use [Concurrency:: create_async](reference/concurrency-namespace-functions.md#create_async) para criar operações assíncronas que podem ser usadas por outros componentes (que podem ser escritos em idiomas C++diferentes de).

- Usar [simultaneidade::p rogress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) para relatar notificações de progresso para componentes que chamam suas operações assíncronas.

- Use tokens de cancelamento para permitir que operações assíncronas internas sejam canceladas.

- O comportamento da `create_async` função depende do tipo de retorno da função de trabalho que é passada para ele. Uma função de trabalho que retorna uma tarefa ( `task<T>` ou `task<void>`) é executada de forma síncrona no contexto `create_async`que chamou. Uma função de trabalho que `T` retorna `void` ou é executada em um contexto arbitrário.

- Você pode usar o método [Concurrency:: Task:: then](reference/task-class.md#then) para criar uma cadeia de tarefas que executa uma após a outra. Em um aplicativo UWP, o contexto padrão para as continuaçãos de uma tarefa depende de como essa tarefa foi construída. Se a tarefa foi criada passando uma ação assíncrona para o construtor da tarefa ou passando uma expressão lambda que retorna uma ação assíncrona, o contexto padrão para todas as continuaçãos dessa tarefa é o contexto atual. Se a tarefa não for construída a partir de uma ação assíncrona, um contexto arbitrário será usado por padrão para as continuaçãos da tarefa. Você pode substituir o contexto padrão pela classe [Concurrency:: task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) .

## <a name="in-this-document"></a>Neste documento

- [Criando operações assíncronas](#create-async)

- [Exemplo: Criando um C++ componente Windows Runtime](#example-component)

- [Controlando o thread de execução](#exethread)

- [Exemplo: Controlando a execução em um aplicativo C++ Windows Runtime com o e o XAML](#example-app)

##  <a name="create-async"></a>Criando operações assíncronas

Você pode usar o modelo de tarefa e continuação na PPL (biblioteca de padrões paralelos) para definir tarefas em segundo plano, bem como tarefas adicionais que são executadas quando a tarefa anterior é concluída. Essa funcionalidade é fornecida pela classe [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) . Para obter mais informações sobre esse modelo e `task` a classe, consulte [paralelismo de tarefas](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

O Windows Runtime é uma interface de programação que você pode usar para criar aplicativos UWP que são executados somente em um ambiente de sistema operacional especial. Esses aplicativos usam funções autorizadas, tipos de dados e dispositivos e são distribuídos do Microsoft Store. O Windows Runtime é representado pela Abi ( *interface binária do aplicativo* ). A ABI é um contrato binário subjacente que torna Windows Runtime APIs disponíveis para linguagens de programação, C++como Visual.

Usando o Windows Runtime, você pode usar os melhores recursos de várias linguagens de programação e combiná-los em um único aplicativo. Por exemplo, você pode criar sua interface do usuário em JavaScript e executar a lógica de aplicativo computacionalmente intensiva C++ em um componente. A capacidade de executar essas operações computacionalmente intensivas em segundo plano é um fator fundamental para manter sua interface do usuário responsiva. Como a `task` classe é específica para C++o, você deve usar uma interface Windows Runtime para comunicar operações assíncronas com outros componentes (que podem ser escritos em C++linguagens diferentes de). O Windows Runtime fornece quatro interfaces que você pode usar para representar operações assíncronas:

[Windows::Foundation::IAsyncAction](/uwp/api/windows.foundation.iasyncaction)<br/>
Representa uma ação assíncrona.

[Windows::Foundation::IAsyncActionWithProgress\<TProgress>](/uwp/api/Windows.Foundation.IAsyncActionWithProgress_TProgress_)<br/>
Representa uma ação assíncrona que relata o progresso.

[Windows::Foundation::IAsyncOperation\<TResult>](/uwp/api/windows.foundation.iasyncoperation_tresult_)<br/>
Representa uma operação assíncrona que retorna um resultado.

[Windows::Foundation::IAsyncOperationWithProgress\<TResult, TProgress>](/uwp/api/windows.foundation.iasyncoperationwithprogress_tresult_tprogress_)<br/>
Representa uma operação assíncrona que retorna um resultado e relata o progresso.

A noção de uma *ação* significa que a tarefa assíncrona não produz um valor (imagine uma função que retorna `void`). A noção de uma *operação* significa que a tarefa assíncrona produz um valor. A noção de *progresso* significa que a tarefa pode relatar mensagens de progresso ao chamador. O JavaScript, o .NET Framework e o C++ Visual fornecem sua própria maneira de criar instâncias dessas interfaces para uso no limite da Abi. Para Visual C++, a PPL fornece a função [Concurrency:: create_async](reference/concurrency-namespace-functions.md#create_async) . Essa função cria uma ação ou operação assíncrona Windows Runtime que representa a conclusão de uma tarefa. A `create_async` função usa uma função de trabalho (normalmente uma expressão lambda), cria internamente `task` um objeto e encapsula essa tarefa em uma das quatro interfaces de Windows Runtime assíncronas.

> [!NOTE]
>  Use `create_async` somente quando precisar criar uma funcionalidade que possa ser acessada de outro idioma ou outro componente Windows Runtime. Use a `task` classe diretamente quando souber que a operação é produzida e consumida pelo C++ código no mesmo componente.

O tipo de retorno `create_async` de é determinado pelo tipo de seus argumentos. Por exemplo, se sua função de trabalho não retornar um valor e não relatar o `create_async` progresso `IAsyncAction`, o retornará. Se sua função de trabalho não retornar um valor e também relatar o `create_async` progresso `IAsyncActionWithProgress`, o retornará. Para relatar o progresso, forneça um objeto [Concurrency::p rogress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) como o parâmetro para sua função de trabalho. A capacidade de relatar o progresso permite que você relate qual quantidade de trabalho foi executada e que valor ainda resta (por exemplo, como uma porcentagem). Ele também permite que você relate os resultados conforme eles ficam disponíveis.

As interfaces `IAsyncAction`, `IAsyncActionWithProgress<TProgress>`, `IAsyncOperation<TResult>` e `IAsyncActionOperationWithProgress<TProgress, TProgress>` fornecem um método `Cancel` que permite cancelar a operação assíncrona. A `task` classe funciona com tokens de cancelamento. Quando você usa um token de cancelamento para cancelar o trabalho, o tempo de execução não inicia um novo trabalho que assina esse token. O trabalho que já está ativo pode monitorar seu token de cancelamento e parar quando puder. Esse mecanismo é descrito mais detalhadamente no [cancelamento do documento na ppl](cancellation-in-the-ppl.md). Você pode conectar o cancelamento de tarefa com`Cancel` os métodos de Windows Runtime de duas maneiras. Primeiro, você pode definir a função de trabalho que você passa `create_async` para para pegar um objeto [Concurrency:: cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) . Quando o `Cancel` método é chamado, esse token de cancelamento é cancelado e as regras normais de cancelamento `task` se aplicam ao `create_async` objeto subjacente que dá suporte à chamada. Se você não fornecer um objeto `cancellation_token`, o objeto `task` subjacente define um de forma implícita. Defina um objeto `cancellation_token` quando você precisa responder de forma cooperativa ao cancelamento na sua função de trabalho. O exemplo [de seção: Controlar a execução em um aplicativo Windows Runtime C++ com o](#example-app) e o XAML mostra um exemplo de como executar o cancelamento em um aplicativo de plataforma universal do Windows C# (UWP) com o e o C++ XAML que usa um componente Windows Runtime personalizado.

> [!WARNING]
>  Em uma cadeia de continuaçãos de tarefa, sempre Limpe o estado e, em seguida, chame [Concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) quando o token de cancelamento for cancelado. Se você retornar antecipadamente em vez `cancel_current_task`de chamar, a operação passará para o estado concluído em vez do estado cancelado.

A tabela a seguir resume as combinações que você pode usar para definir operações assíncronas em seu aplicativo.

|Para criar essa interface de Windows Runtime|Retornar este tipo de`create_async`|Passe esses tipos de parâmetro para sua função de trabalho para usar um token de cancelamento implícito|Passe esses tipos de parâmetro para sua função de trabalho para usar um token de cancelamento explícito|
|----------------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|`IAsyncAction`|`void` ou `task<void>`|(nenhum)|(`cancellation_token`)|
|`IAsyncActionWithProgress<TProgress>`|`void` ou `task<void>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|
|`IAsyncOperation<TResult>`|`T` ou `task<T>`|(nenhum)|(`cancellation_token`)|
|`IAsyncActionOperationWithProgress<TProgress, TProgress>`|`T` ou `task<T>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|

Você pode retornar um valor ou um `task` objeto da função de trabalho que você passa para a `create_async` função. Essas variações produzem comportamentos diferentes. Quando você retorna um valor, a função de trabalho é encapsulada `task` em um para que possa ser executada em um thread em segundo plano. Além disso, o subjacente `task` usa um token de cancelamento implícito. Por outro lado, se você retornar um `task` objeto, a função de trabalho será executada de forma síncrona. Portanto, se você retornar um `task` objeto, certifique-se de que as operações demoradas em sua função de trabalho também sejam executadas como tarefas para permitir que seu aplicativo permaneça responsivo. Além disso, o subjacente `task` não usa um token de cancelamento implícito. Portanto, você precisa definir sua função de trabalho para obter um `cancellation_token` objeto se precisar de suporte para cancelamento quando retornar um `task` objeto de `create_async`.

O exemplo a seguir mostra as várias maneiras de criar `IAsyncAction` um objeto que pode ser consumido por outro componente Windows Runtime.

[!code-cpp[concrt-windowsstore-primes#100](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_1.cpp)]

##  <a name="example-component"></a>Exemplo Criando um C++ componente Windows Runtime e consumindo-o deC#

Considere um aplicativo que usa XAML e C# defina a interface do usuário e C++ um componente Windows Runtime para executar operações de computação intensiva. Neste exemplo, o C++ componente computa quais números em um determinado intervalo são primos. Para ilustrar as diferenças entre as quatro Windows Runtime interfaces de tarefa assíncronas, comece, no Visual Studio, criando uma **solução em branco** e nomeando- `Primes`a. Em seguida, adicione à solução um projeto de **componente Windows Runtime** e `PrimesLibrary`nomeá-lo. Adicione o código a seguir ao arquivo C++ de cabeçalho gerado (Este exemplo renomeia Class1. h para Primes. h). Cada `public` método define uma das quatro interfaces assíncronas. Os métodos que retornam um valor retornam um objeto [Windows:: Foundation:: Collections\<:: IVector int >](/uwp/api/Windows.Foundation.Collections.IVector_T_) . Os métodos que relatam `double` o progresso produzem valores que definem a porcentagem de trabalho geral que foi concluída.

[!code-cpp[concrt-windowsstore-primes#1](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_2.h)]

> [!NOTE]
>  Por convenção, os nomes de métodos assíncronos na Windows Runtime normalmente terminam com "Async".

Adicione o código a seguir ao arquivo C++ de origem gerado (Este exemplo renomeia Class1. cpp como Primes. cpp). A `is_prime` função determina se sua entrada é primo. Os métodos restantes implementam `Primes` a classe. Cada chamada para `create_async` usa uma assinatura que é compatível com o método do qual ele é chamado. Por exemplo, como `Primes::ComputePrimesAsync` retorna `IAsyncAction`, a função de trabalho fornecida para `create_async` não retorna um valor e não pega um `progress_reporter` objeto como seu parâmetro.

[!code-cpp[concrt-windowsstore-primes#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_3.cpp)]

Primeiro, cada método executa a validação para garantir que os parâmetros de entrada sejam não negativos. Se um valor de entrada for negativo, o método lançará [Platform:: InvalidArgumentException](../../cppcx/platform-invalidargumentexception-class.md). O tratamento de erros é explicado mais adiante nesta seção.

Para consumir esses métodos de um aplicativo UWP, use o modelo C# de **aplicativo em branco Visual (XAML)** para adicionar um segundo projeto à solução do Visual Studio. Este exemplo nomeia o projeto `Primes`. Em seguida, no `Primes` projeto, adicione uma referência `PrimesLibrary` ao projeto.

Adicione o código a seguir a MainPage. XAML. Esse código define a interface do usuário para que você possa C++ chamar o componente e exibir os resultados.

[!code-xml[concrt-windowsstore-primes#3](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_4.xaml)]

Adicione o código a seguir à `MainPage` classe em MainPage. XAML. Esse código define um `Primes` objeto e os manipuladores de eventos de botão.

[!code-cs[concrt-windowsstore-primes#4](../../parallel/concrt/codesnippet/csharp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_5.cs)]

Esses métodos usam as `async` palavras `await` -chave e para atualizar a interface do usuário após a conclusão das operações assíncronas. Para obter informações sobre codificação assíncrona em aplicativos UWP, consulte [Threading e programação assíncrona](/windows/uwp/threading-async).

Os `getPrimesCancellation` métodos `cancelGetPrimes` e funcionam em conjunto para permitir que o usuário cancele a operação. Quando o usuário escolhe o botão **Cancelar** , o `cancelGetPrimes` método chama [IAsyncOperationWithProgress\<TResult, TProgress >:: Cancel](/uwp/api/windows.foundation.iasyncinfo.cancel) para cancelar a operação. O Tempo de Execução de Simultaneidade, que gerencia a operação assíncrona subjacente, gera um tipo de exceção interna que é capturado pelo Windows Runtime para comunicar que o cancelamento foi concluído. Para obter mais informações sobre o modelo de cancelamento, consulte [cancelamento](../../parallel/concrt/cancellation-in-the-ppl.md).

> [!IMPORTANT]
>  Para permitir que a PPL relate corretamente ao Windows Runtime que cancelou a operação, não Capture esse tipo de exceção interna. Isso significa que você também não deve capturar todas as exceções`catch (...)`(). Se você precisar capturar todas as exceções, relance a exceção para garantir que a Windows Runtime possa concluir a operação de cancelamento.

A ilustração a seguir mostra `Primes` o aplicativo após a escolha de cada opção.

![Windows Runtime aplicativo Primes](../../parallel/concrt/media/concrt_windows_primes.png "Windows Runtime aplicativo Primes")

Para obter exemplos que `create_async` usam o para criar tarefas assíncronas que podem ser consumidas por outras linguagens, consulte [usando C++ na exemplo do otimizador de viagens do Bing Maps](/previous-versions/windows/apps/hh699891(v=vs.140)) e nas [operações assíncronas do Windows 8 em C++ com a PPL](https://code.msdn.microsoft.com/windowsapps/windows-8-asynchronous-08009a0d).

##  <a name="exethread"></a>Controlando o thread de execução

O Windows Runtime usa o modelo de Threading COM. Nesse modelo, os objetos são hospedados em diferentes Apartments, dependendo de como eles lidam com sua sincronização. Os objetos thread-safe são hospedados no MTA (multi-threaded apartment). Os objetos que devem ser acessados por um único thread são hospedados em um STA (single-threaded apartment).

Em um aplicativo que tem uma interface do usuário, o thread ASTA (Application STA) é responsável por bombear mensagens de janela e é o único thread no processo que pode atualizar os controles de interface do usuário hospedados no STA. Isso tem duas conseqüências. Primeiro, para permitir que o aplicativo permaneça responsivo, todas as operações de e/s intensivas de CPU não devem ser executadas no thread ASTA. Segundo, os resultados provenientes de threads em segundo plano devem ser empacotados de volta para o ASTA para atualizar a interface do usuário. Em um C++ aplicativo UWP, `MainPage` todas as páginas XAML são executadas no ATSA. Portanto, as continuações de tarefa declaradas no ASTA são executadas lá por padrão para que você possa atualizar os controles diretamente no corpo de continuação. No entanto, se você aninhar uma tarefa em outra tarefa, qualquer continuação nessa tarefa aninhada será executada no MTA. Portanto, você precisa considerar se deve especificar explicitamente em que contexto essas continuaçãos são executadas.

Uma tarefa que é criada a partir de uma operação assíncrona `IAsyncOperation<TResult>`, como, usa semântica especial que pode ajudá-lo a ignorar os detalhes de Threading. Embora uma operação possa ser executada em um thread em segundo plano (ou pode não ser apoiada por um thread), suas continuações são, por padrão, garantidas de serem executadas no apartamento que iniciou as operações de continuação (em outras palavras, do apartamento que chamou `task::then`). Você pode usar a classe [Concurrency:: task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) para controlar o contexto de execução de uma continuação. Use estes métodos auxiliares estáticos `task_continuation_context` para criar objetos:

- Use [Concurrency:: task_continuation_context:: use_arbitrary](reference/task-continuation-context-class.md#use_arbitrary) para especificar que a continuação é executada em um thread em segundo plano.

- Use [Concurrency:: task_continuation_context:: use_current](reference/task-continuation-context-class.md#use_current) para especificar que a continuação é executada no thread que chamou `task::then`.

Você pode passar um `task_continuation_context` objeto para o método [Task:: then](reference/task-class.md#then) para controlar explicitamente o contexto de execução da continuação ou pode passar a tarefa para outro Apartment e, em seguida, `task::then` chamar o método para controlar implicitamente o contexto de execução .

> [!IMPORTANT]
>  Como o thread da interface do usuário principal dos aplicativos UWP é executado sob STA, as continuações criadas nesse STA por padrão são executadas no STA. Da mesma forma, as continuações criadas no MTA são executadas no MTA.

A seção a seguir mostra um aplicativo que lê um arquivo do disco, localiza as palavras mais comuns nesse arquivo e, em seguida, mostra os resultados na interface do usuário. A operação final, atualizando a interface do usuário, ocorre no thread da interface do usuário.

> [!IMPORTANT]
> Esse comportamento é específico para aplicativos UWP. Para aplicativos da área de trabalho, você não controla onde as continuaçãos são executadas. Em vez disso, o Agendador escolhe um thread de trabalho no qual executar cada continuação.

> [!IMPORTANT]
> Não chamar [Concurrency:: Task:: aguardar](reference/task-class.md#wait) no corpo de uma continuação que é executada no Sta. Caso contrário, o tempo de execução lançará [Concurrency:: invalid_operation](../../parallel/concrt/reference/invalid-operation-class.md) porque esse método bloqueia o thread atual e pode fazer com que o aplicativo fique sem resposta. No entanto, você pode chamar o método [Concurrency:: Task:: Get](reference/task-class.md#get) para receber o resultado da tarefa Antecedent em uma continuação baseada em tarefa.

##  <a name="example-app"></a>Exemplo Controlando a execução em um aplicativo C++ Windows Runtime com o e o XAML

Considere um C++ aplicativo XAML que leia um arquivo do disco, encontre as palavras mais comuns nesse arquivo e, em seguida, mostre os resultados na interface do usuário. Para criar esse aplicativo, comece, no Visual Studio, criando um projeto de **aplicativo em branco (universal do Windows)** e `CommonWords`nomeando-o. No manifesto do aplicativo, especifique a capacidade da **biblioteca de documentos** para permitir que o aplicativo acesse a pasta documentos. Além disso, adicione o tipo de arquivo Text (. txt) à seção declarações do manifesto do aplicativo. Para obter mais informações sobre as declarações e os recursos do aplicativo, consulte [empacotamento, implantação e consulta de aplicativos do Windows](/windows/win32/appxpkg/appx-portal).

Atualize o `Grid` elemento em MainPage. XAML para incluir um `ProgressRing` elemento e um `TextBlock` elemento. O `ProgressRing` indica que a operação está em andamento `TextBlock` e mostra os resultados da computação.

[!code-xml[concrt-windowsstore-commonwords#1](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_6.xaml)]

Adicione as instruções `#include` a seguir a *PCH. h*.

[!code-cpp[concrt-windowsstore-commonwords#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_7.h)]

Adicione as seguintes declarações de método à `MainPage` classe (MainPage. h).

[!code-cpp[concrt-windowsstore-commonwords#3](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_8.h)]

Adicione as instruções `using` a seguir a MainPage. cpp.

[!code-cpp[concrt-windowsstore-commonwords#4](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_9.cpp)]

Em MainPage. cpp, implemente `MainPage::MakeWordList`os `MainPage::FindCommonWords`métodos, `MainPage::ShowResults` e. O `MainPage::MakeWordList` e`MainPage::FindCommonWords` o executam operações de computação intensiva. O `MainPage::ShowResults` método exibe o resultado da computação na interface do usuário.

[!code-cpp[concrt-windowsstore-commonwords#5](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_10.cpp)]

Modifique o `MainPage` Construtor para criar uma cadeia de tarefas de continuação que é exibida na interface do usuário as palavras comuns no livro *The iLiad* by Homer. As duas primeiras tarefas de continuação, que dividem o texto em palavras individuais e localizam palavras comuns, podem ser demoradas e, portanto, definidas explicitamente para serem executadas em segundo plano. A tarefa de continuação final, que atualiza a interface do usuário, não especifica nenhum contexto de continuação e, portanto, segue as regras de threading de apartamento.

[!code-cpp[concrt-windowsstore-commonwords#6](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_11.cpp)]

> [!NOTE]
>  Este exemplo demonstra como especificar contextos de execução e como compor uma cadeia de continuaçãos. Lembre-se de que, por padrão, uma tarefa que é criada a partir de uma operação assíncrona executa `task::then`suas continuaçãos no apartamento que chamou. Portanto, este exemplo usa `task_continuation_context::use_arbitrary` para especificar que as operações que não envolvem a interface do usuário sejam executadas em um thread em segundo plano.

A ilustração a seguir mostra os resultados do `CommonWords` aplicativo.

![Windows Runtime aplicativo CommonWords](../../parallel/concrt/media/concrt_windows_common_words.png "Windows Runtime aplicativo CommonWords")

Neste exemplo, é possível dar suporte ao cancelamento porque os `task` objetos que dão suporte `create_async` ao usam um token de cancelamento implícito. Defina sua função de trabalho para obter `cancellation_token` um objeto se suas tarefas precisarem responder ao cancelamento de maneira cooperativa. Para obter mais informações sobre o cancelamento na PPL, consulte [cancelamento na ppl](cancellation-in-the-ppl.md)

## <a name="see-also"></a>Consulte também

[Tempo de Execução de Simultaneidade](../../parallel/concrt/concurrency-runtime.md)
