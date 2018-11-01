---
title: Namespace Microsoft::WRL::Wrappers::HandleTraits
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits
helpviewer_keywords:
- HandleTraits namespace
ms.assetid: 2fb5c6d1-bfc2-4e09-91eb-31705064ffb3
ms.openlocfilehash: e558838ca9cd06fb5529f689d45a920db151d272
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643242"
---
# <a name="microsoftwrlwrappershandletraits-namespace"></a>Namespace Microsoft::WRL::Wrappers::HandleTraits

Descreve as características dos tipos comuns de recursos com base no identificador.

## <a name="syntax"></a>Sintaxe

```cpp
namespace Microsoft::WRL::Wrappers::HandleTraits;
```

## <a name="members"></a>Membros

### <a name="structures"></a>Estruturas

|Nome|Descrição|
|----------|-----------------|
|[Estrutura CriticalSectionTraits](../windows/criticalsectiontraits-structure.md)|É especialista um `CriticalSection` objeto para dar suporte a uma seção crítica inválida ou uma função para liberar uma seção crítica.|
|[Estrutura EventTraits](../windows/eventtraits-structure.md)|Define as características de um `Event` identificador de classe.|
|[Estrutura FileHandleTraits](../windows/filehandletraits-structure.md)|Define as características de um identificador de arquivo.|
|[Estrutura HANDLENullTraits](../windows/handlenulltraits-structure.md)|Define as características comuns de um identificador não inicializado.|
|[Estrutura HANDLETraits](../windows/handletraits-structure.md)|Define as características comuns de um identificador.|
|[Estrutura MutexTraits](../windows/mutextraits-structure.md)|Define as características comuns do [Mutex](../windows/mutex-class1.md) classe.|
|[Estrutura SemaphoreTraits](../windows/semaphoretraits-structure.md)|Define as características comuns de um objeto de sinal.|
|[Estrutura SRWLockExclusiveTraits](../windows/srwlockexclusivetraits-structure.md)|Descreve características comuns do `SRWLock` classe no modo de bloqueio exclusivo.|
|[Estrutura SRWLockSharedTraits](../windows/srwlocksharedtraits-structure.md)|Descreve características comuns do `SRWLock` classe no modo de bloqueio compartilhado.|

## <a name="requirements"></a>Requisitos

**Cabeçalho:** corewrappers. h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="see-also"></a>Consulte também

[Namespace Microsoft::WRL::Wrappers](../windows/microsoft-wrl-wrappers-namespace.md)