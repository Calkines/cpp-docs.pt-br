---
title: Classe CNoWorkerThread
ms.date: 11/04/2016
f1_keywords:
- CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread::AddHandle
- ATLUTIL/ATL::CNoWorkerThread::AddTimer
- ATLUTIL/ATL::CNoWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CNoWorkerThread::GetThreadId
- ATLUTIL/ATL::CNoWorkerThread::Initialize
- ATLUTIL/ATL::CNoWorkerThread::RemoveHandle
- ATLUTIL/ATL::CNoWorkerThread::Shutdown
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
ms.openlocfilehash: fcd103283738ce7d573faa2fb1025ee2af642021
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520205"
---
# <a name="cnoworkerthread-class"></a>Classe CNoWorkerThread

Use essa classe como o argumento para o `MonitorClass` parâmetro de modelo para classes de cache se você quiser desabilitar a manutenção de cache dinâmico.

> [!IMPORTANT]
>  Essa classe e seus membros não podem ser usados em aplicativos executados no tempo de execução do Windows.

## <a name="syntax"></a>Sintaxe

```
class CNoWorkerThread
```

## <a name="members"></a>Membros

### <a name="public-methods"></a>Métodos Públicos

|Nome|Descrição|
|----------|-----------------|
|[CNoWorkerThread::AddHandle](#addhandle)|Equivalente a não funcionais [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).|
|[CNoWorkerThread::AddTimer](#addtimer)|Equivalente a não funcionais [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).|
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|Equivalente a não funcionais [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).|
|[CNoWorkerThread::GetThreadId](#getthreadid)|Equivalente a não funcionais [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).|
|[CNoWorkerThread::Initialize](#initialize)|Equivalente a não funcionais [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).|
|[CNoWorkerThread::RemoveHandle](#removehandle)|Equivalente a não funcionais [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).|
|[CNoWorkerThread::Shutdown](#shutdown)|Equivalente a não funcionais [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).|

## <a name="remarks"></a>Comentários

Essa classe fornece a mesma interface pública que [CWorkerThread](../../atl/reference/cworkerthread-class.md). Essa interface deve ser fornecido pelo `MonitorClass` parâmetro de modelo para classes de cache.

Os métodos nessa classe são implementados para não fazer nada. Os métodos que retornam um HRESULT sempre retornam S_OK e os métodos que retornam uma ID de thread ou identificador sempre retornam 0.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atlutil

##  <a name="addhandle"></a>  CNoWorkerThread::AddHandle

Equivalente a não funcionais [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

```
HRESULT AddHandle(HANDLE /* hObject */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */) throw();
```

### <a name="return-value"></a>Valor de retorno

Sempre retorna S_OK.

### <a name="remarks"></a>Comentários

A implementação fornecida por esta classe não fará nada.

##  <a name="addtimer"></a>  CNoWorkerThread::AddTimer

Equivalente a não funcionais [CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer).

```
HRESULT AddTimer(DWORD /* dwInterval */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */,
    HANDLE* /* phTimer */) throw();
```

### <a name="return-value"></a>Valor de retorno

Sempre retorna S_OK.

### <a name="remarks"></a>Comentários

A implementação fornecida por esta classe não fará nada.

##  <a name="getthreadhandle"></a>  CNoWorkerThread::GetThreadHandle

Equivalente a não funcionais [CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle).

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>Valor de retorno

Sempre retorna NULL.

### <a name="remarks"></a>Comentários

A implementação fornecida por esta classe não fará nada.

##  <a name="getthreadid"></a>  CNoWorkerThread::GetThreadId

Equivalente a não funcionais [CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid).

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>Valor de retorno

Sempre retorna 0.

### <a name="remarks"></a>Comentários

A implementação fornecida por esta classe não fará nada.

##  <a name="initialize"></a>  CNoWorkerThread::Initialize

Equivalente a não funcionais [CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize).

```
HRESULT Initialize() throw();
```

### <a name="return-value"></a>Valor de retorno

Sempre retorna S_OK.

### <a name="remarks"></a>Comentários

A implementação fornecida por esta classe não fará nada.

##  <a name="removehandle"></a>  CNoWorkerThread::RemoveHandle

Equivalente a não funcionais [CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle).

```
HRESULT RemoveHandle(HANDLE /* hObject */) throw();
```

### <a name="return-value"></a>Valor de retorno

Sempre retorna S_OK.

### <a name="remarks"></a>Comentários

A implementação fornecida por esta classe não fará nada.

##  <a name="shutdown"></a>  CNoWorkerThread::Shutdown

Equivalente a não funcionais [CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown).

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="return-value"></a>Valor de retorno

Sempre retorna S_OK.

### <a name="remarks"></a>Comentários

A implementação fornecida por esta classe não fará nada.
