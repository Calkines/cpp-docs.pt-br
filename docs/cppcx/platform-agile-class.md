---
title: Classe Platform::Agile
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
helpviewer_keywords:
- Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
ms.openlocfilehash: 86a535bc106e17b276dc5f42a59773aa0de8c361
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161648"
---
# <a name="platformagile-class"></a>Classe Platform::Agile

Representa um objeto que tem um MashalingBehavior=Standard como um objeto Agile, que reduz a possibilidade de exceções de threading do tempo de execução. O `Agile<T>` permite que o objeto não Agile chame ou seja chamado do mesmo thread ou de um thread diferente. Para obter mais informações, consulte [Threading e Marshaling](../cppcx/threading-and-marshaling-c-cx.md).

## <a name="syntax"></a>Sintaxe

```cpp
template <typename T>
class Agile;
```

#### <a name="parameters"></a>Parâmetros

*T*<br/>
O typename para a classe não Agile.

### <a name="remarks"></a>Comentários

A maioria das classes no tempo de execução do Windows são ágeis. Um objeto Agile pode chamar ou ser chamado por um objeto em processo ou fora de processo no mesmo thread ou em um thread diferente. Se um objeto não for Agile, encapsule o objeto não Agile em um objeto `Agile<T>` , que seja Agile. Em seguida, pode-se realizar marshaling do objeto `Agile<T>` e o objeto não Agile subjacente pode ser usado.

A classe `Agile<T>` é uma classe do C++ nativa e padrão e requer o `agile.h`. Representa o *contexto*do objeto não Agile e do objeto Agile. O contexto especifica um modelo de threading e comportamento de marshaling de um objeto Agile. O sistema operacional usa o contexto para determinar como realizar marshaling de um objeto.

### <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[Agile::Agile](#ctor)|Inicializa uma nova instância da classe Agile.|
|[Destruidor Agile::~Agile](#dtor)|Destrói a instância atual da classe Agile.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[Agile::Get](#get)|Retorna um identificador para o objeto representado pelo objeto Agile atual.|
|[Agile::GetAddressOf](#getaddressof)|Reinicializa o objeto Agile atual e retorna o endereço de um identificador para um objeto do tipo `T`.|
|[Agile::GetAddressOfForInOut](#getaddressofforinout)|Retorna o endereço de um identificador para o objeto representado pelo objeto Agile atual.|
|[Agile::Release](#release)|Descarta o objeto e o contexto subjacentes do objeto Agile atual.|

### <a name="public-operators"></a>Operadores públicos

|Nome|Descrição|
|----------|-----------------|
|[Agile::operator->](#operator-arrow)|Recupera um endereço de um identificador para o objeto representado pelo objeto Agile atual.|
|[Agile::operator=](#operator-assign)|Atribui o objeto especificado ao objeto Agile atual.|

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`Object`

`Agile`

### <a name="requirements"></a>Requisitos

**Cliente com suporte mínimo:** Windows 8

**Servidor com suporte mínimo:** Windows Server 2012

**Namespace:** Plataforma

**Cabeçalho:** agile.h

## <a name="ctor"></a>  Construtor Agile:: Agile

Inicializa uma nova instância da classe Agile.

## <a name="syntax"></a>Sintaxe

```cpp
Agile();
Agile(T^ object);
Agile(const Agile<T>& object);
Agile(Agile<T>&& object);
```

#### <a name="parameters"></a>Parâmetros

*T*<br/>
Um tipo especificado pelo parâmetro typename do modelo.

*object*<br/>
Na segunda versão desse construtor, um objeto usado para inicializar uma nova instância de Agile. Na terceira versão, o objeto que é copiado para a nova instância de Agile. Na quarta versão, o objeto que é movido para a nova instância de Agile.

### <a name="remarks"></a>Comentários

A primeira versão desse construtor é o construtor padrão. A segunda versão inicializa a nova classe da instância de Agile do objeto especificado pelo parâmetro `object`. A terceira versão é o construtor de cópia. A quarta versão é o construtor de movimento. Esse construtor não pode gerar exceções.

## <a name="dtor"></a>  Agile:: ~ Agile destruidor

Destrói a instância atual da classe Agile.

## <a name="syntax"></a>Sintaxe

```cpp
~Agile();
```

### <a name="remarks"></a>Comentários

Este destruidor também libera o objeto representado pelo objeto Agile atual.

## <a name="get"></a>   Método Agile:: Get

Retorna um identificador para o objeto representado pelo objeto Agile atual.

## <a name="syntax"></a>Sintaxe

```cpp
T^ Get() const;
```

### <a name="return-value"></a>Valor de retorno

Um identificador para o objeto representado pelo objeto Agile atual.

O tipo do valor retornado é, de fato, um tipo interno não revelado. Uma maneira conveniente de manter o valor retornado é atribuí-lo a uma variável que é declarada com o **automática** palavra-chave de dedução de tipo. Por exemplo, `auto x = myAgileTvariable->Get();`.

## <a name="getaddressof"></a>  Método Agile:: getaddressof

Reinicializa o objeto Agile atual e retorna o endereço de um identificador para um objeto do tipo `T`.

## <a name="syntax"></a>Sintaxe

```cpp
T^* GetAddressOf() throw();
```

#### <a name="parameters"></a>Parâmetros

*T*<br/>
Um tipo especificado pelo parâmetro typename do modelo.

### <a name="return-value"></a>Valor de retorno

O endereço de um identificador para um objeto do tipo `T`.

### <a name="remarks"></a>Comentários

Esta operação libera a representação atual de um objeto do tipo `T`, se houver; reinicializa membros de dados do objeto Agile; adquire o contexto atual de threading; e retorna o endereço de uma variável de identificador para objeto que pode representar um objeto não Agile. Para fazer com que uma instância da classe Agile representar um objeto, use o operador de atribuição ([Agile:: Operator =](#operator-assign)) para atribuir o objeto para a instância da classe Agile.

## <a name="getaddressofforinout"></a>  Método Agile:: getaddressofforinout

Retorna o endereço de um identificador para o objeto representado pelo objeto Agile atual.

## <a name="syntax"></a>Sintaxe

```cpp
T^* GetAddressOfForInOut()  throw();
```

#### <a name="parameters"></a>Parâmetros

*T*<br/>
Um tipo especificado pelo parâmetro typename do modelo.

### <a name="return-value"></a>Valor de retorno

O endereço de um identificador para o objeto representado pelo objeto Agile atual.

### <a name="remarks"></a>Comentários

Esta operação adquire o contexto de threading atual e retorna o endereço de um identificador para o objeto subjacente.

## <a name="release"></a>  Método Agile:: Release

Descarta o objeto e o contexto subjacentes do objeto Agile atual.

## <a name="syntax"></a>Sintaxe

```cpp
void Release() throw();
```

### <a name="remarks"></a>Comentários

O objeto e o contexto subjacentes do objeto Agile atual serão descartados, caso existam, e o valor do objeto Agile será definido como nulo.

## <a name="operator-arrow"></a>  Agile:: Operator -&gt; operador

Recupera um endereço de um identificador para o objeto representado pelo objeto Agile atual.

## <a name="syntax"></a>Sintaxe

```cpp
T^ operator->() const throw();
```

### <a name="return-value"></a>Valor de retorno

Um identificador para o objeto representado pelo objeto Agile atual.

Esse operador retorna, na verdade, um tipo interno não revelado. Uma maneira conveniente de manter o valor retornado é atribuí-lo a uma variável que é declarada com o **automática** palavra-chave de dedução de tipo.

## <a name="operator-assign"></a>  Agile:: Operator operador =

Atribui o objeto especificado ao objeto Agile atual.

## <a name="syntax"></a>Sintaxe

```cpp
Agile<T> operator=( T^ object ) throw();
Agile<T> operator=( const Agile<T>& object ) throw();
Agile<T> operator=( Agile<T>&& object ) throw();
T^ operator=( IUnknown* lp ) throw();
```

#### <a name="parameters"></a>Parâmetros

*T*<br/>
O tipo especificado pelo typename do modelo.

*object*<br/>
O objeto ou o identificador de um objeto que é copiado ou movido para o objeto Agile atual.

*lp*<br/>
O ponteiro de interface de IUnknown de um objeto.

### <a name="return-value"></a>Valor de retorno

Um identificador para um objeto do tipo `T`

### <a name="remarks"></a>Comentários

A primeira versão do operador de atribuição copia um identificador para um tipo de referência para o objeto Agile atual. A segunda versão copia uma referência a um tipo Agile para o objeto Agile atual. A terceira versão move um tipo Agile para o objeto Agile atual. A quarta versão move um ponteiro para um objeto COM para o objeto Agile atual.

A operação de atribuição persiste automaticamente o contexto do objeto Agile atual.

## <a name="see-also"></a>Consulte também

[Namespace de plataforma](platform-namespace-c-cx.md)
