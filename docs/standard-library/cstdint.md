---
title: '&lt;cstdint&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdint>
ms.assetid: 87afafb2-c630-4383-a2fc-a6b47c639e21
ms.openlocfilehash: 9f4839ed6166e328feac4ae89fcce0637abce993
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447475"
---
# <a name="ltcstdintgt"></a>&lt;cstdint&gt;

Inclui o cabeçalho \<stdint.h> da biblioteca C Padrão e adiciona os nomes associados ao namespace `std`. A inclusão desse cabeçalho garante que os nomes declarados usando vinculação externa no cabeçalho da biblioteca C Padrão sejam declarados no namespace `std`.

## <a name="syntax"></a>Sintaxe

```cpp
#include <cstdint>
```

## <a name="types"></a>Tipos

```cpp
namespace std { 
    using int8_t = signed integer type; // optional
    using int16_t = signed integer type; // optional
    using int32_t = signed integer type; // optional
    using int64_t = signed integer type; // optional
    using int_fast8_t = signed integer type;
    using int_fast16_t = signed integer type;
    using int_fast32_t = signed integer type;
    using int_fast64_t = signed integer type;
    using int_least8_t = signed integer type;
    using int_least16_t = signed integer type;
    using int_least32_t = signed integer type;
    using int_least64_t = signed integer type;
    using intmax_t = signed integer type;
    using intptr_t = signed integer type; // optional
    using uint8_t = unsigned integer type; // optional
    using uint16_t = unsigned integer type; // optional
    using uint32_t = unsigned integer type; // optional
    using uint64_t = unsigned integer type; // optional
    using uint_fast8_t = unsigned integer type;
    using uint_fast16_t = unsigned integer type;
    using uint_fast32_t = unsigned integer type;
    using uint_fast64_t = unsigned integer type;
    using uint_least8_t = unsigned integer type;
    using uint_least16_t = unsigned integer type;
    using uint_least32_t = unsigned integer type;
    using uint_least64_t = unsigned integer type;
    using uintmax_t = unsigned integer type;
    using uintptr_t = unsigned integer type; // optional
}
```

## <a name="macros"></a>Macros

```cpp
INT_[FAST LEAST]{8 16 32 64}_MIN
[U]INT_[FAST LEAST]{8 16 32 64}_MAX
INT{MAX PTR}_MIN
[U]INT{MAX PTR}_MAX
{PTRDIFF SIG_ATOMIC WCHAR WINT}{_MAX _MIN}
SIZE_MAX

[U]INT{8 16 32 64 MAX}_C
```

## <a name="see-also"></a>Consulte também

[Referência de Arquivos de Cabeçalho](../standard-library/cpp-standard-library-header-files.md)\
[Visão geral da biblioteca padrão C++](../standard-library/cpp-standard-library-overview.md)
