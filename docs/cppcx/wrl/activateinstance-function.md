---
title: Função ActivateInstance
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Windows::Foundation::ActivateInstance
- client/ABI::Windows::Foundation::ActivateInstance
helpviewer_keywords:
- ActivateInstance function
ms.assetid: 8cfd1dd9-5fda-4cc2-acf8-d40e783b3875
ms.openlocfilehash: 43aa34153f0e71dd665090243ff2288bff704404
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303963"
---
# <a name="activateinstance-function"></a>Função ActivateInstance

Registra e recupera uma instância de um tipo especificado definido em uma ID de classe especificado.

## <a name="syntax"></a>Sintaxe

```cpp
template<typename T>
inline HRESULT ActivateInstance(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> instance
);
```

### <a name="parameters"></a>Parâmetros

*T*<br/>
Um tipo para ativar.

*activatableClassId*<br/>
A ID da classe que define o parâmetro *T*.

*instance*<br/>
Quando essa operação for concluída, uma referência a uma instância do *T*.

## <a name="return-value"></a>Valor de retorno

S_OK se bem-sucedido; Caso contrário, um erro HRESULT que indica a causa do erro.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** client.h

**Namespace:** Windows::Foundation

## <a name="see-also"></a>Consulte também

[Namespace Windows::Foundation](windows-foundation-namespace.md)