---
title: Classe CArrayRowset
ms.date: 11/04/2016
f1_keywords:
- ATL.CArrayRowset<TAccessor>
- ATL.CArrayRowset
- CArrayRowset
- ATL::CArrayRowset
- ATL::CArrayRowset<TAccessor>
- ATL::CArrayRowset::CArrayRowset
- CArrayRowset.CArrayRowset
- ATL.CArrayRowset.CArrayRowset
- ATL.CArrayRowset<TAccessor>.CArrayRowset
- CArrayRowset::CArrayRowset
- CArrayRowset
- CArrayRowset<TAccessor>::CArrayRowset
- ATL::CArrayRowset<TAccessor>::CArrayRowset
- CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset::Snapshot
- Snapshot
- CArrayRowset<TAccessor>::Snapshot
- ATL.CArrayRowset.Snapshot
- ATL.CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset<TAccessor>::Snapshot
- CArrayRowset::Snapshot
- CArrayRowset.Snapshot
- CArrayRowset::operator[]
- CArrayRowset.operator[]
- ATL::CArrayRowset::m_nRowsRead
- ATL::CArrayRowset<TAccessor>::m_nRowsRead
- CArrayRowset<TAccessor>::m_nRowsRead
- ATL.CArrayRowset<TAccessor>.m_nRowsRead
- CArrayRowset.m_nRowsRead
- m_nRowsRead
- ATL.CArrayRowset.m_nRowsRead
- CArrayRowset::m_nRowsRead
helpviewer_keywords:
- CArrayRowset class
- CArrayRowset class, constructor
- Snapshot method
- operator [], arrays
- '[] operator'
- operator[], arrays
- m_nRowsRead
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
ms.openlocfilehash: 39e1a6add012097fad72e05a57cc76df72e83cc8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644841"
---
# <a name="carrayrowset-class"></a>Classe CArrayRowset

Elementos de acessos de um conjunto de linhas usando a sintaxe de matriz.

## <a name="syntax"></a>Sintaxe

```cpp
template < class TAccessor >
class CArrayRowset :
   public CVirtualBuffer <TAccessor>, 
   protected CBulkRowset <TAccessor>
```

### <a name="parameters"></a>Parâmetros

*TAccessor*<br/>
O tipo de classe de acessador que você deseja usar o conjunto de linhas.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atldbcli.h

## <a name="members"></a>Membros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CArrayRowset](#carrayrowset)|Construtor.|
|[Instantâneo](#snapshot)|Lê o conjunto de linhas inteiro na memória.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador&#91;&#93;](#operator)|Acessa um elemento do conjunto de linhas.|

### <a name="data-members"></a>Membros de Dados

|||
|-|-|
|[CArrayRowset::m_nRowsRead](#nrowsread)|O número de linhas já lidas.|

## <a name="carrayrowset"></a> Carrayrowset:: Carrayrowset

Cria um novo objeto `CArrayRowset`.

### <a name="syntax"></a>Sintaxe

```cpp
CArrayRowset(int nMax = 100000);
```

#### <a name="parameters"></a>Parâmetros

*Nmáx*<br/>
[in] Número máximo de linhas no conjunto de linhas.

## <a name="snapshot"></a> Carrayrowset:: snapshot

Lê o conjunto de linhas inteiro na memória, criando uma imagem ou um instantâneo dele.

### <a name="syntax"></a>Sintaxe

```cpp
HRESULT Snapshot() throw();
```

## <a name="operator"></a> Carrayrowset:: Operator

Fornece sintaxe de matriz para acessar uma linha no conjunto de linhas.

### <a name="syntax"></a>Sintaxe

```cpp
TAccessor & operator[](int nrow);
```

#### <a name="parameters"></a>Parâmetros

*TAccessor*<br/>
Um parâmetro de modelo que especifica o tipo de acessador armazenado no conjunto de linhas.

*funções nRow*<br/>
[in] Número da linha (elemento de matriz) em que você deseja acessar.

### <a name="return-value"></a>Valor de retorno

O conteúdo da linha solicitada.

### <a name="remarks"></a>Comentários

Se *funções nRow* exceder o número de linhas no conjunto de linhas, uma exceção será lançada.

## <a name="nrowsread"></a> Carrayrowset:: M_nrowsread

Contém o número de linhas no conjunto de linhas que já tiverem sido lidos.

### <a name="syntax"></a>Sintaxe

```cpp
ULONG m_nRowsRead;
```

## <a name="see-also"></a>Consulte também

[Modelos de consumidor do OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referência de modelos de consumidor do OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Classe CRowset](../../data/oledb/crowset-class.md)