---
title: Classe max_variable_size
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::max_variable_size
- allocators/stdext::max_variable_size::allocated
- allocators/stdext::max_variable_size::deallocated
- allocators/stdext::max_variable_size::full
- allocators/stdext::max_variable_size::released
- allocators/stdext::max_variable_size::saved
helpviewer_keywords:
- stdext::max_variable_size
- stdext::max_variable_size [C++], allocated
- stdext::max_variable_size [C++], deallocated
- stdext::max_variable_size [C++], full
- stdext::max_variable_size [C++], released
- stdext::max_variable_size [C++], saved
ms.assetid: 9f2e9df0-4148-4b37-bc30-f8eca0ef86ae
ms.openlocfilehash: f8b3c61676f784bf9369c22b5db97d7b251f7ac6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447288"
---
# <a name="maxvariablesize-class"></a>Classe max_variable_size

Descreve um objeto da [classe max](../standard-library/allocators-header.md) que limita um objeto [freelist](../standard-library/freelist-class.md) a um comprimento máximo aproximadamente proporcional ao número de blocos de memória alocados.

## <a name="syntax"></a>Sintaxe

```cpp
class max_variable_size
```

### <a name="constructors"></a>Construtores

|Construtor|Descrição|
|-|-|
|[max_variable_size](#max_variable_size)|Constrói um objeto do tipo `max_variable_size`.|

### <a name="member-functions"></a>Funções de membro

|Função de membro|Descrição|
|-|-|
|[allocated](#allocated)|Aumenta a contagem de blocos de memória alocada.|
|[deallocated](#deallocated)|Diminui a contagem de blocos de memória alocada.|
|[full](#full)|Retorna um valor que especifica se mais blocos de memória devem ser adicionados à lista livre.|
|[released](#released)|Diminui a contagem de blocos de memória na lista livre.|
|[saved](#saved)|Aumenta a contagem de blocos de memória na lista livre.|

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<allocators>

**Namespace:** stdext

## <a name="allocated"></a>  max_variable_size::allocated

Aumenta a contagem de blocos de memória alocada.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|
|---------------|-----------------|
|*_Nx*|O valor do incremento.|

### <a name="remarks"></a>Comentários

Essa função de membro adiciona *_Nx* ao valor `_Nallocs`armazenado. Essa função `cache_freelist::allocate` de membro é chamada após cada chamada bem-sucedida do operador to para **New**. O argumento *_Nx* é o número de blocos de memória na parte alocada pelo operador **New**.

## <a name="deallocated"></a>  max_variable_size::deallocated

Diminui a contagem de blocos de memória alocada.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|
|---------------|-----------------|
|*_Nx*|O valor do incremento.|

### <a name="remarks"></a>Comentários

A função membro subtrai *_Nx* do valor `_Nallocs`armazenado. Essa função `cache_freelist::deallocate` de membro é chamada depois de cada chamada de to Operator **delete**. O argumento *_Nx* é o número de blocos de memória na parte desalocada pelo operador **delete**.

## <a name="full"></a>  max_variable_size::full

Retorna um valor que especifica se mais blocos de memória devem ser adicionados à lista livre.

```cpp
bool full();
```

### <a name="return-value"></a>Valor de retorno

**verdadeiro** se `_Nallocs / 16 + 16 <= _Nblocks`.

### <a name="remarks"></a>Comentários

Essa função membro é chamada por `cache_freelist::deallocate`. Se a chamada retornar **true**, `deallocate` colocará o bloco de memória na lista livre; se ele retornar false `deallocate` , chamará o operador **delete** para desalocar o bloco.

## <a name="max_variable_size"></a>  max_variable_size::max_variable_size

Constrói um objeto do tipo `max_variable_size`.

```cpp
max_variable_size();
```

### <a name="remarks"></a>Comentários

O construtor inicializa os valores armazenados `_Nblocks` e `_Nallocs` como zero.

## <a name="released"></a>  max_variable_size::released

Diminui a contagem de blocos de memória na lista livre.

```cpp
void released();
```

### <a name="remarks"></a>Comentários

Essa função membro diminui a o valor armazenado `_Nblocks`. A função membro `released` da classe max é chamada por `cache_freelist::allocate` sempre que ele remove um bloco de memória da lista livre.

## <a name="saved"></a>  max_variable_size::saved

Aumenta a contagem de blocos de memória na lista livre.

```cpp
void saved();
```

### <a name="remarks"></a>Comentários

Essa função membro aumenta a o valor armazenado `_Nblocks`. Essa função membro é chamada pelo `cache_freelist::deallocate` sempre que ele coloca um bloco de memória na lista livre.

## <a name="see-also"></a>Consulte também

[\<allocators>](../standard-library/allocators-header.md)
