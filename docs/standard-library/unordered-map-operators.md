---
title: Operadores &lt;unordered_map&gt;
ms.date: 11/04/2016
f1_keywords:
- unordered_map/std::operator!=
- unordered_map/std::operator==
ms.assetid: 9d5add0b-84bd-4a79-bd82-3f58b55145ed
ms.openlocfilehash: fe4877bc5b371a2570c18950bac36a003078ccc7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454778"
---
# <a name="ltunorderedmapgt-operators"></a>Operadores &lt;unordered_map&gt;

|||||
|-|-|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|[operator!=](#op_neq_multimap)|[operator==](#op_eq_eq_multimap)|

## <a name="op_neq"></a>  operator!=

Testa se o objeto [unordered_map](../standard-library/unordered-map-class.md) à esquerda do operador é diferente do objeto unordered_map à direita.

```cpp
bool operator!=(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*mantida*\
Um objeto do tipo `unordered_map`.

*Certo*\
Um objeto do tipo `unordered_map`.

### <a name="return-value"></a>Valor de retorno

**true** se os unordered_maps não forem iguais; **false** se forem iguais.

### <a name="remarks"></a>Comentários

A comparação entre objetos unordered_map não é afetada pela ordem arbitrária em que eles armazenam seus elementos. Dois unordered_maps serão iguais se tiverem o mesmo número de elementos e os elementos em um contêiner forem uma permutação dos elementos do outro contêiner. Caso contrário, são diferentes.

### <a name="example"></a>Exemplo

```cpp
// unordered_map_op_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_map<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i+1, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i+1 ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i+1, i ) );
   }

   cout << boolalpha;
   cout << "um1 != um2: " << (um1 != um2) << endl;
   cout << "um1 != um3: " << (um1 != um3) << endl;
   cout << "um2 != um3: " << (um2 != um3) << endl;
}
```

**Saída:**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="op_eq_eq"></a>  operator==

Testa se o objeto [unordered_map](../standard-library/unordered-map-class.md) à esquerda do operador é igual ao objeto unordered_map à direita.

```cpp
bool operator==(const unordered_map <Key, Type, Hash, Pred, Allocator>& left, const unordered_map <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*mantida*\
Um objeto do tipo `unordered_map`.

*Certo*\
Um objeto do tipo `unordered_map`.

### <a name="return-value"></a>Valor de retorno

**true** se os unordered_maps forem iguais; **false** se eles não forem iguais.

### <a name="remarks"></a>Comentários

A comparação entre objetos unordered_map não é afetada pela ordem arbitrária em que eles armazenam seus elementos. Dois unordered_maps serão iguais se tiverem o mesmo número de elementos e os elementos em um contêiner forem uma permutação dos elementos do outro contêiner. Caso contrário, são diferentes.

### <a name="example"></a>Exemplo

```cpp
// unordered_map_op_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_map<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i+1, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i+1 ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i+1, i ) );
   }

   cout << boolalpha;
   cout << "um1 == um2: " << (um1 == um2) << endl;
   cout << "um1 == um3: " << (um1 == um3) << endl;
   cout << "um2 == um3: " << (um2 == um3) << endl;
}
```

**Saída:**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="op_neq_multimap"></a>  operator!=

Testa se o objeto [unordered_multimap](../standard-library/unordered-multimap-class.md) à esquerda do operador é diferente do objeto unordered_multimap à direita.

```cpp
bool operator!=(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*mantida*\
Um objeto do tipo `unordered_multimap`.

*Certo*\
Um objeto do tipo `unordered_multimap`.

### <a name="return-value"></a>Valor de retorno

**true** se os unordered_multimaps não forem iguais; **false** se forem iguais.

### <a name="remarks"></a>Comentários

A comparação entre objetos unordered_multimap não é afetada pela ordem arbitrária em que eles armazenam seus elementos. Dois unordered_multimaps serão iguais se tiverem o mesmo número de elementos e os elementos em um contêiner forem uma permutação dos elementos do outro contêiner. Caso contrário, são diferentes.

### <a name="example"></a>Exemplo

```cpp
// unordered_multimap_op_ne.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_multimap<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i, i ) );
   }

   cout << boolalpha;
   cout << "um1 != um2: " << (um1 != um2) << endl;
   cout << "um1 != um3: " << (um1 != um3) << endl;
   cout << "um2 != um3: " << (um2 != um3) << endl;
}
```

**Saída:**

`um1 != um2: true`

`um1 != um3: false`

`um2 != um3: true`

## <a name="op_eq_eq_multimap"></a>  operator==

Testa se o objeto [unordered_multimap](../standard-library/unordered-multimap-class.md) à esquerda do operador é igual ao objeto unordered_multimap à direita.

```cpp
bool operator==(const unordered_multimap <Key, Type, Hash, Pred, Allocator>& left, const unordered_multimap <Key, Type, Hash, Pred, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*mantida*\
Um objeto do tipo `unordered_multimap`.

*Certo*\
Um objeto do tipo `unordered_multimap`.

### <a name="return-value"></a>Valor de retorno

**true** se os unordered_multimaps forem iguais; **false** se eles não forem iguais.

### <a name="remarks"></a>Comentários

A comparação entre objetos unordered_multimap não é afetada pela ordem arbitrária em que eles armazenam seus elementos. Dois unordered_multimaps serão iguais se tiverem o mesmo número de elementos e os elementos em um contêiner forem uma permutação dos elementos do outro contêiner. Caso contrário, são diferentes.

### <a name="example"></a>Exemplo

```cpp
// unordered_multimap_op_eq.cpp
// compile by using: cl.exe /EHsc /nologo /W4 /MTd
#include <unordered_map>
#include <iostream>
#include <ios>

int main( )
{
   using namespace std;
   unordered_multimap<int, int> um1, um2, um3;

   for ( int i = 0 ; i < 3 ; ++i ) {
      um1.insert( make_pair( i, i ) );
      um1.insert( make_pair( i, i ) );

      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );
      um2.insert( make_pair( i, i ) );

      um3.insert( make_pair( i, i ) );
      um3.insert( make_pair( i, i ) );
   }

   cout << boolalpha;
   cout << "um1 == um2: " << (um1 == um2) << endl;
   cout << "um1 == um3: " << (um1 == um3) << endl;
   cout << "um2 == um3: " << (um2 == um3) << endl;
}
```

**Saída:**

`um1 == um2: false`

`um1 == um3: true`

`um2 == um3: false`

## <a name="see-also"></a>Consulte também

[<unordered_map>](../standard-library/unordered-map.md)
