---
title: Classe cache_chunklist
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
ms.openlocfilehash: 73730e0a4a22e7f5e63809cc2c1603cbda1ab596
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449660"
---
# <a name="cachechunklist-class"></a>Classe cache_chunklist

Define um [alocador de blocos](../standard-library/allocators-header.md) que aloca e desaloca os blocos de memória de um único tamanho.

## <a name="syntax"></a>Sintaxe

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|
|---------------|-----------------|
|*Sz*|O número de elementos na matriz a serem alocados.|

## <a name="remarks"></a>Comentários

Essa classe de modelo usa o **operador New** para alocar partes de memória bruta, Subalocando blocos para alocar armazenamento para um bloco de memória quando necessário; Ele armazena blocos de memória desalocados em uma lista gratuita separada para cada parte e usa o **operador Delete** para desalocar uma parte quando nenhum de seus blocos de memória está em uso.

Cada bloco de memória contém os bytes de *sz* de memória utilizável e um ponteiro para a parte à qual ele pertence. Cada parte contém `Nelts` blocos de memória, três ponteiros, um int e os dados que o **operador New** e o **operador Delete** exigem.

### <a name="constructors"></a>Construtores

|Construtor|Descrição|
|-|-|
|[cache_chunklist](#cache_chunklist)|Constrói um objeto do tipo `cache_chunklist`.|

### <a name="member-functions"></a>Funções de membro

|Função de membro|Descrição|
|-|-|
|[allocate](#allocate)|Aloca um bloco de memória.|
|[deallocate](#deallocate)|Libera um número especificado de objetos do armazenamento começando em uma posição especificada.|

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<allocators>

**Namespace:** stdext

## <a name="allocate"></a>  cache_chunklist::allocate

Aloca um bloco de memória.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|
|---------------|-----------------|
|*count*|O número de elementos na matriz a serem alocados.|

### <a name="return-value"></a>Valor de retorno

Um ponteiro para o objeto alocado.

### <a name="remarks"></a>Comentários

## <a name="cache_chunklist"></a>  cache_chunklist::cache_chunklist

Constrói um objeto do tipo `cache_chunklist`.

```cpp
cache_chunklist();
```

### <a name="remarks"></a>Comentários

## <a name="deallocate"></a>  cache_chunklist::deallocate

Libera um número especificado de objetos do armazenamento começando em uma posição especificada.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|
|---------------|-----------------|
|*ptr*|Um ponteiro para o primeiro objeto a ser desalocado do armazenamento.|
|*count*|O número de objetos a serem desalocados do armazenamento.|

### <a name="remarks"></a>Comentários

## <a name="see-also"></a>Consulte também

[\<allocators>](../standard-library/allocators-header.md)
