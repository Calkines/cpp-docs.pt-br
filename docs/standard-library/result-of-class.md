---
title: Classe result_of
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::result_of
- type_traits/std::result_of_t
- type_traits/std::result_of::type
helpviewer_keywords:
- std::result_of
- std::result_of_t
- std::result_of::type
ms.assetid: 5374a096-4b4a-4712-aa97-6852c5cdd6be
ms.openlocfilehash: 84a0fbc9ecfb1a6ba18a10aafce8cd8e50cd5ec6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563810"
---
# <a name="resultof-class"></a>Classe result_of

Determina o tipo de retorno do tipo callable que usa os tipos de argumento especificados.

## <a name="syntax"></a>Sintaxe

```cpp
template<class>
struct result_of; // Causes a static assert

template <class Fn, class... ArgTypes>
struct result_of<Fn(ArgTypes...)>;

// Helper type
template<class T>
   using result_of_t = typename result_of<T>::type;
```

### <a name="parameters"></a>Parâmetros

*Fn*<br/>
O tipo callable para consulta.

*ArgTypes*<br/>
Os tipos de lista de argumentos para o tipo callable para consulta.

## <a name="remarks"></a>Comentários

Use este modelo para determinar no tempo de compilação o tipo de resultado `Fn`(`ArgTypes`), onde *Fn* é um tipo callable, referência à função ou referência ao tipo callable, invocada usando uma lista dos tipos de argumentos na  *ArgTypes*. O membro `type` da classe de modelo nomeia o tipo de resultado de `decltype(std::invoke(declval<Fn>(), declval<ArgTypes>()...))` se a expressão não avaliada `std::invoke(declval<Fn>(), declval<ArgTypes>()...)` está bem formada. Caso contrário, a classe de modelo não terá nenhum membro `type`. O tipo *Fn* e todos os tipos de pacote de parâmetros *ArgTypes* devem ser tipos completos, **void**, ou matrizes de limite desconhecido.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<type_traits>

**Namespace:** std

## <a name="see-also"></a>Consulte também

[<type_traits>](../standard-library/type-traits.md)<br/>
