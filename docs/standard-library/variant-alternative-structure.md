---
title: variant_alternative Struct
ms.date: 04/04/2019
f1_keywords:
- variant/std::variant_alternative
helpviewer_keywords:
- variant_alternative struct
ms.openlocfilehash: f637a2e588297cb44b582a9c5fa108034d99d8f3
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268388"
---
# <a name="variantalternative-struct"></a>variant_alternative Struct

Auxilia os objetos variantes.

## <a name="syntax"></a>Sintaxe

```cpp
template <size_t I, class T>
    struct variant_alternative; // not defined
template <size_t I, class T>
    struct variant_alternative<I, const T>;
template <size_t I, class T>
    struct variant_alternative<I, volatile T>;
template <size_t I, class T>
    struct variant_alternative<I, const volatile T>;
template <size_t I, class T>
    using variant_alternative_t = typename variant_alternative<I, T>::type;
template <size_t I, class... Types>
    struct variant_alternative<I, variant<Types...>>;
```