---
title: Classe CThreadPool
ms.date: 11/04/2016
f1_keywords:
- CThreadPool
- ATLUTIL/ATL::CThreadPool
- ATLUTIL/ATL::CThreadPool::CThreadPool
- ATLUTIL/ATL::CThreadPool::AddRef
- ATLUTIL/ATL::CThreadPool::GetNumThreads
- ATLUTIL/ATL::CThreadPool::GetQueueHandle
- ATLUTIL/ATL::CThreadPool::GetSize
- ATLUTIL/ATL::CThreadPool::GetTimeout
- ATLUTIL/ATL::CThreadPool::Initialize
- ATLUTIL/ATL::CThreadPool::QueryInterface
- ATLUTIL/ATL::CThreadPool::QueueRequest
- ATLUTIL/ATL::CThreadPool::Release
- ATLUTIL/ATL::CThreadPool::SetSize
- ATLUTIL/ATL::CThreadPool::SetTimeout
- ATLUTIL/ATL::CThreadPool::Shutdown
helpviewer_keywords:
- CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
ms.openlocfilehash: 7d363de0d787ecc5015093005b39a379acd82e71
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262695"
---
# <a name="cthreadpool-class"></a>Classe CThreadPool

Essa classe fornece um pool de threads de trabalho que processam uma fila de itens de trabalho.

## <a name="syntax"></a>Sintaxe

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>Parâmetros

*Trabalhador*<br/>
A classe em conformidade com o [arquétipo de trabalhador](../../atl/reference/worker-archetype.md) fornecendo o código usado para processar itens em fila no pool de threads de trabalho.

*ThreadTraits*<br/>
A classe que fornece a função usada para criar os threads no pool.

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|O construtor para o pool de threads.|
|[CThreadPool::~CThreadPool](#dtor)|O destruidor para o pool de threads.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CThreadPool::AddRef](#addref)|Implementação de `IUnknown::AddRef`.|
|[CThreadPool::GetNumThreads](#getnumthreads)|Chame esse método para obter o número de threads no pool.|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|Chame esse método para obter o identificador de porta de conclusão de e/s usada para enfileirar itens de trabalho.|
|[CThreadPool::GetSize](#getsize)|Chame esse método para obter o número de threads no pool.|
|[CThreadPool::GetTimeout](#gettimeout)|Chame esse método para obter o tempo máximo em milissegundos que o pool de threads irá esperar por um segmento para desligar.|
|[CThreadPool::Initialize](#initialize)|Chame esse método para inicializar o pool de threads.|
|[CThreadPool::QueryInterface](#queryinterface)|Implementação de `IUnknown::QueryInterface`.|
|[CThreadPool::QueueRequest](#queuerequest)|Chame esse método para enfileirar um item de trabalho deve ser tratado por um thread no pool.|
|[CThreadPool::Release](#release)|Implementação de `IUnknown::Release`.|
|[CThreadPool::SetSize](#setsize)|Chame esse método para definir o número de threads no pool.|
|[CThreadPool::SetTimeout](#settimeout)|Chame esse método para definir o tempo máximo em milissegundos que o pool de threads irá esperar por um segmento para desligar.|
|[CThreadPool::Shutdown](#shutdown)|Chame esse método para desligar o pool de threads.|

## <a name="remarks"></a>Comentários

Threads no pool são criados e destruídos quando o pool é inicializado, redimensionado ou desligado. Uma instância da classe *trabalhador* será criado na pilha de cada thread de trabalho no pool. Cada instância ficará ativo para o tempo de vida do thread.

Imediatamente após a criação de um thread *trabalhador*::`Initialize` será chamado no objeto associado a esse thread. Imediatamente antes da destruição de um thread *trabalhador*::`Terminate` será chamado. Ambos os métodos devem aceitar uma **void** <strong>\*</strong> argumento. O valor desse argumento é passado para o pool de threads por meio de *pvWorkerParam* parâmetro do [CThreadPool::Initialize](#initialize).

Quando há itens de trabalho nos threads de fila e de trabalho disponível para o trabalho, um thread de trabalho efetuará pull de um item de fila e a chamada a `Execute` método da *trabalhador* objeto para esse thread. Três itens, em seguida, são passados para o método: o item da fila, o mesmo `pvWorkerParam` passado para *trabalhador*:: `Initialize` e *trabalho*:: `Terminate`e um ponteiro para o [OVERLAPPED](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) estrutura usada para a fila de porta de conclusão de e/s.

O *trabalhador* classe declara o tipo dos itens que serão enfileiradas no pool de threads, fornecendo um typedef *trabalhador*:: `RequestType`. Esse tipo deve ser capaz de que está sendo convertido de e para um ULONG_PTR.

Um exemplo de uma *trabalhador* classe é [classe CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md).

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atlutil

##  <a name="addref"></a>  CThreadPool::AddRef

Implementação de `IUnknown::AddRef`.

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>Valor de retorno

Sempre retorna 1.

### <a name="remarks"></a>Comentários

Essa classe não implementa o controle de tempo de vida usando a contagem de referência.

##  <a name="cthreadpool"></a>  CThreadPool::CThreadPool

O construtor para o pool de threads.

```
CThreadPool() throw();
```

### <a name="remarks"></a>Comentários

Inicializa o valor de tempo limite para ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. O tempo padrão é de 36 segundos. Se necessário, você pode definir seu próprio valor de número inteiro positivo para esse símbolo antes de incluir atlutil.

##  <a name="dtor"></a>  CThreadPool::~CThreadPool

O destruidor para o pool de threads.

```
~CThreadPool() throw();
```

### <a name="remarks"></a>Comentários

Chamadas [CThreadPool::Shutdown](#shutdown).

##  <a name="getnumthreads"></a>  CThreadPool::GetNumThreads

Chame esse método para obter o número de threads no pool.

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>Valor de retorno

Retorna o número de threads no pool.

##  <a name="getqueuehandle"></a>  CThreadPool::GetQueueHandle

Chame esse método para obter o identificador de porta de conclusão de e/s usada para enfileirar itens de trabalho.

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>Valor de retorno

Retorna o identificador da fila ou nulo se o pool de threads não foi inicializado.

##  <a name="getsize"></a>  CThreadPool::GetSize

Chame esse método para obter o número de threads no pool.

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>Parâmetros

*pnNumThreads*<br/>
[out] Endereço da variável que, em caso de sucesso, recebe o número de threads no pool.

### <a name="return-value"></a>Valor de retorno

Retorna S_OK no êxito ou um erro HRESULT em caso de falha.

##  <a name="gettimeout"></a>  CThreadPool::GetTimeout

Chame esse método para obter o tempo máximo em milissegundos que o pool de threads irá esperar por um segmento para desligar.

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>Parâmetros

*pdwMaxWait*<br/>
[out] Endereço da variável que, em caso de sucesso, recebe o tempo máximo em milissegundos que o pool de threads irá esperar por um segmento para desligar.

### <a name="return-value"></a>Valor de retorno

Retorna S_OK no êxito ou um erro HRESULT em caso de falha.

### <a name="remarks"></a>Comentários

Esse valor de tempo limite é usado pelo [CThreadPool::Shutdown](#shutdown) se nenhum outro valor for fornecido para esse método.

##  <a name="initialize"></a>  CThreadPool::Initialize

Chame esse método para inicializar o pool de threads.

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>Parâmetros

*pvWorkerParam*<br/>
O parâmetro de trabalho a serem passados para o objeto de thread de trabalho `Initialize`, `Execute`, e `Terminate` métodos.

*nNumThreads*<br/>
O número solicitado de threads no pool.

Se *nNumThreads* é negativo, seu valor absoluto será multiplicado pelo número de processadores no computador para obter o número total de threads.

Se *nNumThreads* for zero, ATLS_DEFAULT_THREADSPERPROC será multiplicado pelo número de processadores no computador para obter o número total de threads.  O padrão é 2 threads por processador. Se necessário, você pode definir seu próprio valor de número inteiro positivo para esse símbolo antes de incluir atlutil.

*dwStackSize*<br/>
O tamanho da pilha para cada thread no pool.

*hCompletion*<br/>
O identificador de um objeto para associar a porta de conclusão.

### <a name="return-value"></a>Valor de retorno

Retorna S_OK no êxito ou um erro HRESULT em caso de falha.

##  <a name="queryinterface"></a>  CThreadPool::QueryInterface

Implementação de `IUnknown::QueryInterface`.

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>Comentários

Objetos dessa classe podem ser consultados com êxito para o `IUnknown` e [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md) interfaces.

##  <a name="queuerequest"></a>  CThreadPool::QueueRequest

Chame esse método para enfileirar um item de trabalho deve ser tratado por um thread no pool.

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>Parâmetros

*request*<br/>
A solicitação a ser enfileirado.

### <a name="return-value"></a>Valor de retorno

Retorna verdadeiro em caso de êxito, FALSE em caso de falha.

### <a name="remarks"></a>Comentários

Esse método adiciona um item de trabalho para a fila. Os threads no pool de escolher itens da fila na ordem em que elas são recebidas.

##  <a name="release"></a>  CThreadPool::Release

Implementação de `IUnknown::Release`.

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>Valor de retorno

Sempre retorna 1.

### <a name="remarks"></a>Comentários

Essa classe não implementa o controle de tempo de vida usando a contagem de referência.

##  <a name="setsize"></a>  CThreadPool::SetSize

Chame esse método para definir o número de threads no pool.

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>Parâmetros

*nNumThreads*<br/>
O número solicitado de threads no pool.

Se *nNumThreads* é negativo, seu valor absoluto será multiplicado pelo número de processadores no computador para obter o número total de threads.

Se *nNumThreads* for zero, ATLS_DEFAULT_THREADSPERPROC será multiplicado pelo número de processadores no computador para obter o número total de threads. O padrão é 2 threads por processador. Se necessário, você pode definir seu próprio valor de número inteiro positivo para esse símbolo antes de incluir atlutil.

### <a name="return-value"></a>Valor de retorno

Retorna S_OK no êxito ou um erro HRESULT em caso de falha.

### <a name="remarks"></a>Comentários

Se o número de threads especificado é menor que o número de threads atualmente no pool, o objeto coloca uma mensagem de desligamento na fila para ser selecionada por um thread em espera. Quando um thread em espera obtém a mensagem da fila, ele notifica o pool de threads e sai do procedimento de thread. Esse processo é repetido até que o número de threads no pool de atingir o número especificado ou até que nenhum thread foi encerrado dentro do período especificado por [GetTimeout](#gettimeout)/ [SetTimeout](#settimeout). Nessa situação, o método será retornado um HRESULT correspondente para WAIT_TIMEOUT, e a mensagem de desligamento pendente será cancelada.

##  <a name="settimeout"></a>  CThreadPool::SetTimeout

Chame esse método para definir o tempo máximo em milissegundos que o pool de threads irá esperar por um segmento para desligar.

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>Parâmetros

*dwMaxWait*<br/>
O tempo máximo solicitado em milissegundos que o pool de threads irá esperar por um segmento para desligar.

### <a name="return-value"></a>Valor de retorno

Retorna S_OK no êxito ou um erro HRESULT em caso de falha.

### <a name="remarks"></a>Comentários

O tempo limite é inicializado como ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT. O tempo padrão é de 36 segundos. Se necessário, você pode definir seu próprio valor de número inteiro positivo para esse símbolo antes de incluir atlutil.

Observe que *dwMaxWait* é a hora em que o pool aguardará para um único thread desligar. O tempo máximo que pode ser tomado para remover vários threads do pool pode ser um pouco menor que *dwMaxWait* multiplicado pelo número de threads.

##  <a name="shutdown"></a>  CThreadPool::Shutdown

Chame esse método para desligar o pool de threads.

```
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>Parâmetros

*dwMaxWait*<br/>
O tempo máximo solicitado em milissegundos que o pool de threads irá esperar por um segmento para desligar. Se 0 ou nenhum valor for fornecido, esse método usará o tempo limite definido [CThreadPool::SetTimeout](#settimeout).

### <a name="remarks"></a>Comentários

Esse método envia uma solicitação de desligamento para todos os threads no pool. Se o tempo limite expirar, esse método chamará [TerminateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-terminatethread) em qualquer thread que não foi encerrado. Esse método é chamado automaticamente do destruidor da classe.

## <a name="see-also"></a>Consulte também

[Interface IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[Classes](../../atl/reference/atl-classes.md)
