---
title: '&lt;future&gt;'
ms.date: 11/04/2016
f1_keywords:
- <future>
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
ms.openlocfilehash: d33b67ed17a95b6717878aaca2f61682b1807c15
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454003"
---
# <a name="ltfuturegt"></a>&lt;future&gt;

Inclua o cabeçalho padrão \<future> para definir classes de modelos e modelos de suporte que simplificam a execução de uma função — possivelmente em um thread separado — e a recuperação de seu resultado. O resultado é o valor retornado pela função ou uma exceção que é emitida pela função, mas não é capturada na função.

Esse cabeçalho usa ConcRT (Tempo de Execução de Simultaneidade) para que você possa usá-lo juntamente com outros mecanismos ConcRT. Para obter mais informações sobre o ConcRT, consulte [Tempo de execução de simultaneidade](../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Sintaxe

```cpp
#include <future>
```

## <a name="remarks"></a>Comentários

> [!NOTE]
> No código que é compilado usando **/CLR**, esse cabeçalho é bloqueado.

Um *provedor assíncrono* armazena o resultado de uma chamada de função. Um *objeto de retorno assíncrono* é usado para recuperar o resultado de uma chamada de função. Um *estado assíncrono associado* fornece comunicação entre um provedor assíncrono e um ou mais objetos de retorno assíncronos.

Um programa não cria diretamente nenhum objetos de estado assíncrono associado. O programa cria um provedor assíncrono sempre que precisa de um e, por meio dele, cria um objeto de retorno assíncrono que compartilha seu estado assíncrono associado com o provedor. Provedores assíncronos e objetos de retorno assíncronos gerenciam os objetos que mantêm seu estado assíncrono associado compartilhado. Quando o último objeto que faz referência ao estado assíncrono associado o libera, o objeto que contém o estado assíncrono associado é destruído.

Um provedor assíncrono ou um objeto de retorno assíncrono sem nenhum estado assíncrono associado fica *vazio*.

Um estado assíncrono associado ficará *pronto* somente se seu provedor assíncrono tiver armazenado um valor retornado ou armazenado uma exceção.

A função de modelo `async` e as classes de modelo `promise` e `packaged_task` são provedores assíncronos. As classes de modelo `future` e `shared_future` descrevem objetos de retorno assíncronos.

`promise`Cada uma das classes de modelo, `future`e `shared_future` tem uma especialização para o tipo **void** e uma especialização parcial para armazenar e recuperar um valor por referência. Essas especializações diferem do modelo primário somente quanto às assinaturas e à semântica das funções que armazenam e recuperam o valor retornado.

As classes `future` de modelo `shared_future` e nunca são bloqueadas em seus destruidores, exceto em um caso que seja preservado para compatibilidade com versões anteriores: Ao contrário de todos os outros futuros, `future`para um — ou `shared_future`o último — que está anexado a uma tarefa `std::async`iniciada com o, o destruidor bloqueia se a tarefa não foi concluída; ou seja, bloqueia se esse thread ainda `.get()` não chamou ou `.wait()`e a tarefa ainda está em execução. A seguinte observação de usabilidade foi adicionada à descrição de `std::async` no padrão de rascunho: "[Observação: Se um futuro obtido a partir de std:: Async for movido para fora do escopo local, outro código que usa o futuro deve estar ciente de que o destruidor futuro pode impedir que o estado compartilhado se torne pronto. — fim da nota] "em `future` todos `shared_future` os outros casos e os destruidores são necessários e garantem que nunca sejam bloqueados.

## <a name="members"></a>Membros

### <a name="classes"></a>Classes

|Nome|Descrição|
|----------|-----------------|
|[Classe future](../standard-library/future-class.md)|Descreve um objeto de retorno assíncrono.|
|[Classe future_error](../standard-library/future-error-class.md)|Descreve um objeto de exceção que pode ser gerado por métodos de tipos que gerenciam objetos `future`.|
|[Classe packaged_task](../standard-library/packaged-task-class.md)|Descreve um provedor assíncrono que é um wrapper de chamada e cuja assinatura de chamada é `Ty(ArgTypes...)`. O estado assíncrono associado mantém uma cópia de seu objeto que pode ser chamado, bem como o possível resultado.|
|[Classe promise](../standard-library/promise-class.md)|Descreve um provedor assíncrono.|
|[Classe shared_future](../standard-library/shared-future-class.md)|Descreve um objeto de retorno assíncrono. Diferente de um objeto `future`, um provedor assíncrono pode ser associado a qualquer quantidade de objetos `shared_future`.|

### <a name="structures"></a>Estruturas

|Nome|Descrição|
|----------|-----------------|
|[Estrutura is_error_code_enum](../standard-library/is-error-code-enum-structure.md)|Especialização que indica que `future_errc` é adequado para armazenar um `error_code`.|
|[Estrutura uses_allocator](../standard-library/uses-allocator-structure.md)|Especialização que sempre se aplica.|

### <a name="functions"></a>Funções

|Nome|Descrição|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|Representa um provedor assíncrono.|
|[future_category](../standard-library/future-functions.md#future_category)|Retorna uma referência ao objeto `error_category` que caracteriza erros associados a objetos `future`.|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|Cria um `error_code` que tem o objeto `error_category` que caracteriza erros `future`.|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|Cria um `error_condition` que tem o objeto `error_category` que caracteriza erros `future`.|
|[swap](../standard-library/future-functions.md#swap)|Troca o estado assíncrono associado de um objeto `promise` pelo de outro objeto.|

### <a name="enumerations"></a>Enumerações

|Nome|Descrição|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|Fornece nomes simbólicos para os erros relatados pela classe `future_error`.|
|[future_status](../standard-library/future-enums.md#future_status)|Fornece nomes simbólicos para os motivos que uma função de espera temporizada pode retornar.|
|[launch](../standard-library/future-enums.md#launch)|Representa um tipo de bitmask que descreve os modos possíveis para a função de modelo `async`.|

## <a name="see-also"></a>Consulte também

[Referência de Arquivos de Cabeçalho](../standard-library/cpp-standard-library-header-files.md)
