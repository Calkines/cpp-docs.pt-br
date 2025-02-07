---
title: utility (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/utility>
- cliext::pair
- cliext::pair::pair
- cliext::pair::first
- cliext::pair::first_type
- cliext::pair::second
- cliext::pair::second_type
- cliext::pair::swap
- cliext::make_pair
- cliext::pair::operator=
- cliext::pair::operator==
- cliext::pair::operator>=
- cliext::pair::operator>
- cliext::pair::operator!=
- cliext::pair::operator<=
- cliext::pair::operator<
helpviewer_keywords:
- <utility> header [STL/CLR]
- utility header [STL/CLR]
- <cliext/utility> header [STL/CLR]
- first member [STL/CLR]
- first_type member [STL/CLR]
- second member [STL/CLR]
- second_type member [STL/CLR]
- swap member [STL/CLR]
- make_pair function [STL/CLR]
- pair class [STL/CLR]
- pair member [STL/CLR]
- operator== member [STL/CLR]
- operator= member [STL/CLR]
- operator>= member [STL/CLR]
- operator> member [STL/CLR]
- operator!= member [STL/CLR]
- operator<= member [STL/CLR]
- operator< member [STL/CLR]
ms.assetid: fb48cb75-d5ef-47ce-b526-bf60dc86c552
ms.openlocfilehash: 1a884a75fbc3ba979402c94c67d2915863a847e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384459"
---
# <a name="utility-stlclr"></a>utility (STL/CLR)

Inclua o cabeçalho STL/CLR `<cliext/utility>` para definir a classe de modelo `pair` e várias funções de modelo de suporte.

## <a name="syntax"></a>Sintaxe

```cpp
#include <utility>
```

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<cliext/utilitário >

**Namespace:** cliext

## <a name="declarations"></a>Declarações

|Classe|Descrição|
|-----------|-----------------|
|[pair (STL/CLR)](#pair)|Encapsule um par de elementos.|

|Operador|Descrição|
|--------------|-----------------|
|[operator== (pair) (STL/CLR)](#op_eq)|Comparação de igualdade de par.|
|[operator!= (pair) (STL/CLR)](#op_neq)|Par não igual a comparação.|
|[operator< (pair) (STL/CLR)](#op_lt)|Par menor do que a comparação.|
|[operator\<= (pair) (STL/CLR)](#op_lteq)|Emparelhe menor ou igual comparação.|
|[operator> (pair) (STL/CLR)](#op_gt)|Maior que a comparação do par.|
|[operator>= (pair) (STL/CLR)](#op_gteq)|Par de maior que ou igual comparação.|

|Função|Descrição|
|--------------|-----------------|
|[make_pair (STL/CLR)](#make_pair)|Tornar um par de um par de valores.|

## <a name="members"></a>Membros

## <a name="pair"></a> pair (STL/CLR)
A classe de modelo descreve um objeto que encapsula um par de valores.

### <a name="syntax"></a>Sintaxe

```cpp
template<typename Value1,
    typename Value2>
    ref class pair;
```

#### <a name="parameters"></a>Parâmetros

*Value1*<br/>
O tipo do primeiro valor encapsulado.

*Value2*<br/>
O tipo do segundo valor encapsulado.

## <a name="members"></a>Membros

|Definição do tipo|Descrição|
|---------------------|-----------------|
|[pair::first_type (STL/CLR)](#first_type)|O tipo do primeiro valor encapsulado.|
|[pair::second_type (STL/CLR)](#second_type)|O tipo do segundo valor encapsulado.|

|Objeto de membro|Descrição|
|-------------------|-----------------|
|[pair::first (STL/CLR)](#first)|O primeiro valor armazenado.|
|[pair::second (STL/CLR)](#second)|O segundo valor armazenado.|

|Função membro|Descrição|
|---------------------|-----------------|
|[pair::pair (STL/CLR)](#pair_pair)|Constrói um objeto do par.|
|[pair::swap (STL/CLR)](#swap)|Troca o conteúdo de dois pares.|

|Operador|Descrição|
|--------------|-----------------|
|[pair::operator= (STL/CLR)](#op_as)|Substitui o par de valores armazenado.|

## <a name="remarks"></a>Comentários

O objeto armazena um par de valores. Você pode usar essa classe de modelo para combinar dois valores em um único objeto. Além disso, o objeto `cliext::pair` (descrita aqui) armazena apenas os tipos gerenciados; para armazenar um par de não gerenciado tipos usam `std::pair`, declarado em `<utility>`.

## <a name="first"></a> pair::first (STL/CLR)

O primeiro valor encapsulado.

### <a name="syntax"></a>Sintaxe

```cpp
Value1 first;
```

### <a name="remarks"></a>Comentários

O objeto armazena o primeiro valor encapsulado.

### <a name="example"></a>Exemplo

```cpp
// cliext_pair_first.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="first_type"></a> pair::first_type (STL/CLR)

O tipo do primeiro valor encapsulado.

### <a name="syntax"></a>Sintaxe

```cpp
typedef Value1 first_type;
```

### <a name="remarks"></a>Comentários

O tipo é um sinônimo do parâmetro de modelo *Value1*.

### <a name="example"></a>Exemplo

```cpp
// cliext_pair_first_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="op_as"></a> pair::operator= (STL/CLR)

Substitui o par de valores armazenado.

### <a name="syntax"></a>Sintaxe

```cpp
pair<Value1, Value2>% operator=(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parâmetros

*right*<br/>
Par para copiar.

### <a name="remarks"></a>Comentários

As cópias de operador de membro *certa* ao objeto, em seguida, retorna `*this`. Você pode usá-lo para substituir o par de valores armazenado com uma cópia do par de valores em armazenado *certa*.

### <a name="example"></a>Exemplo

```cpp
// cliext_pair_operator_as.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

// assign to a new pair
    cliext::pair<wchar_t, int> c2;
    c2 = c1;
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);
    return (0);
    }
```

```Output
[x, 3]
[x, 3]
```

## <a name="pair_pair"></a> pair::pair (STL/CLR)

Constrói um objeto do par.

### <a name="syntax"></a>Sintaxe

```cpp
pair();
pair(pair<Coll>% right);
pair(pair<Coll>^ right);
pair(Value1 val1, Value2 val2);
```

#### <a name="parameters"></a>Parâmetros

*right*<br/>
Par para armazenar.

*val1*<br/>
Primeiro valor para armazenar.

*val2*<br/>
Segundo valor para armazenar.

### <a name="remarks"></a>Comentários

O construtor:

`pair();`

inicializa o par armazenado com valores padrão construído.

O construtor:

`pair(pair<Value1, Value2>% right);`

inicializa o par armazenado com `right.` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) e `right.` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

`pair(pair<Value1, Value2>^ right);`

inicializa o par armazenado com `right->` [pair::first (STL/CLR)](../dotnet/pair-first-stl-clr.md) e `right>` [pair::second (STL/CLR)](../dotnet/pair-second-stl-clr.md).

O construtor:

`pair(Value1 val1, Value2 val2);`

inicializa o par armazenado com *val1* e *val2*.

### <a name="example"></a>Exemplo

```cpp
// cliext_pair_construct.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
// construct an empty container
    cliext::pair<wchar_t, int> c1;
    System::Console::WriteLine("[{0}, {1}]",
        c1.first == L'\0' ? "\\0" : "??", c1.second);

// construct with a pair of values
    cliext::pair<wchar_t, int> c2(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

// construct by copying another pair
    cliext::pair<wchar_t, int> c3(c2);
    System::Console::WriteLine("[{0}, {1}]", c3.first, c3.second);

// construct by copying a pair handle
    cliext::pair<wchar_t, int> c4(%c3);
    System::Console::WriteLine("[{0}, {1}]", c4.first, c4.second);

    return (0);
    }
```

```Output
[\0, 0]
[x, 3]
[x, 3]
[x, 3]
```

## <a name="second"></a> pair::second (STL/CLR)

O segundo valor encapsulado.

### <a name="syntax"></a>Sintaxe

```cpp
Value2 second;
```

### <a name="remarks"></a>Comentários

O objeto armazena o segundo valor encapsulado.

### <a name="example"></a>Exemplo

```cpp
// cliext_pair_second.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="second_type"></a> pair::second_type (STL/CLR)

O tipo do segundo valor encapsulado.

### <a name="syntax"></a>Sintaxe

```cpp
typedef Value2 second_type;
```

### <a name="remarks"></a>Comentários

O tipo é um sinônimo do parâmetro de modelo *Value2*.

### <a name="example"></a>Exemplo

```cpp
// cliext_pair_second_type.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    cliext::pair<wchar_t, int>::first_type first_val = c1.first;
    cliext::pair<wchar_t, int>::second_type second_val = c1.second;
    System::Console::WriteLine("[{0}, {1}]", first_val, second_val);
    return (0);
    }
```

```Output
[x, 3]
```

## <a name="swap"></a> pair::swap (STL/CLR)

Troca o conteúdo de dois pares.

### <a name="syntax"></a>Sintaxe

```cpp
void swap(pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parâmetros

*right*<br/>
Par para trocar conteúdo com.

### <a name="remarks"></a>Comentários

A função membro troca o par de valores entre armazenado `*this` e *direito*.

### <a name="example"></a>Exemplo

```cpp
// cliext_pair_swap.cpp
// compile with: /clr
#include <cliext/adapter>
#include <cliext/deque>

typedef cliext::collection_adapter<
    System::Collections::ICollection> Mycoll;
int main()
    {
    cliext::deque<wchar_t> d1;
    d1.push_back(L'a');
    d1.push_back(L'b');
    d1.push_back(L'c');
    Mycoll c1(%d1);

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    cliext::deque<wchar_t> d2(5, L'x');
    Mycoll c2(%d2);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x x x x x
x x x x x
a b c
```

## <a name="make_pair"></a> make_pair (STL/CLR)

Tornar um `pair` de um par de valores.

### <a name="syntax"></a>Sintaxe

```cpp
template<typename Value1,
    typename Value2>
    pair<Value1, Value2> make_pair(Value1 first, Value2 second);
```

#### <a name="parameters"></a>Parâmetros

*Value1*<br/>
O tipo do primeiro valor encapsulado.

*Value2*<br/>
O tipo do segundo valor encapsulado.

*first*<br/>
Primeiro valor a ser encapsulado.

*second*<br/>
Segundo valor a ser encapsulado.

### <a name="remarks"></a>Comentários

A função do modelo retorna `pair<Value1, Value2>(first, second)`. Você pode usá-lo para construir um `pair<Value1, Value2>` objeto a partir de um par de valores.

### <a name="example"></a>Exemplo

```cpp
// cliext_make_pair.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);

    c1 = cliext::make_pair(L'y', 4);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    return (0);
    }
```

```Output
[x, 3]
[y, 4]
```

## <a name="op_neq"></a> operator!= (pair) (STL/CLR)

Par não igual a comparação.

### <a name="syntax"></a>Sintaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator!=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parâmetros

*left*<br/>
Par esquerdo a ser comparado.

*right*<br/>
Par correto a ser comparado.

### <a name="remarks"></a>Comentários

Retorna a função de operador `!(left == right)`. Usá-lo para testar se *esquerdo* não for ordenado igual *direita* quando os dois pares são comparado elemento por elemento.

### <a name="example"></a>Exemplo

```cpp
// cliext_pair_operator_ne.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] != [x 3] is {0}",
        c1 != c1);
    System::Console::WriteLine("[x 3] != [x 4] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] != [x 3] is False
[x 3] != [x 4] is True
```

## <a name="op_lt"></a> operador&lt; (pair) (STL/CLR)

Par menor do que a comparação.

### <a name="syntax"></a>Sintaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator<(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parâmetros

*left*<br/>
Par esquerdo a ser comparado.

*right*<br/>
Par correto a ser comparado.

### <a name="remarks"></a>Comentários

Retorna a função de operador `left.first <` `right.first || !(right.first <` `left.first &&` `left.second <` `right.second`. Usá-lo para testar se *esquerdo* é ordenada o antes *direita* quando os dois pares são comparado elemento por elemento.

### <a name="example"></a>Exemplo

```cpp
// cliext_pair_operator_lt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] < [x 3] is {0}",
        c1 < c1);
    System::Console::WriteLine("[x 3] < [x 4] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] < [x 3] is False
[x 3] < [x 4] is True
```

## <a name="op_lteq"></a> operador&lt;= (pair) (STL/CLR)

Emparelhe menor ou igual comparação.

### <a name="syntax"></a>Sintaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator<=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parâmetros

*left*<br/>
Par esquerdo a ser comparado.

*right*<br/>
Par correto a ser comparado.

### <a name="remarks"></a>Comentários

Retorna a função de operador `!(right < left)`. Usá-lo para testar se *esquerdo* não for ordenado após *direita* quando os dois pares são comparado elemento por elemento.

### <a name="example"></a>Exemplo

```cpp
// cliext_pair_operator_le.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] <= [x 3] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[x 4] <= [x 3] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] <= [x 3] is True
[x 4] <= [x 3] is False
```

## <a name="op_eq"></a> operator== (pair) (STL/CLR)

Comparação de igualdade de par.

### <a name="syntax"></a>Sintaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator==(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parâmetros

*left*<br/>
Par esquerdo a ser comparado.

*right*<br/>
Par correto a ser comparado.

### <a name="remarks"></a>Comentários

Retorna a função de operador `left.first ==` `right.first &&` `left.second ==` `right.second`. Usá-lo para testar se *esquerdo* é ordenada igual *direita* quando os dois pares são comparado elemento por elemento.

### <a name="example"></a>Exemplo

```cpp
// cliext_pair_operator_eq.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] == [x 3] is {0}",
        c1 == c1);
    System::Console::WriteLine("[x 3] == [x 4] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] == [x 3] is True
[x 3] == [x 4] is False
```

## <a name="op_gt"></a> operador&gt; (pair) (STL/CLR)

Maior que a comparação do par.

### <a name="syntax"></a>Sintaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator>(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parâmetros

*left*<br/>
Par esquerdo a ser comparado.

*right*<br/>
Par correto a ser comparado.

### <a name="remarks"></a>Comentários

Retorna a função de operador `right` `<` `left`. Usá-lo para testar se *esquerdo* é ordenada após *direita* quando os dois pares são comparado elemento por elemento.

### <a name="example"></a>Exemplo

```cpp
// cliext_pair_operator_gt.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] > [x 3] is {0}",
        c1 > c1);
    System::Console::WriteLine("[x 4] > [x 3] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] > [x 3] is False
[x 4] > [x 3] is True
```

## <a name="op_gteq"></a> operador&gt;= (pair) (STL/CLR)

Par de maior que ou igual comparação.

### <a name="syntax"></a>Sintaxe

```cpp
template<typename Value1,
    typename Value2>
    bool operator>=(pair<Value1, Value2>% left,
        pair<Value1, Value2>% right);
```

#### <a name="parameters"></a>Parâmetros

*left*<br/>
Par esquerdo a ser comparado.

*right*<br/>
Par correto a ser comparado.

### <a name="remarks"></a>Comentários

Retorna a função de operador `!(left < right)`. Usá-lo para testar se *esquerdo* não for ordenado antes *direita* quando os dois pares são comparado elemento por elemento.

### <a name="example"></a>Exemplo

```cpp
// cliext_pair_operator_ge.cpp
// compile with: /clr
#include <cliext/utility>

int main()
    {
    cliext::pair<wchar_t, int> c1(L'x', 3);
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);
    cliext::pair<wchar_t, int> c2(L'x', 4);
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);

    System::Console::WriteLine("[x 3] >= [x 3] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[x 3] >= [x 4] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
[x, 3]
[x, 4]
[x 3] >= [x 3] is True
[x 3] >= [x 4] is False
```