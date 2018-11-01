---
title: Classe Platform::Collections::VectorViewIterator
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorViewIterator::VectorViewIterator
helpviewer_keywords:
- VectorViewIterator Class
ms.assetid: be3aa1ae-e6ba-4a06-8d6b-86d8128026f7
ms.openlocfilehash: 6ee03b546cf89aff3ef79fa9c89d15f39b4d9fe0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539133"
---
# <a name="platformcollectionsvectorviewiterator-class"></a>Classe Platform::Collections::VectorViewIterator

Fornece um iterador da biblioteca de modelo padrão para objetos derivados de tempo de execução do Windows`IVectorView` interface.

`ViewVectorIterator` é um iterador proxy que armazena elementos do tipo `VectorProxy<T>`. Entretanto, o objeto proxy quase nunca é visível ao código do usuário. Para obter mais informações, consulte [Coleções (C++/CX)](../cppcx/collections-c-cx.md).

## <a name="syntax"></a>Sintaxe

```
template <typename T>
class VectorViewIterator;
```

#### <a name="parameters"></a>Parâmetros

*T*<br/>
O typename da classe de modelo de VectorViewIterator.

### <a name="members"></a>Membros

### <a name="public-typedefs"></a>Typedefs públicos

|Nome|Descrição|
|----------|-----------------|
|`difference_type`|Uma diferença de ponteiro (ptrdiff_t).|
|`iterator_category`|A categoria de um iterador de acesso aleatório (::std::random_access_iterator_tag).|
|`pointer`|Um ponteiro para um tipo interno que é necessário para a implementação de VectorViewIterator.|
|`reference`|Uma referência para um tipo interno que é necessário para a implementação de VectorViewIterator.|
|`value_type`|O typename `T` .|

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[VectorViewIterator::VectorViewIterator](#ctor)|Inicializa uma nova instância da classe VectorViewIterator.|

### <a name="public-operators"></a>Operadores públicos

|Nome|Descrição|
|----------|-----------------|
|[Operador VectorViewIterator::operator-](#operator-minus)|Subtrai um número especificado de elementos do iterador atual, gerando um novo iterador, ou um iterador especificado do iterador atual, gerando o número de elementos entre os iteradores.|
|[Operador VectorViewIterator::operator--](#operator-decrement)|Decrementa o VectorViewIterator atual.|
|[Operador VectorViewIterator::operator!=](#operator-inequality)|Indica se o VectorViewIterator atual não é igual a um VectorViewIterator especificado.|
|[Operador VectorViewIterator::operator*](#operator-dereference)|Recupera uma referência ao elemento especificado pelo VectorViewIterator atual.|
|[VectorViewIterator::operator\[\]](#operator-at)|Recupera uma referência ao elemento que é um deslocamento especificado de VectorViewIterator atual.|
|[Operador VectorViewIterator::operator+](#operator-plus)|Retorna um VectorViewIterator que referencia o elemento no deslocamento especificado do VectorViewIterator especificado.|
|[Operador VectorViewIterator::operator++](#operator-increment)|Incrementa o VectorViewIterator atual.|
|[Operador VectorViewIterator::operator+=](#operator-plus-assign)|Incrementa o VectorViewIterator atual pelo deslocamento especificado.|
|[Operador VectorViewIterator::operator<](#operator-less-than)|Indica se o VectorViewIterator atual é menor que um VectorViewIterator especificado.|
|[Operador vectorviewiterator::\<Operator =](#operator-less-than-or-equals)|Indica se o VectorViewIterator atual é menor ou igual a um VectorViewIterator especificado.|
|[VectorViewIterator::operator-= Operator](#operator-minus-assign)|Decrementa o VectorViewIterator atual pelo deslocamento especificado.|
|[Operador VectorViewIterator::operator==](#operator-equality)|Indica se o VectorViewIterator atual é igual a um VectorViewIterator especificado.|
|[Operador VectorViewIterator::operator>](#operator-greater-than)|Indica se o VectorViewIterator atual é maior que um VectorViewIterator especificado.|
|[Operador VectorViewIterator::operator->](#operator-arrow)|Recupera o endereço do elemento referenciado pelo VectorViewIterator atual.|
|[Operador VectorViewIterator::operator>=](#operator-greater-than-or-equals)|Indica se o VectorViewIterator atual é maior ou igual a um VectorViewIterator especificado.|

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`VectorViewIterator`

### <a name="requirements"></a>Requisitos

**Cabeçalho:** collection.h

**Namespace:** Platform::Collections

## <a name="operator-arrow"></a>  Operador vectorviewiterator:: -&gt; operador

Recupera o endereço do elemento referenciado pelo VectorViewIterator atual.

### <a name="syntax"></a>Sintaxe

```
Detail::ArrowProxy<T> operator->() const;
```

### <a name="return-value"></a>Valor de retorno

O valor do elemento que é referenciado pelo VectorViewIterator atual.

O tipo do valor retornado é um tipo interno não especificado que é necessário para a implementação desse operador.

## <a name="operator-decrement"></a>  Operador vectorviewiterator:: – operador

Decrementa o VectorViewIterator atual.

### <a name="syntax"></a>Sintaxe

```
VectorViewIterator& operator--();
VectorViewIterator operator--(int);
```

### <a name="return-value"></a>Valor de retorno

A primeira sintaxe diminui e, em seguida, retorna o VectorViewIterator atual. A segunda sintaxe retorna uma cópia do VectorViewIterator atual e, em seguida, diminui o VectorViewIterator atual.

### <a name="remarks"></a>Comentários

A primeira sintaxe de VectorViewIterator pré-diminui o VectorViewIterator atual.

A segunda sintaxe pós-diminui o VectorViewIterator atual. O tipo `int` na segunda sintaxe indica uma operação de pós-diminuição, não um operando de inteiro real.

## <a name="operator-dereference"></a>  Operador vectorviewiterator::\* operador

Recupera uma referência ao elemento especificado pelo VectorViewIterator atual.

### <a name="syntax"></a>Sintaxe

```
reference operator*() const;
```

### <a name="return-value"></a>Valor de retorno

O elemento especificado pelo VectorViewIterator atual.

## <a name="operator-equality"></a>  Operador vectorviewiterator:: Operator = =

Indica se o VectorViewIterator atual é igual a um VectorViewIterator especificado.

### <a name="syntax"></a>Sintaxe

```
bool operator==(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parâmetros

*other*<br/>
Outro VectorViewIterator.

### <a name="return-value"></a>Valor de retorno

**Verdadeiro** se o atual `VectorViewIterator` é igual a *outras*; caso contrário, **false**.

## <a name="operator-greater-than"></a>  Operador vectorviewiterator::&gt; operador

Indica se o VectorViewIterator atual é maior que um VectorViewIterator especificado.

### <a name="syntax"></a>Sintaxe

```

bool operator>(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parâmetros

*other*<br/>
Outro VectorViewIterator.

### <a name="return-value"></a>Valor de retorno

**Verdadeiro** se o VectorViewIterator atual for maior que *outras*; caso contrário, **false**.

## <a name="operator-greater-than-or-equals"></a>  Operador vectorviewiterator::&gt;Operator =

Indica se o atual `VectorViewIterator` é maior que ou igual ao especificado `VectorViewIterator`.

### <a name="syntax"></a>Sintaxe

```

bool operator>=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parâmetros

*other*<br/>
Outro VectorViewIterator.

### <a name="return-value"></a>Valor de retorno

**Verdadeiro** se atual `VectorViewIterator` é maior que ou igual a *outras*; caso contrário, **false**.

## <a name="operator-increment"></a>  Operador vectorviewiterator:: + + operador

Incrementa o VectorViewIterator atual.

### <a name="syntax"></a>Sintaxe

```

VectorViewIterator& operator++();
VectorViewIterator operator++(int);
```

### <a name="return-value"></a>Valor de retorno

A primeira sintaxe incrementa e, em seguida, retorna o VectorViewIterator atual. A segunda sintaxe retorna uma cópia de VectorViewIterator atual e, em seguida, incrementa o VectorViewIterator atual.

### <a name="remarks"></a>Comentários

A primeira sintaxe de VectorViewIterator pré-incrementa o VectorViewIterator atual.

A segunda sintaxe pós-incrementa o VectorViewIterator atual. O tipo `int` na segunda sintaxe indica uma operação de pós-incremento, não um operando de inteiro real.

## <a name="operator-inequality"></a>  Operador vectorviewiterator::! = operador

Indica se o VectorViewIterator atual não é igual a um VectorViewIterator especificado.

### <a name="syntax"></a>Sintaxe

```
bool operator!=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parâmetros

*other*<br/>
Outro VectorViewIterator.

### <a name="return-value"></a>Valor de retorno

**Verdadeiro** se o atual `VectorViewIterator` não é igual a *outras*; caso contrário, **false**.

## <a name="operator-less-than"></a>  Operador vectorviewiterator::&lt; operador

Indica se o VectorIterator atual é menor que um VectorIterator especificado.

### <a name="syntax"></a>Sintaxe

```
bool operator<(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parâmetros

*other*<br/>
Outro `VectorIterator`.

### <a name="return-value"></a>Valor de retorno

**Verdadeiro** se o atual `VectorIterator` é menor que *outras*; caso contrário, **false**.

## <a name="operator-less-than-or-equals"></a>  Operador vectorviewiterator::&lt;Operator =

Indica se o atual `VectorIterator` é menor que ou igual a um especificado `VectorIterator`.

### <a name="syntax"></a>Sintaxe

```

bool operator<=(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parâmetros

*other*<br/>
Outro `VectorIterator`.

### <a name="return-value"></a>Valor de retorno

**Verdadeiro** se o atual `VectorIterator` é menor que ou igual a *outras*; caso contrário, **false**.

## <a name="operator-minus"></a>  Operador vectorviewiterator:: Operator-

Subtrai um número especificado de elementos do iterador atual, gerando um novo iterador, ou um iterador especificado do iterador atual, gerando o número de elementos entre os iteradores.

### <a name="syntax"></a>Sintaxe

```

VectorViewIterator operator-(difference_type n) const;

difference_type operator-(const VectorViewIterator& other) const;
```

### <a name="parameters"></a>Parâmetros

*n*<br/>
Um número de elementos.

*other*<br/>
Outro VectorViewIterator.

### <a name="return-value"></a>Valor de retorno

A primeira sintaxe do operador retorna um objeto VectorViewIterator que corresponde a `n` elementos menos o VectorViewIterator atual. A segunda sintaxe do operador retorna o número de elementos entre o VectorViewIterator atual e `other`.

## <a name="operator-plus-equals"></a>  Operador vectorviewiterator:: + = operador

Incrementa o VectorViewIterator atual pelo deslocamento especificado.

### <a name="syntax"></a>Sintaxe

```
VectorViewIterator& operator+=(difference_type n);
```

### <a name="parameters"></a>Parâmetros

*n*<br/>
Um deslocamento de inteiro.

### <a name="return-value"></a>Valor de retorno

O VectorViewIterator atualizado.

## <a name="operator-plus"></a>  Operador vectorviewiterator:: + operador

Retorna um VectorViewIterator que referencia o elemento no deslocamento especificado do VectorViewIterator especificado.

### <a name="syntax"></a>Sintaxe

```

VectorViewIterator operator+(difference_type n) const;

template <typename T>
inline VectorViewIterator<T> operator+
   (ptrdiff_t n,
   const VectorViewIterator<T>& i);
```

### <a name="parameters"></a>Parâmetros

*T*<br/>
Na segunda sintaxe, o typename de VectorViewIterator.

*n*<br/>
Um deslocamento de inteiro.

*i*<br/>
Na segunda sintaxe, um VectorViewIterator.

### <a name="return-value"></a>Valor de retorno

Na primeira sintaxe, um VectorViewIterator que referencia o elemento no deslocamento especificado do VectorViewIterator atual.

Na segunda sintaxe, um VectorViewIterator que referencia o elemento no deslocamento especificado do início do parâmetro `i`.

## <a name="operator-minus-assign"></a>  Operador-= operador vectorviewiterator::

Decrementa o VectorIterator atual pelo deslocamento especificado.

### <a name="syntax"></a>Sintaxe

```
VectorViewIterator& operator-=(difference_type n);
```

### <a name="parameters"></a>Parâmetros

*n*<br/>
Um deslocamento de inteiro.

### <a name="return-value"></a>Valor de retorno

O VectorIterator atualizado.

## <a name="operator-at"></a>  VectorViewIterator::operator\[\]

Recupera uma referência ao elemento que é um deslocamento especificado de VectorViewIterator atual.

### <a name="syntax"></a>Sintaxe

```
reference operator[](difference_type n) const;
```

### <a name="parameters"></a>Parâmetros

*n*<br/>
Um deslocamento de inteiro.

### <a name="return-value"></a>Valor de retorno

O elemento que é deslocado pelos elementos `n` de VectorViewIterator atual.

## <a name="ctor"></a>  Construtor vectorviewiterator:: Vectorviewiterator

Inicializa uma nova instância da classe VectorViewIterator.

### <a name="syntax"></a>Sintaxe

```

VectorViewIterator();

explicit VectorViewIterator(
   Windows::Foundation::Collections::IVectorView<T>^ v
);
```

### <a name="parameters"></a>Parâmetros

*v*<br/>
Um IVectorView\<T > objeto.

### <a name="remarks"></a>Comentários

O primeiro exemplo de sintaxe é o construtor padrão. O segundo exemplo de sintaxe é um construtor explícito que é usado para construir um VectorViewIterator de um IVectorView\<T > objeto.

## <a name="see-also"></a>Consulte também

[Namespace de plataforma](platform-namespace-c-cx.md)