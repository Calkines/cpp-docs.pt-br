---
title: Função Make
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Make
helpviewer_keywords:
- Make function
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
ms.openlocfilehash: b45337ef773f93968570f62ab73c02d11fae88ff
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028241"
---
# <a name="make-function"></a>Função Make

Inicializa a classe de tempo de execução do Windows especificada. Use esta função para criar uma instância de um componente que é definido no mesmo módulo.

## <a name="syntax"></a>Sintaxe

```cpp
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8,
   typename TArg9
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8,
   TArg9 &&arg9
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3
);
template <
   typename T,
   typename TArg1,
   typename TArg2
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2
);
template <
   typename T,
   typename TArg1
>
ComPtr<T> Make(
   TArg1 &&arg1
);
template <
   typename T
>
ComPtr<T> Make();
```

### <a name="parameters"></a>Parâmetros

*T*<br/>
Uma classe especificada pelo usuário que herda de `WRL::RuntimeClass`.

*TArg1*<br/>
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

*arg2*<br/>
Argumento 2 que é passado para a classe de tempo de execução especificado.

*arg3*<br/>
Argumento 3 que é passado para a classe de tempo de execução especificado.

*arg4*<br/>
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

Um `ComPtr<T>` objeto se for bem-sucedido; caso contrário, `nullptr`.

## <a name="remarks"></a>Comentários

Confira [Como Instanciar componentes WRL-diretamente](how-to-instantiate-wrl-components-directly.md) para saber as diferenças entre essa função e [Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md)e para obter um exemplo.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** Implements. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Consulte também

[Namespace Microsoft::WRL](microsoft-wrl-namespace.md)