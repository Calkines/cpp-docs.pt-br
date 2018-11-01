---
title: Operadores &lt;set&gt;
ms.date: 11/04/2016
f1_keywords:
- set/std::operator!=
- set/std::operator&gt;
- set/std::operator&gt;=
- set/std::operator&lt;
- set/std::operator&lt;=
- set/std::operator==
ms.assetid: b4256ebc-c449-4688-95db-fced42d20d4d
helpviewer_keywords:
- std::operator!= (set)
- std::operator&gt; (set)
- std::operator&gt;= (set)
- std::operator&lt; (set)
- std::operator&lt;= (set)
- std::operator== (set)
ms.openlocfilehash: f6354da2a7b4cf6419be4aae1a8d5f20356a4012
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441815"
---
# <a name="ltsetgt-operators"></a>Operadores &lt;set&gt;

||||
|-|-|-|
|[operator!= (set)](#op_neq)|[operator&gt; (set)](#op_gt)|[operator&gt;= (set)](#eq)|
|[operator&lt; (set)](#op_lt)|[operator&lt;= (set)](#eq)|[operator== (set)](#op_eq_eq)|
|[operator!= (multiset)](#op_neq_multiset)|[operator&gt; (multiset)](#op_gt_multiset)|[operator&gt;= (multiset)](#op_gt_eq_multiset)|
|[operator&lt; (multiset)](#op_lt_multiset)|[operator&lt;= (multiset)](#op_lt_eq_multiset)|[operator== (multiset)](#op_eq_eq_multiset)|

## <a name="op_neq"></a>  operator!= (set)

Testa se o objeto set à esquerda do operador é diferente do objeto set à direita.

```cpp
bool operator!=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*left*<br/>
Um objeto do tipo `set`.

*right*<br/>
Um objeto do tipo `set`.

### <a name="return-value"></a>Valor de retorno

**true** se os sets não forem iguais; **false** se os sets forem iguais.

### <a name="remarks"></a>Comentários

A comparação entre os objetos set é baseada em uma comparação de paridade de seus elementos. Dois sets serão iguais se tiverem o mesmo número de elementos e seus respectivos elementos tiverem os mesmos valores. Caso contrário, são diferentes.

### <a name="example"></a>Exemplo

```cpp
// set_op_ne.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 != s2 )
      cout << "The sets s1 and s2 are not equal." << endl;
   else
      cout << "The sets s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The sets s1 and s3 are not equal." << endl;
   else
      cout << "The sets s1 and s3 are equal." << endl;
}
/* Output:
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
*/
```

## <a name="op_lt"></a>  operator&lt; (set)

Testa se o objeto set à esquerda do operador é menor do que o objeto set à direita.

```cpp
bool operator<(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*left*<br/>
Um objeto do tipo `set`.

*right*<br/>
Um objeto do tipo `set`.

### <a name="return-value"></a>Valor de retorno

**true**, se o set à esquerda do operador for estritamente menor que o set à direita do operador; caso contrário, **false**.

### <a name="remarks"></a>Comentários

A comparação entre os objetos set baseia-se em uma comparação par de seus elementos. A relação menor que entre dois objetos é baseada em uma comparação do primeiro par de elementos desiguais.

### <a name="example"></a>Exemplo

```cpp
// set_op_lt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 < s2 )
      cout << "The set s1 is less than the set s2." << endl;
   else
      cout << "The set s1 is not less than the set s2." << endl;

   if ( s1 < s3 )
      cout << "The set s1 is less than the set s3." << endl;
   else
      cout << "The set s1 is not less than the set s3." << endl;
}
/* Output:
The set s1 is less than the set s2.
The set s1 is not less than the set s3.
*/
```

## <a name="op_lt_eq"></a>  operator&lt;= (set)

Testa se o objeto set à esquerda do operador é menor ou igual ao objeto set à direita.

```cpp
bool operator!<=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*left*<br/>
Um objeto do tipo `set`.

*right*<br/>
Um objeto do tipo `set`.

### <a name="return-value"></a>Valor de retorno

**true**, se o set à esquerda do operador for menor ou igual ao set à direita do operador; caso contrário, **false**.

### <a name="remarks"></a>Comentários

A comparação entre os objetos set baseia-se em uma comparação par de seus elementos. A relação menor que ou igual a entre dois objetos é baseada em uma comparação entre o primeiro par de elementos desiguais.

### <a name="example"></a>Exemplo

```cpp
// set_op_le.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 <= s2 )
      cout << "Set s1 is less than or equal to the set s2." << endl;
   else
      cout << "The set s1 is greater than the set s2." << endl;

   if ( s1 <= s3 )
      cout << "Set s1 is less than or equal to the set s3." << endl;
   else
      cout << "The set s1 is greater than the set s3." << endl;

   if ( s1 <= s4 )
      cout << "Set s1 is less than or equal to the set s4." << endl;
   else
      cout << "The set s1 is greater than the set s4." << endl;
}
/* Output:
Set s1 is less than or equal to the set s2.
The set s1 is greater than the set s3.
Set s1 is less than or equal to the set s4.
*/
```

## <a name="op_eq_eq"></a>  operator== (set)

Testa se o objeto set à esquerda do operador é igual ao objeto set à direita.

```cpp
bool operator!==(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*left*<br/>
Um objeto do tipo `set`.

*right*<br/>
Um objeto do tipo `set`.

### <a name="return-value"></a>Valor de retorno

**true**, se o set à esquerda do operador for igual ao set à direita do operador; caso contrário, **false**.

### <a name="remarks"></a>Comentários

A comparação entre os objetos set baseia-se em uma comparação par de seus elementos. Dois sets serão iguais se tiverem o mesmo número de elementos e seus respectivos elementos tiverem os mesmos valores. Caso contrário, são diferentes.

### <a name="example"></a>Exemplo

```cpp
// set_op_eq.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The sets s1 and s2 are equal." << endl;
   else
      cout << "The sets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The sets s1 and s3 are equal." << endl;
   else
      cout << "The sets s1 and s3 are not equal." << endl;
}
/* Output:
The sets s1 and s2 are not equal.
The sets s1 and s3 are equal.
*/
```

## <a name="op_gt"></a>  operator&gt; (set)

Testa se o objeto set à esquerda do operador é maior que o objeto set à direita.

```cpp
bool operator>(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*left*<br/>
Um objeto do tipo `set`.

*right*<br/>
Um objeto do tipo `set`.

### <a name="return-value"></a>Valor de retorno

**true**, se o set à esquerda do operador for maior que o set à direita do operador; caso contrário, **false**.

### <a name="remarks"></a>Comentários

A comparação entre os objetos set baseia-se em uma comparação par de seus elementos. A relação maior que entre dois objetos é baseada em uma comparação entre o primeiro par de elementos desiguais.

### <a name="example"></a>Exemplo

```cpp
// set_op_gt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 > s2 )
      cout << "The set s1 is greater than the set s2." << endl;
   else
      cout << "The set s1 is not greater than the set s2." << endl;

   if ( s1 > s3 )
      cout << "The set s1 is greater than the set s3." << endl;
   else
      cout << "The set s1 is not greater than the set s3." << endl;
}
/* Output:
The set s1 is not greater than the set s2.
The set s1 is greater than the set s3.
*/
```

## <a name="op_gt_eq"></a>  operator&gt;= (set)

Testa se o objeto set à esquerda do operador é maior ou igual ao objeto set à direita.

```cpp
bool operator!>=(const set <Key, Traits, Allocator>& left, const set <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*left*<br/>
Um objeto do tipo `set`.

*right*<br/>
Um objeto do tipo `set`.

### <a name="return-value"></a>Valor de retorno

**true**, se o set à esquerda do operador for maior ou igual ao set à direita do operador; caso contrário, **false**.

### <a name="remarks"></a>Comentários

A comparação entre os objetos set baseia-se em uma comparação par de seus elementos. A relação maior que ou igual entre dois objetos é baseada em uma comparação entre o primeiro par de elementos diferentes.

### <a name="example"></a>Exemplo

```cpp
// set_op_ge.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 >= s2 )
      cout << "Set s1 is greater than or equal to set s2." << endl;
   else
      cout << "The set s1 is less than the set s2." << endl;

   if ( s1 >= s3 )
      cout << "Set s1 is greater than or equal to set s3." << endl;
   else
      cout << "The set s1 is less than the set s3." << endl;

   if ( s1 >= s4 )
      cout << "Set s1 is greater than or equal to set s4." << endl;
   else
      cout << "The set s1 is less than the set s4." << endl;
}
/* Output:
The set s1 is less than the set s2.
Set s1 is greater than or equal to set s3.
Set s1 is greater than or equal to set s4.
*/
```

## <a name="op_neq_multiset"></a>  operator!= (multiset)

Testa se o objeto multiset à esquerda do operador é diferente do objeto multiset à direita.

```cpp
bool operator!=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*left*<br/>
Um objeto do tipo `multiset`.

*right*<br/>
Um objeto do tipo `multiset`.

### <a name="return-value"></a>Valor de retorno

**true** se os sets ou multisets não forem iguais; **false** se os sets ou multisets forem iguais.

### <a name="remarks"></a>Comentários

A comparação entre os objetos multiset é baseada em uma comparação de paridade de seus elementos. Dois sets ou multisets serão iguais se tiverem o mesmo número de elementos e seus respectivos elementos tiverem os mesmos valores. Caso contrário, são diferentes.

### <a name="example"></a>Exemplo

```cpp
// multiset_op_ne.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 != s2 )
      cout << "The multisets s1 and s2 are not equal." << endl;
   else
      cout << "The multisets s1 and s2 are equal." << endl;

   if ( s1 != s3 )
      cout << "The multisets s1 and s3 are not equal." << endl;
   else
      cout << "The multisets s1 and s3 are equal." << endl;
}
/* Output:
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
*/
```

## <a name="op_lt_multiset"></a>  operator&lt; (multiset)

Testa se o objeto multiset à esquerda do operador é menor que o objeto multiset à direita.

```cpp
bool operator<(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*left*<br/>
Um objeto do tipo `multiset`.

*right*<br/>
Um objeto do tipo `multiset`.

### <a name="return-value"></a>Valor de retorno

**true** se o multiset à esquerda do operador for estritamente menor que o multiset à direita do operador; caso contrário, **false**.

### <a name="remarks"></a>Comentários

A comparação entre os objetos multiset baseia-se em uma comparação par de seus elementos. A relação menor que entre dois objetos é baseada em uma comparação do primeiro par de elementos desiguais.

### <a name="example"></a>Exemplo

```cpp
// multiset_op_lt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 < s2 )
      cout << "The multiset s1 is less than "
           << "the multiset s2." << endl;
   else
      cout << "The multiset s1 is not less than "
           << "the multiset s2." << endl;

   if ( s1 < s3 )
      cout << "The multiset s1 is less than "
           << "the multiset s3." << endl;
   else
      cout << "The multiset s1 is not less than "
           << "the multiset s3." << endl;
}
/* Output:
The multiset s1 is less than the multiset s2.
The multiset s1 is not less than the multiset s3.
*/
```

## <a name="op_lt_eq_multiset"></a>  operator&lt;= (multiset)

Testa se o objeto multiset à esquerda do operador é menor ou igual ao objeto multiset à direita.

```cpp
bool operator!<=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*left*<br/>
Um objeto do tipo `multiset`.

*right*<br/>
Um objeto do tipo `multiset`.

### <a name="return-value"></a>Valor de retorno

**true** se o multiset à esquerda do operador for menor ou igual ao multiset à direita do operador; caso contrário, **false**.

### <a name="remarks"></a>Comentários

A comparação entre os objetos multiset baseia-se em uma comparação par de seus elementos. A relação menor que ou igual a entre dois objetos é baseada em uma comparação entre o primeiro par de elementos desiguais.

### <a name="example"></a>Exemplo

```cpp
// multiset_op_le.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 <= s2 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s2." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s2." << endl;

   if ( s1 <= s3 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s3." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s3." << endl;

   if ( s1 <= s4 )
      cout << "The multiset s1 is less than "
           << "or equal to the multiset s4." << endl;
   else
      cout << "The multiset s1 is greater than "
           << "the multiset s4." << endl;
}
/* Output:
The multiset s1 is less than or equal to the multiset s2.
The multiset s1 is greater than the multiset s3.
The multiset s1 is less than or equal to the multiset s4.
*/
```

## <a name="op_eq_eq_multiset"></a>  operator== (multiset)

Testa se o objeto multiset à esquerda do operador é igual ao objeto multiset à direita.

```cpp
bool operator!==(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*left*<br/>
Um objeto do tipo `multiset`.

*right*<br/>
Um objeto do tipo `multiset`.

### <a name="return-value"></a>Valor de retorno

**true** se o multiset à esquerda do operador for igual ao multiset à direita do operador; caso contrário, **false**.

### <a name="remarks"></a>Comentários

A comparação entre os objetos multiset baseia-se em uma comparação par de seus elementos. Dois sets ou multisets serão iguais se tiverem o mesmo número de elementos e seus respectivos elementos tiverem os mesmos valores. Caso contrário, são diferentes.

### <a name="example"></a>Exemplo

```cpp
// multiset_op_eq.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i );
   }

   if ( s1 == s2 )
      cout << "The multisets s1 and s2 are equal." << endl;
   else
      cout << "The multisets s1 and s2 are not equal." << endl;

   if ( s1 == s3 )
      cout << "The multisets s1 and s3 are equal." << endl;
   else
      cout << "The multisets s1 and s3 are not equal." << endl;
}
/* Output:
The multisets s1 and s2 are not equal.
The multisets s1 and s3 are equal.
*/
```

## <a name="op_gt_multiset"></a>  operator&gt; (multiset)

Testa se o objeto multiset à esquerda do operador é maior que o objeto multiset à direita.

```cpp
bool operator>(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*left*<br/>
Um objeto do tipo `multiset`.

*right*<br/>
Um objeto do tipo `multiset`.

### <a name="return-value"></a>Valor de retorno

**true** se o multiset à esquerda do operador for maior que o multiset à direita do operador; caso contrário, **false**.

### <a name="remarks"></a>Comentários

A comparação entre os objetos multiset baseia-se em uma comparação par de seus elementos. A relação maior que entre dois objetos é baseada em uma comparação entre o primeiro par de elementos desiguais.

### <a name="example"></a>Exemplo

```cpp
// multiset_op_gt.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
   }

   if ( s1 > s2 )
      cout << "The multiset s1 is greater than "
           << "the multiset s2." << endl;
   else
      cout << "The multiset s1 is not greater "
           << "than the multiset s2." << endl;

   if ( s1 > s3 )
      cout << "The multiset s1 is greater than "
           << "the multiset s3." << endl;
   else
      cout << "The multiset s1 is not greater than "
           << "the multiset s3." << endl;
}
/* Output:
The multiset s1 is not greater than the multiset s2.
The multiset s1 is greater than the multiset s3.
*/
```

## <a name="op_gt_eq_multiset"></a>  operator&gt;= (multiset)

Testa se o objeto multiset à esquerda do operador é maior ou igual ao objeto multiset à direita.

```cpp
bool operator!>=(const multiset <Key, Traits, Allocator>& left, const multiset <Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*left*<br/>
Um objeto do tipo `multiset`.

*right*<br/>
Um objeto do tipo `multiset`.

### <a name="return-value"></a>Valor de retorno

**true** se o multiset à esquerda do operador for maior ou igual ao multiset à direita do operador; caso contrário, **false**.

### <a name="remarks"></a>Comentários

A comparação entre os objetos multiset baseia-se em uma comparação par de seus elementos. A relação maior que ou igual entre dois objetos é baseada em uma comparação entre o primeiro par de elementos diferentes.

### <a name="example"></a>Exemplo

```cpp
// multiset_op_ge.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   multiset <int> s1, s2, s3, s4;
   int i;

   for ( i = 0 ; i < 3 ; i++ )
   {
      s1.insert ( i );
      s2.insert ( i * i );
      s3.insert ( i - 1 );
      s4.insert ( i );
   }

   if ( s1 >= s2 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s2." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s2." << endl;

   if ( s1 >= s3 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s3." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s3." << endl;

   if ( s1 >= s4 )
      cout << "The multiset s1 is greater than "
           << "or equal to the multiset s4." << endl;
   else
      cout << "The multiset s1 is less than "
           << "the multiset s4." << endl;
}
/* Output:
The multiset s1 is less than the multiset s2.
The multiset s1 is greater than or equal to the multiset s3.
The multiset s1 is greater than or equal to the multiset s4.
*/
```

## <a name="see-also"></a>Consulte também

[\<set>](../standard-library/set.md)<br/>
