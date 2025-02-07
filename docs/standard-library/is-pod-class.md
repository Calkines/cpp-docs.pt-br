---
title: Classe is_pod
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_pod
helpviewer_keywords:
- is_pod class
- is_pod
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
ms.openlocfilehash: 1249e9a3689d4b91334e545ba294c28984898035
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455757"
---
# <a name="ispod-class"></a>Classe is_pod

Testa se o tipo é um POD.

## <a name="syntax"></a>Sintaxe

```cpp
template <class T>
struct is_pod;
```

### <a name="parameters"></a>Parâmetros

*T*\
O tipo a ser consultado.

## <a name="remarks"></a>Comentários

`is_pod<T>::value`será **true** se o tipo *T* for um pod (dados antigos simples). Caso contrário, será **false**.

Tipos aritméticos, tipos de enumeração, tipos de ponteiro e tipos de ponteiro para membro são POD.

Uma versão qualificada para CV de um tipo POD também é um tipo POD.

Uma matriz de POD também é POD.

Um struct ou união, de que todos os membros de dados não estáticos forem POD, também será POD se não tiver:

- nenhum construtor declarado pelo usuário.

- nenhum membro de dados não estáticos particular ou protegido.

- Nenhuma classe base.

- nenhuma função virtual.

- nenhum membro de dados não estáticos do tipo de referência.

- nenhum operador de atribuição de cópia definido pelo usuário.

- nenhum destruidor definido pelo usuário.

Portanto, é possível compilar recursivamente structs e matrizes POD que contêm structs e matrizes POD.

## <a name="example"></a>Exemplo

```cpp
// std__type_traits__is_pod.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial {
    int val;
};

struct throws {
    throws() {}  // User-declared ctor, so not POD

    int val;
};

int main() {
    std::cout << "is_pod<trivial> == " << std::boolalpha
        << std::is_pod<trivial>::value << std::endl;
    std::cout << "is_pod<int> == " << std::boolalpha
        << std::is_pod<int>::value << std::endl;
    std::cout << "is_pod<throws> == " << std::boolalpha
        << std::is_pod<throws>::value << std::endl;

    return (0);
}
```

```Output
is_pod<trivial> == true
is_pod<int> == true
is_pod<throws> == false
```

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<type_traits>

**Namespace:** std

## <a name="see-also"></a>Consulte também

[<type_traits>](../standard-library/type-traits.md)
