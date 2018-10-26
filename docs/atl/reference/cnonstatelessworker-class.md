---
title: Classe CNonStatelessWorker | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker
- ATLUTIL/ATL::CNonStatelessWorker::RequestType
- ATLUTIL/ATL::CNonStatelessWorker::Execute
- ATLUTIL/ATL::CNonStatelessWorker::Initialize
- ATLUTIL/ATL::CNonStatelessWorker::Terminate
dev_langs:
- C++
helpviewer_keywords:
- CNonStatelessWorker class
ms.assetid: d00936c6-9e7d-49fb-b87d-417b963367d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90c50d3a918f452372aacae5beb36f5425d6a77a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053611"
---
# <a name="cnonstatelessworker-class"></a>Classe CNonStatelessWorker

Recebe solicitações de um pool de threads e as transmite para um objeto de trabalho que é criado e destruído em cada solicitação.

> [!IMPORTANT]
>  Essa classe e seus membros não podem ser usados em aplicativos executados no tempo de execução do Windows.

## <a name="syntax"></a>Sintaxe

```
template <class Worker>
class CNonStatelessWorker
```

#### <a name="parameters"></a>Parâmetros

*Trabalhador*<br/>
Uma classe de thread de trabalho em conformidade com o [arquétipo de trabalhador](../../atl/reference/worker-archetype.md) adequado para tratar as solicitações em fila no [CThreadPool](../../atl/reference/cthreadpool-class.md).

## <a name="members"></a>Membros

### <a name="public-typedefs"></a>Typedefs públicos

|Nome|Descrição|
|----------|-----------------|
|[CNonStatelessWorker::RequestType](#requesttype)|Implementação de [WorkerArchetype::RequestType](worker-archetype.md#requesttype).|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CNonStatelessWorker::Execute](#execute)|Implementação de [WorkerArchetype::Execute](worker-archetype.md#execute).|
|[CNonStatelessWorker::Initialize](#initialize)|Implementação de [WorkerArchetype::Initialize](worker-archetype.md#initialize).|
|[CNonStatelessWorker::Terminate](#terminate)|Implementação de [WorkerArchetype::Terminate](worker-archetype.md#terminate).|

## <a name="remarks"></a>Comentários

Essa classe é um thread de trabalho simples para uso com [CThreadPool](../../atl/reference/cthreadpool-class.md). Essa classe não fornece quaisquer recursos de tratamento de solicitação do seu próprio. Em vez disso, ele cria uma instância de uma instância do *trabalhador* por solicitação e delega a implementação de seus métodos a essa instância.

O benefício dessa classe é que ele fornece uma maneira conveniente de alterar o modelo de estado para as classes de thread de trabalho existentes. `CThreadPool` criará um único trabalho para o tempo de vida do thread, portanto, se a classe de trabalho mantém o estado, ele irá mantê-los em várias solicitações. Simplesmente encapsulando dessa classe na `CNonStatelessWorker` modelo antes de usá-lo com `CThreadPool`, o tempo de vida do trabalho e o estado em que ele contém é limitado a uma única solicitação.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atlutil

##  <a name="execute"></a>  CNonStatelessWorker::Execute

Implementação de [WorkerArchetype::Execute](worker-archetype.md#execute).

```
void Execute(
    Worker::RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

### <a name="remarks"></a>Comentários

Esse método cria uma instância das *trabalhador* classe na pilha e chamadas [inicializar](worker-archetype.md#initialize) naquele objeto. Se a inicialização for bem-sucedida, este método também chama [Execute](worker-archetype.md#execute) e [Terminate](worker-archetype.md#terminate) no mesmo objeto.

##  <a name="initialize"></a>  CNonStatelessWorker::Initialize

Implementação de [WorkerArchetype::Initialize](worker-archetype.md#initialize).

```
BOOL Initialize(void* /* pvParam */) throw();
```

### <a name="return-value"></a>Valor de retorno

Sempre retorna TRUE.

### <a name="remarks"></a>Comentários

Essa classe não faz qualquer inicialização `Initialize`.

##  <a name="requesttype"></a>  CNonStatelessWorker::RequestType

Implementação de [WorkerArchetype::RequestType](worker-archetype.md#requesttype).

```
typedef Worker::RequestType RequestType;
```

### <a name="remarks"></a>Comentários

Essa classe manipula o mesmo tipo de item de trabalho que a classe usada para o *trabalhador* parâmetro de modelo. Ver [visão geral de CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md) para obter detalhes.

##  <a name="terminate"></a>  CNonStatelessWorker::Terminate

Implementação de [WorkerArchetype::Terminate](worker-archetype.md#terminate).

```
void Terminate(void* /* pvParam */) throw();
```

### <a name="remarks"></a>Comentários

Essa classe não faz qualquer limpeza `Terminate`.

## <a name="see-also"></a>Consulte também

[Classe CThreadPool](../../atl/reference/cthreadpool-class.md)<br/>
[Arquétipo de trabalhador](../../atl/reference/worker-archetype.md)<br/>
[Classes](../../atl/reference/atl-classes.md)
