---
title: Estrutura DispatchState
ms.date: 11/04/2016
f1_keywords:
- DispatchState
- CONCRTRM/concurrency::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::DispatchState
- CONCRTRM/concurrency::DispatchState::DispatchState::m_dispatchStateSize
- CONCRTRM/concurrency::DispatchState::DispatchState::m_fIsPreviousContextAsynchronouslyBlocked
- CONCRTRM/concurrency::DispatchState::DispatchState::m_reserved
helpviewer_keywords:
- DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
ms.openlocfilehash: 4c15fc0ba9c78d8b6416cd88480c8ada6e3febf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603551"
---
# <a name="dispatchstate-structure"></a>Estrutura DispatchState

O `DispatchState` estrutura é usada para transferir o estado para o `IExecutionContext::Dispatch` método. Ele descreve as circunstâncias em que o `Dispatch` método é invocado em um `IExecutionContext` interface.

## <a name="syntax"></a>Sintaxe

```
struct DispatchState;
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|[DispatchState::DispatchState](#ctor)|Constrói um novo objeto `DispatchState`.|

### <a name="public-data-members"></a>Membros de Dados Públicos

|Nome|Descrição|
|----------|-----------------|
|[DispatchState::m_dispatchStateSize](#m_dispatchstatesize)|Tamanho dessa estrutura, que é usado para controle de versão.|
|[DispatchState::m_fIsPreviousContextAsynchronouslyBlocked](#m_fispreviouscontextasynchronouslyblocked)|Informa se entrou nesse contexto o `Dispatch` método porque o contexto anterior assincronamente bloqueado. Isso é usado apenas no contexto de programação UMS e é definido como o valor `0` para todos os outros contextos de execução.|
|[DispatchState::m_reserved](#m_reserved)|Bits reservados para informações futuras passando.|

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`DispatchState`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** concrtrm. h

**Namespace:** simultaneidade

##  <a name="ctor"></a>  Construtor dispatchstate:: Dispatchstate

Constrói um novo objeto `DispatchState`.

```
DispatchState();
```

##  <a name="m_dispatchstatesize"></a>  Membro de dados dispatchstate:: M_dispatchstatesize

Tamanho dessa estrutura, que é usado para controle de versão.

```
unsigned long m_dispatchStateSize;
```

##  <a name="m_fispreviouscontextasynchronouslyblocked"></a>  Membro de dados dispatchstate:: M_fispreviouscontextasynchronouslyblocked

Informa se entrou nesse contexto o `Dispatch` método porque o contexto anterior assincronamente bloqueado. Isso é usado apenas no contexto de programação UMS e é definido como o valor `0` para todos os outros contextos de execução.

```
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```

##  <a name="m_reserved"></a>  Membro de dados dispatchstate:: M_reserved

Bits reservados para informações futuras passando.

```
unsigned int m_reserved : 31;
```

## <a name="see-also"></a>Consulte também

[Namespace de simultaneidade](concurrency-namespace.md)
