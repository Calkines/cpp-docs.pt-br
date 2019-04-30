---
title: Criando operações assíncronas em C++ para aplicativos UWP
ms.date: 11/19/2018
helpviewer_keywords:
- Windows 8.x apps, creating C++ async operations
- Creating C++ async operations
ms.assetid: a57cecf4-394a-4391-a957-1d52ed2e5494
ms.openlocfilehash: 8815861e525a2824bb1bc7a7d0e40f96b053c6a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413969"
---
# <a name="creating-asynchronous-operations-in-c-for-uwp-apps"></a>Criando operações assíncronas em C++ para aplicativos UWP

Este documento descreve alguns dos principais pontos para ter em mente quando você usa a classe de tarefa para gerar operações assíncronas baseadas em Windows ThreadPool em um aplicativo de tempo de execução Universal do Windows (UWP).

O uso de programação assíncrona é um componente fundamental no modelo de aplicativo de tempo de execução do Windows porque ela permite que aplicativos continuem respondendo à entrada do usuário. Você pode iniciar uma tarefa de longa execução sem bloquear o thread de interface do usuário, e você pode receber os resultados da tarefa mais tarde. Você também pode cancelar as tarefas e receber notificações de progresso como tarefas executadas em segundo plano. O documento [programação assíncrona em C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) fornece uma visão geral do padrão assíncrono que está disponível no Visual C++ para criar aplicativos UWP. Esse documento ensina como consumir e criar cadeias de operações assíncronas de tempo de execução do Windows. Esta seção descreve como usar os tipos em ppltasks. h para gerar operações assíncronas que podem ser consumidas por outro componente de tempo de execução do Windows e como controlar o trabalho assíncrono como é executado. Também considere a leitura [padrões e dicas no Hilo (aplicativos da Windows Store usando C++ e XAML) de programação assíncrona](https://msdn.microsoft.com/library/windows/apps/jj160321.aspx) para saber mais como usamos a classe de tarefa para implementar operações assíncronas no Hilo, um aplicativo de tempo de execução do Windows usando C++ e XAML.

> [!NOTE]
>  Você pode usar o [biblioteca de padrões paralelos](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) e [biblioteca de agentes assíncronos](../../parallel/concrt/asynchronous-agents-library.md) em um aplicativo UWP. No entanto, você não pode usar o Agendador de tarefas ou o Gerenciador de recursos. Este documento descreve os recursos adicionais que fornece a PPL que estão disponíveis apenas para um aplicativo UWP e não a um aplicativo da área de trabalho.

## <a name="key-points"></a>Pontos-chave

- Use [Concurrency:: create_async](reference/concurrency-namespace-functions.md#create_async) para criar operações assíncronas que podem ser usadas por outros componentes (que podem ser escrito em linguagens diferentes de C++).

- Use [Concurrency:: progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) para notificações de progresso de relatório para componentes que chamam as operações assíncronas.

- Use tokens de cancelamento para habilitar operações assíncronas internas Cancelar.

- O comportamento do `create_async` função depende o tipo de retorno da função de trabalho que é passado para ele. Uma função de trabalho que retorna uma tarefa (tanto `task<T>` ou `task<void>`) é executado de forma síncrona no contexto de chamada `create_async`. Uma função de trabalho que retorna `T` ou `void` é executado em um contexto arbitrário.

- Você pode usar o [concurrency::task::then](reference/task-class.md#then) método para criar uma cadeia de tarefas que são executadas uma após a outra. Em um aplicativo UWP, o contexto padrão para continuações de uma tarefa depende de como essa tarefa foi construída. Se a tarefa foi criada, passando uma ação assíncrona para o construtor de tarefa, ou transmitindo uma expressão lambda que retorna uma ação assíncrona, o contexto padrão para todas as continuações de tarefa é o contexto atual. Se a tarefa não é criada com uma ação assíncrona, em seguida, um contexto arbitrário é usado por padrão para continuações da tarefa. Você pode substituir o contexto padrão com o [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) classe.

## <a name="in-this-document"></a>Neste documento

- [Criando operações assíncronas](#create-async)

- [Exemplo: Criando um componente de tempo de execução do Windows C++](#example-component)

- [Controlando o Thread de execução](#exethread)

- [Exemplo: Controlando a execução em um aplicativo de tempo de execução do Windows com C++ e XAML](#example-app)

##  <a name="create-async"></a> Criando operações assíncronas

Você pode usar o modelo de tarefa e continuação em paralelo padrões biblioteca (PPL) para definir as tarefas em segundo plano, bem como tarefas adicionais que são executados quando a tarefa anterior seja concluída. Essa funcionalidade é fornecida pelos [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) classe. Para obter mais informações sobre esse modelo e o `task` classe, consulte [paralelismo de tarefas](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

O tempo de execução do Windows é uma interface de programação que você pode usar para criar aplicativos UWP que são executados somente em um ambiente especial do sistema operacional. Esses aplicativos usam funções autorizadas, tipos de dados e dispositivos, além de serem distribuídos a partir do Microsoft Store. O tempo de execução do Windows é representado pela *Interface binária de aplicativo* (ABI). A ABI é um contrato binário subjacente que torna as APIs do Windows Runtime disponíveis para linguagens de programação como Visual C++.

Ao usar o tempo de execução do Windows, você pode usar os melhores recursos de várias linguagens de programação e combiná-los em um aplicativo. Por exemplo, você pode criar sua interface do usuário em JavaScript e executar a lógica de aplicativo de computação intensa em um componente C++. A capacidade de executar essas operações de computação intensa em segundo plano é um fator importante em manter a interface do usuário responsiva. Porque o `task` classe é específico a C++, você deve usar uma interface de tempo de execução do Windows para se comunicar operações assíncronas para outros componentes (que podem ser escritos em linguagens diferentes do C++). O tempo de execução do Windows fornece quatro interfaces que você pode usar para representar operações assíncronas:

[Windows::Foundation::IAsyncAction](/uwp/api/windows.foundation.iasyncaction)<br/>
Representa uma ação assíncrona.

[Windows::Foundation::IAsyncActionWithProgress\<TProgress>](https://msdn.microsoft.com/library/windows/apps/br206581.aspx)<br/>
Representa uma ação assíncrona que relata o progresso.

[Windows::Foundation::IAsyncOperation\<TResult>](https://msdn.microsoft.com/library/windows/apps/br206598.aspx)<br/>
Representa uma operação assíncrona que retorna um resultado.

[Windows::Foundation::IAsyncOperationWithProgress\<TResult, TProgress>](https://msdn.microsoft.com/library/windows/apps/br206594.aspx)<br/>
Representa uma operação assíncrona que retorna um resultado e relatórios de progresso.

A noção de um *ação* significa que a tarefa assíncrona não produz um valor (pense em uma função que retorna `void`). A noção de um *operação* significa que a tarefa assíncrona produzir um valor. A noção de *andamento* significa que a tarefa possa relatar mensagens de andamento ao chamador. JavaScript, o .NET Framework e Visual C++ fornece sua própria maneira de criar instâncias dessas interfaces para uso pelo limite da ABI. Para o Visual C++, a PPL fornece o [Concurrency:: create_async](reference/concurrency-namespace-functions.md#create_async) função. Essa função cria uma operação que representa a conclusão de uma tarefa ou ação assíncrona do tempo de execução do Windows. O `create_async` função usa uma função de trabalho (normalmente uma expressão lambda), cria internamente uma `task` objeto e o encapsula em uma das quatro interfaces de tempo de execução do Windows assíncronas de tarefa.

> [!NOTE]
>  Use `create_async` somente quando for necessário criar a funcionalidade que pode ser acessada de outro componente de tempo de execução do Windows ou de outro idioma. Use o `task` diretamente quando você sabe que a operação foi produzida e consumida pelo código do C++ no mesmo componente de classe.

O tipo de retorno de `create_async` é determinado pelo tipo dos seus argumentos. Por exemplo, se sua função de trabalho não retorna um valor e não informam o andamento, `create_async` retorna `IAsyncAction`. Se sua função de trabalho não retorna um valor e também relata o andamento, `create_async` retorna `IAsyncActionWithProgress`. Para relatar o andamento, forneça uma [Concurrency:: progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) objeto como parâmetro para sua função de trabalho. A capacidade de relatar o progresso permite que você relate que quantidade de trabalho foi executada e qual o valor ainda permanece (por exemplo, como uma porcentagem). Ele também permite relatar os resultados conforme eles ficam disponíveis.

As interfaces `IAsyncAction`, `IAsyncActionWithProgress<TProgress>`, `IAsyncOperation<TResult>` e `IAsyncActionOperationWithProgress<TProgress, TProgress>` fornecem um método `Cancel` que permite cancelar a operação assíncrona. O `task` classe funciona com tokens de cancelamento. Quando você usa um token de cancelamento para cancelar o trabalho, o tempo de execução não inicia um novo trabalho assina esse token. Trabalho que já está ativo pode monitorar seu token de cancelamento e interromper quando for possível. Esse mecanismo é descrito mais detalhadamente no documento [cancelamento no PPL](cancellation-in-the-ppl.md). Você pode conectar o cancelamento da tarefa com o tempo de execução do Windows`Cancel` métodos de duas maneiras. Primeiro, você pode definir a função de trabalho que você passa para `create_async` tirar uma [cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) objeto. Quando o `Cancel` método é chamado, esse token de cancelamento é cancelado, e as regras de cancelamento normais são aplicadas subjacente `task` objeto compatível com o `create_async` chamar. Se você não fornecer um objeto `cancellation_token`, o objeto `task` subjacente define um de forma implícita. Defina um objeto `cancellation_token` quando você precisa responder de forma cooperativa ao cancelamento na sua função de trabalho. A seção [exemplo: Controlando a execução em um App do tempo de execução do Windows com C++ e XAML](#example-app) mostra um exemplo de como executar o cancelamento em um aplicativo da plataforma Universal do Windows (UWP) com C# e XAML que usa um componente C++ do tempo de execução Windows personalizado.

> [!WARNING]
>  Em uma cadeia de continuação de tarefas, sempre Limpar estado e, em seguida, chame [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) quando o token de cancelamento é cancelado. Se você retornar antecipadamente em vez de chamar `cancel_current_task`, as transições de operação para o estado concluído, em vez do estado cancelado.

A tabela a seguir resume as combinações que você pode usar para definir as operações assíncronas em seu aplicativo.

|Para criar a interface de tempo de execução do Windows|Retornar esse tipo de `create_async`|Transmitir esses tipos de parâmetro para sua função de trabalho usar um token de cancelamento implícito|Transmitir esses tipos de parâmetro para sua função de trabalho usar um token de cancelamento explícita|
|----------------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|`IAsyncAction`|`void` ou `task<void>`|(nenhum)|(`cancellation_token`)|
|`IAsyncActionWithProgress<TProgress>`|`void` ou `task<void>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|
|`IAsyncOperation<TResult>`|`T` ou `task<T>`|(nenhum)|(`cancellation_token`)|
|`IAsyncActionOperationWithProgress<TProgress, TProgress>`|`T` ou `task<T>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|

Você pode retornar um valor ou uma `task` objeto da função de trabalho que você passa para o `create_async` função. Essas variações produzem comportamentos diferentes. Quando você retorna um valor, a função de trabalho é encapsulada em um `task` para que ele pode ser executado em um thread em segundo plano. Além disso, subjacente `task` usa um token de cancelamento implícito. Por outro lado, se você retornar um `task` do objeto, a função de trabalho é executada de forma síncrona. Portanto, se você retornar um `task` de objeto, certifique-se de que quaisquer operações demoradas em sua função de trabalho também executados como tarefas para habilitar seu aplicativo permaneça responsivo. Além disso, subjacente `task` não usa um token de cancelamento implícito. Portanto, você precisará definir sua função de trabalho para tirar uma `cancellation_token` do objeto se você precisa de suporte para cancelamento quando você retornar um `task` do objeto de `create_async`.

O exemplo a seguir mostra várias maneiras de criar um `IAsyncAction` objeto que pode ser consumido por outro componente de tempo de execução do Windows.

[!code-cpp[concrt-windowsstore-primes#100](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_1.cpp)]

##  <a name="example-component"></a> Exemplo: Criando um componente de tempo de execução do Windows C++ e consumindo-o deC#

Considere um aplicativo que usa XAML e c# para definir a interface do usuário e um componente de tempo de execução do C++ Windows para executar operações de computação intensiva. Neste exemplo, o componente C++ calcula os números em um determinado intervalo são primo. Para ilustrar as diferenças entre as quatro interfaces de tarefa assíncrona do tempo de execução do Windows, começar, no Visual Studio, criando uma **solução em branco** e nomeá-lo `Primes`. Em seguida, adicione à solução um **componente de tempo de execução do Windows** do projeto e nomeá-lo `PrimesLibrary`. Adicione o seguinte código para o arquivo de cabeçalho gerado do C++ (Este exemplo renomeia Class1.h para Primes.h). Cada `public` método define uma das quatro interfaces assíncronas. Os métodos que retornam um valor retornam um [Windows::Foundation::Collections::IVector\<int >](/uwp/api/Windows.Foundation.Collections.IVector_T_) objeto. Os métodos que informam o andamento produzem `double` valores que definem a porcentagem do trabalho geral que foi concluída.

[!code-cpp[concrt-windowsstore-primes#1](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_2.h)]

> [!NOTE]
>  Por convenção, os nomes de método assíncrono no tempo de execução do Windows geralmente terminam com "Async".

Adicione o seguinte código para o arquivo de origem C++ gerado (Este exemplo renomeia Class1.cpp para Primes.cpp). O `is_prime` função determina se a sua entrada é primo. Implementam os métodos restantes de `Primes` classe. Cada chamada para `create_async` usa uma assinatura que é compatível com o método do qual ele é chamado. Por exemplo, porque `Primes::ComputePrimesAsync` retorna `IAsyncAction`, a função de trabalho que é fornecida ao `create_async` não retorna um valor e não leva um `progress_reporter` objeto como seu parâmetro.

[!code-cpp[concrt-windowsstore-primes#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_3.cpp)]

Cada método primeiro executa validação para garantir que os parâmetros de entrada sejam não-negativo. Se um valor de entrada for negativo, o método gerará [Platform:: invalidargumentexception](https://msdn.microsoft.com/library/windows/apps/hh755794.aspx). Tratamento de erros é explicado mais adiante nesta seção.

Para consumir esses métodos de um aplicativo UWP, use o Visual c# **aplicativo em branco (XAML)** modelo para adicionar um segundo projeto à solução do Visual Studio. Este exemplo denomina o projeto `Primes`. Em seguida, na `Primes` do projeto, adicione uma referência para o `PrimesLibrary` projeto.

Adicione o seguinte código para MainPage. XAML. Esse código define a interface do usuário para que você possa chamar o componente C++ e exibir os resultados.

[!code-xml[concrt-windowsstore-primes#3](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_4.xaml)]

Adicione o seguinte código para o `MainPage` classe em MainPage. XAML. Esse código define uma `Primes` objeto e os manipuladores de eventos do botão.

[!code-cs[concrt-windowsstore-primes#4](../../parallel/concrt/codesnippet/csharp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_5.cs)]

Esses métodos usam o `async` e `await` palavras-chave para atualizar a interface do usuário depois de concluir as operações assíncronas. Para obter informações sobre codificação assíncrona em aplicativos UWP, consulte [Threading e programação assíncrona](/windows/uwp/threading-async).

O `getPrimesCancellation` e `cancelGetPrimes` métodos funcionam juntos para permitir que o usuário cancelar a operação. Quando o usuário escolhe o **cancele** botão, o `cancelGetPrimes` chamadas de método [IAsyncOperationWithProgress\<TResult, TProgress >:: Cancelar](/uwp/api/windows.foundation.iasyncinfo.cancel) para cancelar a operação. O tempo de execução de simultaneidade, que gerencia a operação assíncrona subjacente, gera um tipo de exceção interna que é capturado pelo Windows Runtime para comunicar-se de que o cancelamento foi concluído. Para obter mais informações sobre o modelo de cancelamento, consulte [cancelamento](../../parallel/concrt/cancellation-in-the-ppl.md).

> [!IMPORTANT]
>  Para habilitar a PPL relatar corretamente para o tempo de execução do Windows, que ele cancelou a operação, não Capture esse tipo de exceção interna. Isso significa que você também não deve capturar todas as exceções (`catch (...)`). Se você deve capturar todas as exceções, relançar a exceção para garantir que o tempo de execução do Windows pode concluir a operação de cancelamento.

A ilustração a seguir mostra o `Primes` aplicativo depois de cada opção foi escolhida.

![Tempo de execução do Windows inicia o aplicativo](../../parallel/concrt/media/concrt_windows_primes.png "tempo de execução do Windows inicia o aplicativo")

Para obter exemplos que usam `create_async` para criar tarefas assíncronas que podem ser consumidas por outros idiomas, consulte [usando o C++ no exemplo Bing Maps Trip Optimizer](https://msdn.microsoft.com/library/windows/apps/hh699891.aspx) e [operações assíncronas do Windows 8 em C++ com PPL](http://code.msdn.microsoft.com/windowsapps/windows-8-asynchronous-08009a0d).

##  <a name="exethread"></a> Controlando o Thread de execução

O tempo de execução do Windows usa o modelo de threading COM. Nesse modelo, os objetos são hospedados em apartments diferentes, dependendo de como eles lidam com suas sincronizações. Objetos thread-safe são hospedados no multi-threaded apartment (MTA). Objetos que devem ser acessados por um único thread são hospedados em um single-threaded apartment (STA).

Em um aplicativo que tem uma interface do usuário, o thread ASTA (aplicativo STA) é responsável por bombeando mensagens de janela e é o único thread no processo que pode atualizar os controles hospedados STA da interface do usuário. Isso tem duas consequências. Primeiro, para permitir que o aplicativo permaneça responsivo, todas as operações de e/s e de uso intensivo de CPU devem não ser executadas no thread de ASTA. Em segundo lugar, os resultados que vêm de threads em segundo plano devem ser empacotados para de ASTA para atualizar a interface do usuário. Em um aplicativo UWP em C++, `MainPage` e todas as outras páginas de XAML é executado no ATSA. Portanto, o continuações de tarefa que são declaradas em de ASTA são executadas lá por padrão, para que você possa atualizar os controles diretamente no corpo da continuação. No entanto, caso você aninhe uma tarefa em outra tarefa, todas as continuações nessa tarefa aninhada é executado no MTA. Portanto, você precisa considerar se deve especificar explicitamente em que contexto executar esses continuações.

Uma tarefa que é criada a partir de uma operação assíncrona, como `IAsyncOperation<TResult>`, usa semântica especial que pode ajudar você a ignora os detalhes de threads. Embora uma operação pode ser executado em um thread em segundo plano (ou ele não pode ser feito por um thread em todos os), suas continuações são, por padrão, certamente será executado no apartment que a continuação de operações iniciadas (em outras palavras, do apartment que chamou `task::then`). Você pode usar o [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) classe para controlar o contexto de execução de uma continuação. Use esses métodos auxiliares estáticos para criar `task_continuation_context` objetos:

- Use [concurrency::task_continuation_context::use_arbitrary](reference/task-continuation-context-class.md#use_arbitrary) para especificar que a continuação é executada em um thread em segundo plano.

- Use [concurrency::task_continuation_context::use_current](reference/task-continuation-context-class.md#use_current) para especificar que a continuação é executada no thread que chamou `task::then`.

Você pode passar uma `task_continuation_context` do objeto para o [Task:: Then](reference/task-class.md#then) método para controlar explicitamente o contexto de execução de continuação ou você pode passar a tarefa para outra apartment e, em seguida, chamar o `task::then` método para controlar implicitamente o contexto de execução.

> [!IMPORTANT]
>  Como o thread de interface do usuário principal de aplicativos UWP são executados em STA, continuações que você cria nesse STA por padrão é executado no STA. Da mesma forma, as continuações que você cria no MTA executar em MTA.

A seção a seguir mostra um aplicativo que lê um arquivo do disco, localiza as palavras mais comuns nesse arquivo e, em seguida, mostra os resultados na interface do usuário. A operação final, atualizando a interface do usuário ocorre no thread da interface do usuário.

> [!IMPORTANT]
> Esse comportamento é específico para aplicativos UWP. Para aplicativos da área de trabalho, você não controlar onde as continuações é executado. Em vez disso, o agendador escolherá um thread de trabalho no qual executar cada continuação.

> [!IMPORTANT]
> Não chame [concurrency::task::wait](reference/task-class.md#wait) no corpo de uma continuação que é executado no STA. Caso contrário, o tempo de execução gera [Concurrency:: invalid_operation](../../parallel/concrt/reference/invalid-operation-class.md) porque esse método bloqueia o thread atual e pode fazer com que o aplicativo pare de responder. No entanto, você pode chamar o [concurrency::task::get](reference/task-class.md#get) método para receber o resultado da tarefa antecedente em uma continuação baseada em tarefa.

##  <a name="example-app"></a> Exemplo: Controlando a execução em um aplicativo de tempo de execução do Windows com C++ e XAML

Considere um aplicativo XAML de C++ que lê um arquivo do disco, localiza as palavras mais comuns nesse arquivo e, em seguida, mostra os resultados na interface do usuário. Para criar esse aplicativo, iniciar, no Visual Studio, criando uma **aplicativo em branco (Universal Windows)** do projeto e nomeá-lo `CommonWords`. Em seu manifesto de aplicativo, especifique o **biblioteca de documentos** capacidade de permitir que o aplicativo acessar a pasta de documentos. Adicione também o tipo de arquivo de texto (. txt) à seção declarations do manifesto do aplicativo. Para obter mais informações sobre os recursos de aplicativo e declarações, consulte [pacotes de aplicativos e implantação](https://msdn.microsoft.com/library/windows/apps/hh464929.aspx).

Atualizar o `Grid` elemento em MainPage. XAML para incluir uma `ProgressRing` elemento e um `TextBlock` elemento. O `ProgressRing` indica que a operação está em andamento e o `TextBlock` mostra os resultados do cálculo.

[!code-xml[concrt-windowsstore-commonwords#1](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_6.xaml)]

Adicione o seguinte `#include` instruções para pch. h.

[!code-cpp[concrt-windowsstore-commonwords#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_7.h)]

Adicione as seguintes declarações de método para o `MainPage` classe (MainPage).

[!code-cpp[concrt-windowsstore-commonwords#3](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_8.h)]

Adicione o seguinte `using` instruções MainPage.cpp.

[!code-cpp[concrt-windowsstore-commonwords#4](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_9.cpp)]

Em MainPage.cpp, implemente a `MainPage::MakeWordList`, `MainPage::FindCommonWords`, e `MainPage::ShowResults` métodos. O `MainPage::MakeWordList` e `MainPage::FindCommonWords` executar operações de computação intensa. O `MainPage::ShowResults` método exibe o resultado da computação na interface do usuário.

[!code-cpp[concrt-windowsstore-commonwords#5](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_10.cpp)]

Modificar a `MainPage` construtor para criar uma cadeia de tarefas de continuação que exibe na interface do usuário as palavras comuns no livro *a Ilíada* por Homero. As primeiras tarefas de continuação de dois, qual dividir o texto em palavras individuais e encontrar palavras comuns, podem ser demoradas e, portanto, são explicitamente definidas para execução em segundo plano. A tarefa de continuação final, que atualiza a interface do usuário, não especifica nenhum contexto de continuação e, portanto, segue o apartment threading regras.

[!code-cpp[concrt-windowsstore-commonwords#6](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_11.cpp)]

> [!NOTE]
>  Este exemplo demonstra como especificar os contextos de execução e como compor uma cadeia de continuações. Lembre-se de que, por padrão uma tarefa criada por meio de uma operação assíncrona executa suas continuações no apartment que chamou `task::then`. Portanto, este exemplo usa `task_continuation_context::use_arbitrary` para especificar que as operações que não envolvem a interface do usuário seja executada em um thread em segundo plano.

A ilustração a seguir mostra os resultados do `CommonWords` aplicativo.

![Aplicativo do Windows Runtime CommonWords](../../parallel/concrt/media/concrt_windows_common_words.png "Windows CommonWords de tempo de execução de aplicativo")

Neste exemplo, é possível oferecer suporte ao cancelamento, porque o `task` objetos que dão suporte ao `create_async` usar um token de cancelamento implícito. Definir sua função de trabalho para tirar uma `cancellation_token` objeto se suas tarefas precisam responder ao cancelamento de forma cooperativa. Para obter mais informações sobre cancelamento no PPL, consulte [cancelamento no PPL](cancellation-in-the-ppl.md)

## <a name="see-also"></a>Consulte também

[Tempo de Execução de Simultaneidade](../../parallel/concrt/concurrency-runtime.md)
