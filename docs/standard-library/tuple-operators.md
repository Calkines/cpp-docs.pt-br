---
title: Operadores &lt;tuple&gt;
ms.date: 11/04/2016
f1_keywords:
- tuple/std::operator!=
- tuple/std::operator>
- tuple/std::operator>=
- tuple/std::operator<
- tuple/std::operator<=
- tuple/std::operator==
ms.assetid: f25752dc-d3e2-4e12-b5ac-9a8682ca60ed
ms.openlocfilehash: 5554f08f32048bafde5bdb2c316e12e1e01c6ffb
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68241658"
---
# <a name="lttuplegt-operators"></a>Operadores &lt;tuple&gt;

## <a name="op_neq"></a> operador! =

Compare objetos `tuple` quanto a desigualdade.

```cpp
template <class T1, class T2, ..., class TN,
    class U1, class U2, ..., class UN>
bool operator!=(const tuple<T1, T2, ..., TN>& tpl1,
    const tuple<U1, U2, ..., UN>& tpl2);
```

### <a name="parameters"></a>Parâmetros

*TN*\
O tipo do enésimo elemento de tupla.

### <a name="remarks"></a>Comentários

A função retorna falso quando `N` é 0, caso contrário `get<0>(tpl1) != get<0>(tpl2) || get<1>(tpl1) != get<1>(tpl2) || ... || get<N - 1>(tpl1) == get<N - 1>(tpl2)`.

### <a name="example"></a>Exemplo

```cpp
// std__tuple__operator_ne.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 != c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c0 != c1);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
false
true
```

## <a name="op_lt"></a> Operador&lt;

Compare objetos `tuple` quanto a menor que.

```cpp
template <class T1, class T2, ..., class TN,
    class U1, class U2, ..., class UN>
bool operator<(const tuple<T1, T2, ..., TN>& tpl1,
    const tuple<U1, U2, ..., UN>& tpl2);
```

### <a name="parameters"></a>Parâmetros

*TN*\
O tipo do enésimo elemento de tupla.

### <a name="remarks"></a>Comentários

A função retorna verdadeiro quando `N` é maior que 0 e o primeiro valor divergente em `tpl1` é comparado como menor que o valor correspondente em `tpl2`, caso contrário, retorna falso.

### <a name="example"></a>Exemplo

```cpp
// std__tuple__operator_lt.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 < c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c0 < c1);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
false
true
```

## <a name="op_lt_eq"></a> operador&lt;=

Compare objetos `tuple` quanto a menor que ou igual a.

```cpp
template <class T1, class T2, ..., class TN,
    class U1, class U2, ..., class UN>
bool operator<=(const tuple<T1, T2, ..., TN>& tpl1,
    const tuple<U1, U2, ..., UN>& tpl2);
```

### <a name="parameters"></a>Parâmetros

*TN*\
O tipo do enésimo elemento de tupla.

### <a name="remarks"></a>Comentários

A função retorna `!(tpl2 < tpl1)`.

### <a name="example"></a>Exemplo

```cpp
// std__tuple__operator_le.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 <= c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c1 <= c0);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
true
false
```

## <a name="op_eq_eq"></a> operador = =

Compare objetos `tuple` quanto a igualdade.

```cpp
template <class T1, class T2, ..., class TN,
    class U1, class U2, ..., class UN>
bool operator==(const tuple<T1, T2, ..., TN>& tpl1,
    const tuple<U1, U2, ..., UN>& tpl2);
```

### <a name="parameters"></a>Parâmetros

*TN*\
O tipo do enésimo elemento de tupla.

### <a name="remarks"></a>Comentários

A função retorna verdadeiro quando `N` é 0, caso contrário `get<0>(tpl1) == get<0>(tpl2) && get<1>(tpl1) == get<1>(tpl2) && ... && get<N - 1>(tpl1) == get<N - 1>(tpl2)`.

### <a name="example"></a>Exemplo

```cpp
// std__tuple__operator_eq.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 == c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c0 == c1);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
true
false
```

## <a name="op_gt"></a> Operador&gt;

Compare objetos `tuple` quanto a maior que.

```cpp
template <class T1, class T2, ..., class TN,
    class U1, class U2, ..., class UN>
bool operator>(const tuple<T1, T2, ..., TN>& tpl1,
    const tuple<U1, U2, ..., UN>& tpl2);
```

### <a name="parameters"></a>Parâmetros

*TN*\
O tipo do enésimo elemento de tupla.

### <a name="remarks"></a>Comentários

A função retorna `tpl2 < tpl1`.

### <a name="example"></a>Exemplo

```cpp
// std__tuple__operator_gt.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 > c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c1 > c0);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
false
true
```

## <a name="op_gt_eq"></a> operador&gt;=

Compare objetos `tuple` quanto a maior que ou igual a.

```cpp
template <class T1, class T2, ..., class TN,
    class U1, class U2, ..., class UN>
bool operator>=(const tuple<T1, T2, ..., TN>& tpl1,
    const tuple<U1, U2, ..., UN>& tpl2);
```

### <a name="parameters"></a>Parâmetros

*TN*\
O tipo do enésimo elemento de tupla.

### <a name="remarks"></a>Comentários

A função retorna `!(tpl1 < tpl2)`.

### <a name="example"></a>Exemplo

```cpp
// std__tuple__operator_ge.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

// display results of comparisons
    std::cout << std::boolalpha << " " << (c0 >= c0);
    std::cout << std::endl;
    std::cout << std::boolalpha << " " << (c0 >= c1);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
true
false
```
