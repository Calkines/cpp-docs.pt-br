---
title: Funções &lt;unordered_set&gt;
ms.date: 11/04/2016
f1_keywords:
- unordered_set/std::swap (set)
- unordered_set/std::swap (unordered_multiset)
ms.assetid: 66b35671-4023-4411-ad50-83786580d8ee
ms.openlocfilehash: f34d818c1829baba1740bf2776b2d47a8808bf68
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243423"
---
# <a name="ltunorderedsetgt-functions"></a>Funções &lt;unordered_set&gt;

## <a name="swap"></a> swap (unordered_set)

Alterna o conteúdo de dois contêineres.

```

template <class Key, class Hash, class Pred, class Alloc>
void swap(
   unordered_set <Key, Hash, Pred, Alloc>& left,
   unordered_set <Key, Hash, Pred, Alloc>& right);
```

### <a name="parameters"></a>Parâmetros

*Chave*\
O tipo principal.

*hash*\
O tipo de objeto da função de hash.

*Pred*\
O tipo de objeto da função de comparação de igualdade.

*ALLOC*\
A classe do alocador.

*À esquerda*\
O primeiro contêiner para alternância.

*Certo*\
O segundo contêiner para alternância.

### <a name="remarks"></a>Comentários

A função de modelo executa `left.`[unordered_set::swap](../standard-library/unordered-set-class.md#swap)`(right)`.

### <a name="example"></a>Exemplo

```cpp
#include <unordered_set>
#include <iostream>

typedef std::unordered_set<char> Myset;
int main()
{
Myset c1;

c1.insert('a');
c1.insert('b');
c1.insert('c');

// display contents " [c] [b] [a]"
for (Myset::const_iterator it = c1.begin();
it != c1.end(); ++it)
std::cout << " [" << *it << "]";
std::cout << std::endl;

Myset c2;

c2.insert('d');
c2.insert('e');
c2.insert('f');

c1.swap(c2);

// display contents " [f] [e] [d]"
for (Myset::const_iterator it = c1.begin();
it != c1.end(); ++it)
std::cout << " [" << *it << "]";
std::cout << std::endl;

swap(c1, c2);

// display contents " [c] [b] [a]"
for (Myset::const_iterator it = c1.begin();
it != c1.end(); ++it)
std::cout << " [" << *it << "]";
std::cout << std::endl;

return (0);
}
```

```Output
[c] [b] [a]
[f] [e] [d]
[c] [b] [a]
```

## <a name="swap_unordered_multiset"></a> swap (unordered_multiset)

Alterna o conteúdo de dois contêineres.

```
template <class Key, class Hash, class Pred, class Alloc>
void swap(
   unordered_multiset <Key, Hash, Pred, Alloc>& left,
   unordered_multiset <Key, Hash, Pred, Alloc>& right);
```

### <a name="parameters"></a>Parâmetros

*Chave*\
O tipo principal.

*hash*\
O tipo de objeto da função de hash.

*Pred*\
O tipo de objeto da função de comparação de igualdade.

*ALLOC*\
A classe do alocador.

*À esquerda*\
O primeiro contêiner para alternância.

*Certo*\
O segundo contêiner para alternância.

### <a name="remarks"></a>Comentários

A função de modelo executa `left.`[unordered_multiset::swap](../standard-library/unordered-multiset-class.md#swap)`(right)`.

### <a name="example"></a>Exemplo

```cpp
// std__unordered_set__u_ms_swap.cpp
// compile with: /EHsc
#include <unordered_set>
#include <iostream>

typedef std::unordered_multiset<char> Myset;
int main()
{
    Myset c1;

    c1.insert('a');
    c1.insert('b');
    c1.insert('c');

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    Myset c2;

    c2.insert('d');
    c2.insert('e');
    c2.insert('f');

    c1.swap(c2);

    // display contents " [f] [e] [d]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    swap(c1, c2);

    // display contents " [c] [b] [a]"
    for (Myset::const_iterator it = c1.begin();
        it != c1.end(); ++it)
        std::cout << " [" << *it << "]";
    std::cout << std::endl;

    return (0);
}
```

```Output
[c] [b] [a]
[f] [e] [d]
[c] [b] [a]
```
