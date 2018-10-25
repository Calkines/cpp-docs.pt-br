---
title: Função MakeAndInitialize | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
dev_langs:
- C++
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 54cb237a4dac09b26018cef92b4c5980c3de5061
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50061673"
---
# <a name="makeandinitialize-function"></a>Função MakeAndInitialize

Inicializa a classe de tempo de execução do Windows especificada. Use esta função para criar uma instância de um componente que é definido no mesmo módulo.

## <a name="syntax"></a>Sintaxe

```cpp
template <typename T, typename I,
typename TArg1,
typename TArg2,
typename TArg3,
typename TArg4,
typename TArg5,
typename TArg6,
typename TArg7,
typename TArg8,
typename TArg9> HRESULT MakeAndInitialize(_Outptr_result_nullonfailure_ I** ppvObject, TArg1 &&arg1, TArg2 &&arg2, TArg3 &&arg3, TArg4 &&arg4, TArg5 &&arg5, TArg6 &&arg6, TArg7 &&arg7, TArg8 &&arg8, TArg9 &&arg9) throw()
```

### <a name="parameters"></a>Parâmetros

*T*<br/>
Uma classe especificada pelo usuário que herda de `WRL::RuntimeClass`.

*DynamicSite<Targ1*<br/>
Tipo de argumento 1, o que é passado para a classe de tempo de execução especificado.

*TArg2*<br/>
Tipo de argumento 2 que é passado para a classe de tempo de execução especificado.

*TArg3*<br/>
Tipo de argumento 3 que é passado para a classe de tempo de execução especificado.

*TArg4*<br/>
Tipo de argumento 4 que é passado para a classe de tempo de execução especificado.

*TArg5*<br/>
Tipo de argumento 5, o que é passado para a classe de tempo de execução especificado.

*TArg6*<br/>
Tipo de argumento 6, o que é passado para a classe de tempo de execução especificado.

*TArg7*<br/>
Tipo de argumento 7, o que é passado para a classe de tempo de execução especificado.

*TArg8*<br/>
Tipo de argumento 8, o que é passado para a classe de tempo de execução especificado.

*TArg9*<br/>
Tipo de argumento 9 que é passado para a classe de tempo de execução especificado.

*arg1*<br/>
Argumento 1 que é passado para a classe de tempo de execução especificado.

*Arg2*<br/>
Argumento 2 que é passado para a classe de tempo de execução especificado.

*arg3*<br/>
Argumento 3 que é passado para a classe de tempo de execução especificado.

*Arg4*<br/>
Argumento de 4 que é passado para a classe de tempo de execução especificado.

*arg5*<br/>
Argumento 5 que é passado para a classe de tempo de execução especificado.

*arg6*<br/>
Argumento 6 que é passado para a classe de tempo de execução especificado.

*arg7*<br/>
Argumento 7 que é passado para a classe de tempo de execução especificado.

*arg8*<br/>
Argumento 8 que é passado para a classe de tempo de execução especificado.

*arg9*<br/>
Argumento 9 que é passado para a classe de tempo de execução especificado.

## <a name="return-value"></a>Valor de retorno

Um valor HRESULT.

## <a name="remarks"></a>Comentários

Ver [como: instanciar componentes WRL diretamente](../windows/how-to-instantiate-wrl-components-directly.md) para saber as diferenças entre essa função e [Microsoft::WRL::Make](../windows/make-function.md)e para obter um exemplo.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** Implements. h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Consulte também

[Namespace Microsoft::WRL::Details](../windows/microsoft-wrl-details-namespace.md)