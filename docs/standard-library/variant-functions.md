---
title: '&lt;variante&gt; funções'
ms.date: 04/04/2019
f1_keywords:
- variant/std::get
- variant/std::get_if
- variant/std::holds_alternative
- variant/std::visit
ms.openlocfilehash: d558eb086e076ba22722080b0c19f3d5733136d2
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268378"
---
# <a name="ltvariantgt-functions"></a>&lt;variante&gt; funções

## <a name="get"></a> Obter

Obtém a variante de um objeto.

```cpp
template <size_t I, class... Types>
    constexpr variant_alternative_t<I, variant<Types...>>& get(variant<Types...>&);
template <size_t I, class... Types>
    constexpr variant_alternative_t<I, variant<Types...>>&& get(variant<Types...>&&);
template <size_t I, class... Types>
    constexpr const variant_alternative_t<I, variant<Types...>>& get(const variant<Types...>&);
template <size_t I, class... Types>
    constexpr const variant_alternative_t<I, variant<Types...>>&& get(const variant<Types...>&&);
template <class T, class... Types>
    constexpr T& get(variant<Types...>&);
template <class T, class... Types>
    constexpr T&& get(variant<Types...>&&);
template <class T, class... Types>
    constexpr const T& get(const variant<Types...>&);
template <class T, class... Types>
    constexpr const T&& get(const variant<Types...>&&);
```

## <a name="get_if"></a> get_if

Obtém a variante de um objeto se ele existir.

```cpp
template <size_t I, class... Types>
    constexpr add_pointer_t<variant_alternative_t<I, variant<Types...>>> get_if(variant<Types...>*) noexcept;
template <size_t I, class... Types>
    constexpr add_pointer_t<const variant_alternative_t<I, variant<Types...>>> get_if(const variant<Types...>*) noexcept;
template <class T, class... Types>
    constexpr add_pointer_t<T> get_if(variant<Types...>*) noexcept;
template <class T, class... Types>
    constexpr add_pointer_t<const T> get_if(const variant<Types...>*) noexcept;
```

## <a name="holds_alternative"></a> holds_alternative

Retornar **verdadeira** se existir uma variante.

```cpp
template <class T, class... Types>
    constexpr bool holds_alternative(const variant<Types...>&) noexcept;
```

## <a name="swap"></a> troca

```cpp
template <class... Types>
    void swap(variant<Types...>&, variant<Types...>&) noexcept(see below);
```

## <a name="variant_npos"></a> variant_npos

```cpp
namespace std {
    inline constexpr size_t variant_npos = -1;
}
```

## <a name="visit"></a> Visite o

Move para a próxima **variante**.

```cpp
template <class Visitor, class... Variants>
    constexpr see below
        visit(Visitor&&, Variants&&...);
```
