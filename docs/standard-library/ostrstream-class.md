---
title: Classe ostrstream
ms.date: 11/04/2016
f1_keywords:
- strstream/std::ostrstream::freeze
- strstream/std::ostrstream::pcount
- strstream/std::ostrstream::rdbuf
- strstream/std::ostrstream::str
helpviewer_keywords:
- std::ostrstream [C++], freeze
- std::ostrstream [C++], pcount
- std::ostrstream [C++], rdbuf
- std::ostrstream [C++], str
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
ms.openlocfilehash: c73ab13d3cb2531ff3d741766bc86f8354a0be9d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458056"
---
# <a name="ostrstream-class"></a>Classe ostrstream

Descreve um objeto que controla a inserção de elementos e objetos codificados em um buffer de fluxo da classe [strstreambuf](../standard-library/strstreambuf-class.md).

## <a name="syntax"></a>Sintaxe

```cpp
class ostrstream : public ostream
```

## <a name="remarks"></a>Comentários

O objeto armazena um objeto da classe `strstreambuf`.

> [!NOTE]
> Essa classe foi preterida. Considere usar [ostringstream](../standard-library/sstream-typedefs.md#ostringstream) ou [wostringstream](../standard-library/sstream-typedefs.md#wostringstream) em vez disso.

### <a name="constructors"></a>Construtores

|Construtor|Descrição|
|-|-|
|[ostrstream](#ostrstream)|Constrói um objeto do tipo `ostrstream`.|

### <a name="member-functions"></a>Funções de membro

|Função de membro|Descrição|
|-|-|
|[freeze](#freeze)|Faz com que um buffer de fluxo esteja indisponível por meio de operações de buffer de fluxo.|
|[pcount](#pcount)|Retorna uma contagem do número de elementos gravados na sequência controlada.|
|[rdbuf](#rdbuf)|Retorna um ponteiro para o objeto `strstreambuf` associado do fluxo.|
|[str](#str)|Chama [freeze](../standard-library/strstreambuf-class.md#freeze) e retorna um ponteiro para o início da sequência controlada.|

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<strstream>

**Namespace:** std

## <a name="freeze"></a>  ostrstream::freeze

Faz com que um buffer de fluxo esteja indisponível por meio de operações de buffer de fluxo.

```cpp
void freeze(bool _Freezeit = true);
```

### <a name="parameters"></a>Parâmetros

*_Freezeit*\
Um **bool** que indica se você deseja que o fluxo seja congelado.

### <a name="remarks"></a>Comentários

A função membro chama [rdbuf](#rdbuf) -> [freeze](../standard-library/strstreambuf-class.md#freeze)(_ *Freezeit*).

### <a name="example"></a>Exemplo

Consulte [strstream:: Freeze](../standard-library/strstreambuf-class.md#freeze) para obter um exemplo que `freeze`usa.

## <a name="ostrstream"></a>  ostrstream::ostrstream

Constrói um objeto do tipo `ostrstream`.

```cpp
ostrstream();

ostrstream(char* ptr,
    streamsize count,
    ios_base::openmode _Mode = ios_base::out);
```

### <a name="parameters"></a>Parâmetros

*PTR*\
O buffer.

*contar*\
O tamanho do buffer em bytes.

*_Mode*\
O modo de entrada e saída do buffer. Consulte [ios_base::openmode](../standard-library/ios-base-class.md#openmode) para obter mais informações.

### <a name="remarks"></a>Comentários

Ambos os construtores inicializam a classe base chamando [ostream](../standard-library/ostream-typedefs.md#ostream)(**SB**), em `sb` que é o objeto armazenado da classe [strstreambuf](../standard-library/strstreambuf-class.md). O primeiro construtor também é `sb` inicializado `strstreambuf`chamando. O segundo construtor inicializa a classe base com uma de duas maneiras:

- Se `_Mode` **ios_base::** `count` `strstreambuf` `count``ptr`App = = 0, devedesignaroprimeiroelementodeumamatrizdeelementoseoconstrutorchama(,,`ptr`  &  `ptr`).

- Caso contrário `ptr` , deve designar o primeiro elemento de uma matriz de elementos de contagem que contém uma cadeia de caracteres C cujo primeiro `ptr`elemento é designado por e `strstreambuf`o construtor `count`chama (`ptr`,, `ptr` + `strlen`( `ptr`) ).

## <a name="pcount"></a>  ostrstream::pcount

Retorna uma contagem do número de elementos gravados na sequência controlada.

```cpp
streamsize pcount() const;
```

### <a name="return-value"></a>Valor de retorno

O número de elementos gravados na sequência controlada.

### <a name="remarks"></a>Comentários

A função membro retorna [rdbuf](#rdbuf) -> [pcount](../standard-library/strstreambuf-class.md#pcount).

### <a name="example"></a>Exemplo

Consulte [strstream::pcount](../standard-library/strstreambuf-class.md#pcount) para ver uma amostra que usa `pcount`.

## <a name="rdbuf"></a>  ostrstream::rdbuf

Retorna um ponteiro para o objeto strstreambuf associado ao fluxo.

```cpp
strstreambuf *rdbuf() const
```

### <a name="return-value"></a>Valor de retorno

Um ponteiro para o objeto strstreambuf associado ao fluxo.

### <a name="remarks"></a>Comentários

A função membro retorna o endereço do buffer de fluxo armazenado do tipo `pointer` para [strstreambuf](../standard-library/strstreambuf-class.md).

### <a name="example"></a>Exemplo

Consulte [strstreambuf::pcount](../standard-library/strstreambuf-class.md#pcount) para ver uma amostra que usa `rdbuf`.

## <a name="str"></a>  ostrstream::str

Chama [freeze](../standard-library/strstreambuf-class.md#freeze) e retorna um ponteiro para o início da sequência controlada.

```cpp
char *str();
```

### <a name="return-value"></a>Valor de retorno

Um ponteiro para o início da sequência controlada.

### <a name="remarks"></a>Comentários

A função membro retorna [rdbuf](#rdbuf) -> [str](../standard-library/strstreambuf-class.md#str).

### <a name="example"></a>Exemplo

Consulte [strstream:: Str](../standard-library/strstreambuf-class.md#str) para obter um exemplo que `str`usa.

## <a name="see-also"></a>Consulte também

[ostream](../standard-library/ostream-typedefs.md#ostream)\
[Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programação de iostream](../standard-library/iostream-programming.md)\
[Convenções de iostreams](../standard-library/iostreams-conventions.md)
