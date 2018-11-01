---
title: Estrutura SRWLockExclusiveTraits
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock method
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
ms.openlocfilehash: 4005f0dc1f75b79650963efc9a6f9f7522bc3395
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476460"
---
# <a name="srwlockexclusivetraits-structure"></a>Estrutura SRWLockExclusiveTraits

Descreve características comuns do `SRWLock` classe no modo de bloqueio exclusivo.

## <a name="syntax"></a>Sintaxe

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>Membros

### <a name="public-typedefs"></a>Typedefs públicos

Nome   | Descrição
------ | --------------------------------------------------------------------------
`Type` | Sinônimo de um ponteiro para o [SRWLOCK](../windows/srwlock-class.md) classe.

### <a name="public-methods"></a>Métodos públicos

Nome                                                        | Descrição
----------------------------------------------------------- | --------------------------------------------------------------------
[Srwlockexclusivetraits:: Getinvalidvalue](#getinvalidvalue) | Recupera um `SRWLockExclusiveTraits` objeto sempre é inválido.
[Srwlockexclusivetraits:: Unlock](#unlock)                   | Libera o controle exclusivo do especificado `SRWLock` objeto.

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`SRWLockExclusiveTraits`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** corewrappers. h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>Srwlockexclusivetraits:: Getinvalidvalue

Recupera um `SRWLockExclusiveTraits` objeto sempre é inválido.

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>Valor de retorno

Um objeto `SRWLockExclusiveTraits` vazio.

## <a name="unlock"></a>Srwlockexclusivetraits:: Unlock

Libera o controle exclusivo do especificado `SRWLock` objeto.

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>Parâmetros

*SRWLOCK*<br/>
Identificador para um `SRWLock` objeto.
