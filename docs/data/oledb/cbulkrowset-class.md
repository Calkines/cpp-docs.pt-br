---
title: Classe CBulkRowset
ms.date: 11/04/2016
f1_keywords:
- ATL::CBulkRowset
- ATL.CBulkRowset
- ATL::CBulkRowset<TAccessor>
- CBulkRowset
- ATL.CBulkRowset<TAccessor>
- CBulkRowset::AddRefRows
- AddRefRows
- CBulkRowset.AddRefRows
- ATL.CBulkRowset<TAccessor>.AddRefRows
- ATL::CBulkRowset::AddRefRows
- CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset.AddRefRows
- ATL::CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset<TAccessor>.CBulkRowset
- ATL::CBulkRowset::CBulkRowset
- CBulkRowset.CBulkRowset
- CBulkRowset::CBulkRowset
- ATL.CBulkRowset.CBulkRowset
- ATL::CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset<TAccessor>::CBulkRowset
- CBulkRowset
- ATL.CBulkRowset.MoveFirst
- CBulkRowset<TAccessor>.MoveFirst
- ATL.CBulkRowset<TAccessor>.MoveFirst
- ATL::CBulkRowset::MoveFirst
- ATL::CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset::MoveFirst
- CBulkRowset<TAccessor>::MoveFirst
- CBulkRowset.MoveFirst
- CBulkRowset.MoveLast
- ATL.CBulkRowset.MoveLast
- ATL::CBulkRowset<TAccessor>::MoveLast
- CBulkRowset::MoveLast
- CBulkRowset<TAccessor>.MoveLast
- ATL::CBulkRowset::MoveLast
- ATL.CBulkRowset<TAccessor>.MoveLast
- CBulkRowset<TAccessor>::MoveLast
- MoveLast
- ATL.CBulkRowset<TAccessor>.MoveNext
- ATL::CBulkRowset::MoveNext
- CBulkRowset::MoveNext
- ATL.CBulkRowset.MoveNext
- CBulkRowset.MoveNext
- ATL::CBulkRowset<TAccessor>::MoveNext
- CBulkRowset<TAccessor>.MoveNext
- CBulkRowset<TAccessor>::MoveNext
- CBulkRowset::MovePrev
- MovePrev
- CBulkRowset<TAccessor>::MovePrev
- ATL::CBulkRowset<TAccessor>::MovePrev
- CBulkRowset<TAccessor>.MovePrev
- ATL::CBulkRowset::MovePrev
- CBulkRowset.MovePrev
- ATL.CBulkRowset.MovePrev
- ATL.CBulkRowset<TAccessor>.MovePrev
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
- ReleaseRows
- ATL.CBulkRowset<TAccessor>.ReleaseRows
- ATL::CBulkRowset<TAccessor>::ReleaseRows
- ATL.CBulkRowset.ReleaseRows
- CBulkRowset<TAccessor>::ReleaseRows
- ATL::CBulkRowset::ReleaseRows
- CBulkRowset::ReleaseRows
- CBulkRowset.ReleaseRows
- ATL.CBulkRowset.SetRows
- CBulkRowset::SetRows
- CBulkRowset<TAccessor>.SetRows
- ATL.CBulkRowset<TAccessor>.SetRows
- CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset<TAccessor>::SetRows
- ATL::CBulkRowset::SetRows
- CBulkRowset.SetRows
- SetRows
helpviewer_keywords:
- CBulkRowset class
- AddRefRows method
- CBulkRowset class, constructor
- MoveFirst method
- MoveLast method
- MoveNext method
- MovePrev method
- MoveToBookmark method
- MoveToRatio method
- ReleaseRows method
- SetRows method
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
ms.openlocfilehash: ba6b41a708cd854e398cbaa80609472ebbe167e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176463"
---
# <a name="cbulkrowset-class"></a>Classe CBulkRowset

Busca e manipula as linhas para trabalhar em dados em massa recuperando vários identificadores de linha com uma única chamada.

## <a name="syntax"></a>Sintaxe

```cpp
template <class TAccessor>
class CBulkRowset : public CRowset<TAccessor>
```

### <a name="parameters"></a>Parâmetros

*TAccessor*<br/>
Uma classe de acessador.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atldbcli.h

## <a name="members"></a>Membros

### <a name="methods"></a>Métodos

|||
|-|-|
|[AddRefRows](#addrefrows)|Incrementa a contagem de referência.|
|[CBulkRowset](#cbulkrowset)|Construtor.|
|[MoveFirst](#movefirst)|Recupera a primeira linha de dados, executar uma busca em massa novo se necessário.|
|[MoveLast](#movelast)|Move para a última linha.|
|[MoveNext](#movenext)|Recupera a próxima linha de dados.|
|[MovePrev](#moveprev)|Move para a linha anterior.|
|[MoveToBookmark](#movetobookmark)|Busca a linha marcada por um indicador ou a linha em um deslocamento especificado desse indicador.|
|[MoveToRatio](#movetoratio)|Busca linhas a partir de uma posição fracionária no conjunto de linhas.|
|[ReleaseRows](#releaserows)|Define a linha atual (`m_nCurrentRow`) para zero e libera todas as linhas.|
|[SetRows](#setrows)|Define o número de identificadores de linha a ser recuperado por uma chamada.|

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra o uso da `CBulkRowset` classe.

[!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/cpp/cbulkrowset-class_1.cpp)]

## <a name="addrefrows"></a> CBulkRowset::AddRefRows

Chamadas [IRowset::AddRefRows](/previous-versions/windows/desktop/ms719619(v=vs.85)) para incrementar a contagem de referência para todas as linhas recuperadas no momento do conjunto de linhas em massa.

### <a name="syntax"></a>Sintaxe

```cpp
HRESULT AddRefRows() throw();
```

### <a name="return-value"></a>Valor de retorno

Um HRESULT padrão.

## <a name="cbulkrowset"></a> CBulkRowset::CBulkRowset

Cria um novo `CBulkRowset` do objeto e define a contagem de linha padrão para 10.

### <a name="syntax"></a>Sintaxe

```cpp
CBulkRowset();
```

## <a name="movefirst"></a> CBulkRowset::MoveFirst

Recupera a primeira linha de dados.

### <a name="syntax"></a>Sintaxe

```cpp
HRESULT MoveFirst() throw();
```

### <a name="return-value"></a>Valor de retorno

Um HRESULT padrão.

## <a name="movelast"></a> CBulkRowset::MoveLast

Move para a última linha.

### <a name="syntax"></a>Sintaxe

```cpp
HRESULT MoveLast() throw();
```

### <a name="return-value"></a>Valor de retorno

Um HRESULT padrão.

## <a name="movenext"></a> CBulkRowset::MoveNext

Recupera a próxima linha de dados.

### <a name="syntax"></a>Sintaxe

```cpp
HRESULT MoveNext() throw();
```

### <a name="return-value"></a>Valor de retorno

Um HRESULT padrão. Quando o final do conjunto de linhas foi atingido, retorna DB_S_ENDOFROWSET.

## <a name="moveprev"></a> CBulkRowset::MovePrev

Move para a linha anterior.

### <a name="syntax"></a>Sintaxe

```cpp
HRESULT MovePrev() throw();
```

### <a name="return-value"></a>Valor de retorno

Um HRESULT padrão.

## <a name="movetobookmark"></a> CBulkRowset::MoveToBookmark

Busca a linha marcada por um indicador ou a linha em um deslocamento especificado (*lSkip*) desse indicador.

### <a name="syntax"></a>Sintaxe

```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,
   DBCOUNTITEM lSkip = 0) throw();
```

#### <a name="parameters"></a>Parâmetros

*bookmark*<br/>
[in] Um indicador que marca o local do qual você deseja buscar dados.

*lSkip*<br/>
[in] A contagem do número de linhas de indicador para a linha de destino. Se *lSkip* for zero, a primeira linha buscada é a linha indicada. Se *lSkip* é 1, a primeira linha buscada é a linha após a linha indicada. Se *lSkip* é -1, a primeira linha buscada é a linha antes da linha indicada.

### <a name="return-value"></a>Valor de retorno

Ver [IRowset:: GetData](/previous-versions/windows/desktop/ms716988(v=vs.85)) na *referência do programador do OLE DB*.

## <a name="movetoratio"></a> CBulkRowset::MoveToRatio

Busca linhas a partir de uma posição fracionária no conjunto de linhas.

### <a name="syntax"></a>Sintaxe

```cpp
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,
   DBCOUNTITEM nDenominator)throw();
```

#### <a name="parameters"></a>Parâmetros

*nNumerator*<br/>
[in] O numerador usado para determinar a posição fracionária das quais buscar dados.

*nDenominator*<br/>
[in] O denominador usado para determinar a posição fracionária das quais buscar dados.

### <a name="return-value"></a>Valor de retorno

Um HRESULT padrão.

### <a name="remarks"></a>Comentários

`MoveToRatio` busque as linhas mais ou menos, de acordo com a seguinte fórmula:

`(nNumerator *  RowsetSize ) / nDenominator`

Onde `RowsetSize` é o tamanho do conjunto de linhas, medido em linhas. A precisão dessa fórmula depende do provedor específico. Para obter detalhes, consulte [irowsetscroll:: Getrowsatratio](/previous-versions/windows/desktop/ms709602(v=vs.85)) na *referência do programador DB OLE*.

## <a name="releaserows"></a> CBulkRowset::ReleaseRows

Chamadas [IRowset:: Releaserows](/previous-versions/windows/desktop/ms719771(v=vs.85)) para diminuir a contagem de referência para todas as linhas recuperadas no momento do conjunto de linhas em massa.

### <a name="syntax"></a>Sintaxe

```cpp
HRESULT ReleaseRows() throw();
```

### <a name="return-value"></a>Valor de retorno

Um HRESULT padrão.

## <a name="setrows"></a> CBulkRowset::SetRows

Define o número de identificadores de linha recuperados por cada chamada.

### <a name="syntax"></a>Sintaxe

```cpp
void SetRows(DBROWCOUNT nRows) throw();
```

#### <a name="parameters"></a>Parâmetros

*nRows*<br/>
[in] O novo tamanho do conjunto de linhas (número de linhas).

### <a name="remarks"></a>Comentários

Se você chamar essa função, ele deve ser antes que o conjunto de linhas é aberto.

## <a name="see-also"></a>Consulte também

[Modelos de consumidor do OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referência de modelos de consumidor do OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)