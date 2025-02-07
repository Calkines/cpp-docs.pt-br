---
title: '&lt;TYPEDEFs string_view&gt;'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: c3367afe1353ac70abb74a59658a255614ac8470
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459179"
---
# <a name="ltstringviewgt-typedefs"></a>&lt;TYPEDEFs string_view&gt;

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a>string_view

Um tipo que descreve uma especialização do modelo de classe [basic_string_view](../standard-library/basic-string-view-class.md) com elementos do tipo **Char**.

```cpp
typedef basic_string_view<char, char_traits<char>> string_view;
```

### <a name="remarks"></a>Comentários

As declarações a seguir são equivalentes:

```cpp
string_view str("Hello");

basic_string_view<char> str("Hello");
```

Para obter uma lista de construtores de cadeia de caracteres, consulte [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string_view"></a> u16string_view

Um tipo que descreve uma especialização do modelo de classe [basic_string_view](../standard-library/basic-string-view-class.md) com elementos do `char16_t`tipo.

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>Comentários

Para obter uma lista de construtores de cadeia de caracteres, consulte [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string_view"></a> u32string_view

Um tipo que descreve uma especialização do modelo de classe [basic_string_view](../standard-library/basic-string-view-class.md) com elementos do `char32_t`tipo.

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>Comentários

Para obter uma lista de construtores de cadeia de caracteres, consulte [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring_view"></a>wstring_view

Um tipo que descreve uma especialização do modelo de classe [basic_string_view](../standard-library/basic-string-view-class.md) com elementos do tipo **wchar_t**.

```cpp
typedef basic_string_view<wchar_t, char_traits<wchar_t>> wstring_view;
```

### <a name="remarks"></a>Comentários

As declarações a seguir são equivalentes:

```cpp
wstring_view wstr(L"Hello");

basic_string_view<wchar_t> wstr(L"Hello");
```

Para obter uma lista de construtores de cadeia de caracteres, consulte [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> O tamanho de **wchar_t** é de dois bytes no Windows, mas esse não é necessariamente o caso para todas as plataformas. Se você precisar de um tipo de caractere string_view largo com uma largura garantida para permanecer o mesmo em todas as plataformas, use [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) ou [u32string_view](../standard-library/string-view-typedefs.md#u32string_view).

## <a name="see-also"></a>Consulte também

[\<string_view>](../standard-library/string-view.md)
