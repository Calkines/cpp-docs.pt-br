---
title: Classe remove_reference
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_reference
helpviewer_keywords:
- remove_reference class
- remove_reference
ms.assetid: 294e1965-3ae3-46ee-bc42-4fdf60c24717
ms.openlocfilehash: 76f700b488d78af77e39ec91c7328604d18931fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473548"
---
# <a name="removereference-class"></a>Classe remove_reference

Cria tipo de não referência do tipo.

## <a name="syntax"></a>Sintaxe

```cpp
template <class T>
struct remove_reference;

template <class T>
using remove_reference_t = typename remove_reference<T>::type;
```

### <a name="parameters"></a>Parâmetros

*T*<br/>
O tipo a ser modificado.

## <a name="remarks"></a>Comentários

Uma instância do `remove_reference<T>` mantém um tipo modificado que é `T1` quando *T* está no formato `T1&`; caso contrário, *T*.

## <a name="example"></a>Exemplo

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    int *p = (std::remove_reference_t<int&> *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "remove_reference_t<int&> == "
        << typeid(*p).name() << std::endl;

    return (0);
    }
```

```Output
remove_reference_t<int&> == int
```

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<type_traits>

**Namespace:** std

## <a name="see-also"></a>Consulte também

[<type_traits>](../standard-library/type-traits.md)<br/>
[Classe add_lvalue_reference](../standard-library/add-lvalue-reference-class.md)<br/>
