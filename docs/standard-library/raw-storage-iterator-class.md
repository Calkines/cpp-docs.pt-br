---
title: Classe raw_storage_iterator
ms.date: 11/04/2016
f1_keywords:
- memory/std::raw_storage_iterator
- memory/std::raw_storage_iterator::element_type
- memory/std::raw_storage_iterator::iter_type
helpviewer_keywords:
- std::raw_storage_iterator [C++]
- std::raw_storage_iterator [C++], element_type
- std::raw_storage_iterator [C++], iter_type
ms.assetid: 6f033f15-f48e-452a-a326-647ea2cf346f
ms.openlocfilehash: eb32d1846c4e94fbd275dcc416de4f37d9bb53f1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240371"
---
# <a name="rawstorageiterator-class"></a>Classe raw_storage_iterator

Uma classe de adaptador que é fornecida para permitir que algoritmos armazenem seus resultados na memória não inicializada.

## <a name="syntax"></a>Sintaxe

```cpp
template <class OutputIterator, class Type>
    class raw_storage_iterator
```

### <a name="parameters"></a>Parâmetros

*OutputIterator*\
Especifica o iterador de saída para o objeto que está sendo armazenado.

*Tipo*\
O tipo de objeto para o qual o armazenamento está sendo alocado.

## <a name="remarks"></a>Comentários

A classe descreve um iterador de saída que constrói objetos do tipo `Type` na sequência gerada. Um objeto da classe `raw_storage_iterator` \< **ForwardIterator**, **tipo**> acessa o armazenamento por meio de um objeto de iterador de avanço, da classe `ForwardIterator`, que você especifica quando você Construa o objeto. Para um objeto de primeira classe `ForwardIterator`, a expressão  **& \*primeiro** deve designar o armazenamento para o próximo objeto (do tipo `Type`) na sequência gerada.

Essa classe de adaptador é usada quando é necessário separar a alocação de memória e a construção de objetos. O `raw_storage_iterator` pode ser usado para copiar objetos no armazenamento não inicializado, tal como memória alocada usando a função `malloc`.

## <a name="members"></a>Membros

### <a name="constructors"></a>Construtores

|||
|-|-|
|[raw_storage_iterator](#raw_storage_iterator)|Constrói um iterador de armazenamento bruto com um iterador de saída subjacente especificado.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[element_type](#element_type)|Fornece um tipo que descreve um elemento a ser armazenado em um iterador de armazenamento bruto.|
|[iter_type](#iter_type)|Fornece um tipo que descreve um iterador que dá suporte a um iterador de armazenamento bruto.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator*](#op_star)|Um operador de desreferenciamento usado para implementar a expressão do iterador de saída \* `ii`  =  `x`.|
|[operator=](#op_eq)|Um operador de atribuição usado para implementar a expressão do iterador de armazenamento bruto \* `i`  =  `x` para armazenamento na memória.|
|[operator++](#op_add_add)|Operadores pré e pós-incremento para iteradores de armazenamento brutos.|

### <a name="element_type"></a> ELEMENT_TYPE

Fornece um tipo que descreve um elemento a ser armazenado em um iterador de armazenamento bruto.

```cpp
typedef Type element_type;
```

#### <a name="remarks"></a>Comentários

O tipo é um sinônimo do parâmetro de modelo de classe raw_storage_iterator `Type`.

### <a name="iter_type"></a> iter_type

Fornece um tipo que descreve um iterador que dá suporte a um iterador de armazenamento bruto.

```cpp
typedef ForwardIterator iter_type;
```

#### <a name="remarks"></a>Comentários

O tipo é um sinônimo do parâmetro de modelo `ForwardIterator`.

### <a name="op_star"></a> Operador\*

Um operador de desreferenciamento usado para implementar a expressão do iterador de armazenamento bruto \* *ii* = *x*.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator*();
```

#### <a name="return-value"></a>Valor de retorno

Uma referência ao iterador de armazenamento bruto

#### <a name="remarks"></a>Comentários

Os requisitos para um `ForwardIterator` são que o raw iterador de armazenamento deve satisfazer exigem somente que a expressão \* *ii* = *t* seja válida e que ela não diz nada sobre o **operador** ou o `operator=` por conta própria. Os operadores de membro nesta implementação retorna  **\*isso**, de modo que [operador =](#op_eq)(**constType**&) pode executar o repositório real em uma expressão como \* *ptr* = `val`.

#### <a name="example"></a>Exemplo

```cpp
// raw_storage_iterator_op_deref.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };

   Int &operator=(int i)
   {
      if (!bIsConstructed)
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl;
      x = i;
      return *this;
   };

   int x;

private:
   bool bIsConstructed;
};

int main( void)
{
   Int *pInt = ( Int* ) malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;
*pInt = 5;
   raw_storage_iterator< Int*, Int > it( pInt );
*it = 5;
}
```

```Output
Not constructed.
Copying 5
Constructing 5
```

### <a name="op_eq"></a> operador =

Um operador de atribuição usado para implementar a expressão do iterador de armazenamento bruto \* *i* = *x* para armazenamento na memória.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator=(
    const Type& val);
```

#### <a name="parameters"></a>Parâmetros

*Val*\
O valor do objeto do tipo `Type` a ser inserido na memória.

#### <a name="return-value"></a>Valor de retorno

O operador insere `val` na memória e, em seguida, retorna uma referência ao iterador de armazenamento bruto.

#### <a name="remarks"></a>Comentários

Os requisitos para um `ForwardIterator` estado que o iterador de armazenamento bruto deve satisfazer exigem somente que a expressão \* *ii* = *t* seja válida e que ela não diz nada sobre o **operador** ou o `operator=` por conta própria. Esses operadores de membros retornam **\*this**.

O operador de atribuição constrói o próximo objeto na sequência da saída usando o valor de iterador armazenado primeiro, avaliando a expressão de novo posicionamento **new** ( ( `void` \*)&\* **first**) **Type**( `val`).

#### <a name="example"></a>Exemplo

```cpp
// raw_storage_iterator_op_assign.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int( int i )
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if ( !bIsConstructed )
         cout << "Not constructed.\n";
      cout << "Copying " << i << endl; x = i;
      return *this;
   };
   int x;
private:
   bool bIsConstructed;
};

int main( void )
{
   Int *pInt = ( Int* )malloc( sizeof( Int ) );
   memset( pInt, 0, sizeof( Int ) ); // Set bIsConstructed to false;

*pInt = 5;

   raw_storage_iterator<Int*, Int> it( pInt );
*it = 5;
}
```

```Output
Not constructed.
Copying 5
Constructing 5
```

### <a name="op_add_add"></a> operador + +

Operadores pré e pós-incremento para iteradores de armazenamento brutos.

```cpp
raw_storage_iterator<ForwardIterator, Type>& operator++();

raw_storage_iterator<ForwardIterator, Type> operator++(int);
```

#### <a name="return-value"></a>Valor de retorno

Um iterador de armazenamento bruto ou uma referência a um iterador de armazenamento bruto.

#### <a name="remarks"></a>Comentários

O primeiro operador eventualmente tenta extrair e armazenar um objeto do tipo `CharType` do fluxo de entrada associado. O segundo operador faz uma cópia do objeto, incrementa o objeto e, em seguida, retorna a cópia.

O primeiro operador pré-incremento incrementa o objeto de iterador de saída armazenado e retorna **\*this**.

O segundo operador pós-incremento faz uma cópia de **\*this**, incrementa o objeto de iterador de saída e retorna a cópia.

O construtor armazena `first` como o objeto de iterador de saída.

#### <a name="example"></a>Exemplo

```cpp
// raw_storage_iterator_op_incr.cpp
// compile with: /EHsc
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

int main( void )
{
   int *pInt = new int[5];
   std::raw_storage_iterator<int*,int> it( pInt );
   for ( int i = 0; i < 5; i++, it++ ) {
      *it = 2 * i;
   };

   for ( int i = 0; i < 5; i++ ) cout << "array " << i << " = " << pInt[i] << endl;;

   delete[] pInt;
}
```

```Output
array 0 = 0
array 1 = 2
array 2 = 4
array 3 = 6
array 4 = 8
```

### <a name="raw_storage_iterator"></a> raw_storage_iterator

Constrói um iterador de armazenamento bruto com um iterador de saída subjacente especificado.

```cpp
explicit raw_storage_iterator(ForwardIterator first);
```

#### <a name="parameters"></a>Parâmetros

*Primeiro*\
O iterador de avanço que dá suporte ao objeto `raw_storage_iterator` que está sendo construído.

#### <a name="example"></a>Exemplo

```cpp
// raw_storage_iterator_ctor.cpp
// compile with: /EHsc /W3
#include <iostream>
#include <iterator>
#include <memory>
#include <list>
using namespace std;

class Int
{
public:
   Int(int i)
   {
      cout << "Constructing " << i << endl;
      x = i;
      bIsConstructed = true;
   };
   Int &operator=( int i )
   {
      if (!bIsConstructed)
         cout << "Error! I'm not constructed!\n";
      cout << "Copying " << i << endl;  x = i; return *this;
   };
   int x;
   bool bIsConstructed;
};

int main( void )
{
   std::list<int> l;
   l.push_back( 1 );
   l.push_back( 2 );
   l.push_back( 3 );
   l.push_back( 4 );

   Int *pInt = (Int*)malloc(sizeof(Int)*l.size( ));
   memset (pInt, 0, sizeof(Int)*l.size( ));
   // Hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ), pInt );  // C4996
   for (unsigned int i = 0; i < l.size( ); i++)
      cout << "array " << i << " = " << pInt[i].x << endl;;

   memset (pInt, 0, sizeof(Int)*l.size( ));
   // hack: make sure bIsConstructed is false

   std::copy( l.begin( ), l.end( ),
      std::raw_storage_iterator<Int*,Int>(pInt));  // C4996
   for (unsigned int i = 0; i < l.size( ); i++ )
      cout << "array " << i << " = " << pInt[i].x << endl;

   free(pInt);
}
```

```Output
Error! I'm not constructed!
Copying 1
Error! I'm not constructed!
Copying 2
Error! I'm not constructed!
Copying 3
Error! I'm not constructed!
Copying 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
Constructing 1
Constructing 2
Constructing 3
Constructing 4
array 0 = 1
array 1 = 2
array 2 = 3
array 3 = 4
```