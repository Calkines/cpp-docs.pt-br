---
title: 'Conjunto de registros: indicadores e posições absolutas (ODBC)'
ms.date: 11/04/2016
f1_keywords:
- SetAbsolutePosition
helpviewer_keywords:
- CDBVariant class, bookmarks
- absolute positions, ODBC recordsets
- bookmarks, CDBVariant
- bookmarks, ODBC recordsets
- ODBC recordsets, absolute positions
- ODBC recordsets, bookmarks
- cursors [ODBC], absolute position in recordsets
- recordsets, bookmarks
- bookmarks
- SetAbsolutePosition method
- recordsets, absolute positions
- positioning records
- SetBookmark method
- record positioning
- GetBookmark method
- SetAbsolutePosition method, bookmarks
ms.assetid: 189788d6-33c1-41c5-9265-97db2a5d43cc
ms.openlocfilehash: 826c1c0124eb261c97fff8f1e2fa01c8becb073a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500926"
---
# <a name="recordset-bookmarks-and-absolute-positions-odbc"></a>Conjunto de registros: indicadores e posições absolutas (ODBC)

Este tópico se aplica às classes ODBC do MFC.

Ao navegar por meio de um conjunto de registros, muitas vezes você precisa de uma maneira de retornar a um determinado registro. Indicador e a posição absoluta de um registro fornecem dois métodos.

Este tópico explica:

- [Como usar indicadores](#_core_bookmarks_in_mfc_odbc).

- [Como definir o registro atual usando as posições absolutas](#_core_absolute_positions_in_mfc_odbc).

##  <a name="_core_bookmarks_in_mfc_odbc"></a> Indicadores no ODBC do MFC

Um indicador identifica exclusivamente um registro. Quando você navega por meio de um conjunto de registros, você não pode sempre contar a posição absoluta de um registro porque os registros podem ser excluídos do conjunto de registros. O modo seguro para controlar a posição de um registro é usar seu indicador. Classe `CRecordset` fornece funções de membro para:

- Obtendo o indicador do registro atual, portanto, você pode salvá-lo em uma variável ([GetBookmark](../../mfc/reference/crecordset-class.md#getbookmark)).

- Mover rapidamente para um determinado registro especificando seu indicador, o que você salvou anteriormente em uma variável ([SetBookmark](../../mfc/reference/crecordset-class.md#setbookmark)).

O exemplo a seguir ilustra como usar essas funções de membro para marcar o registro atual e retornar posteriormente a ele:

```cpp
// rs is a CRecordset or
// CRecordset-derived object

CDBVariant varRecordToReturnTo;
rs.GetBookmark( varRecordToReturnTo );

// More code in which you
// move to other records

rs.SetBookmark( varRecordToReturnTo );
```

Você não precisa extrair o tipo de dados subjacente dos [classe CDBVariant](../../mfc/reference/cdbvariant-class.md) objeto. Atribua o valor com `GetBookmark` e retornar para esse indicador com `SetBookmark`.

> [!NOTE]
>  Dependendo do driver ODBC e o tipo de conjunto de registros, os indicadores podem não ter suporte. Você pode determinar facilmente se os indicadores são compatíveis com chamando [CRecordset::CanBookmark](../../mfc/reference/crecordset-class.md#canbookmark). Além disso, se houver suporte para indicadores, é necessário escolher explicitamente para implementá-los, especificando o `CRecordset::useBookmarks` opção a [{1&gt;crecordset::Open&lt;1](../../mfc/reference/crecordset-class.md#open) função de membro. Você também deve verificar a persistência de indicadores depois de determinadas operações de conjunto de registros. Por exemplo, se você `Requery` um conjunto de registros, indicadores talvez não sejam mais válidos. Chame [CDatabase::GetBookmarkPersistence](../../mfc/reference/cdatabase-class.md#getbookmarkpersistence) para verificar se você pode chamar com segurança `SetBookmark`.

##  <a name="_core_absolute_positions_in_mfc_odbc"></a> Posições absolutas em MFC ODBC

Além de indicadores, classe `CRecordset` permite que você defina o registro atual, especificando uma posição ordinal. Isso é chamado de posicionamento absoluto.

> [!NOTE]
>  O posicionamento absoluto não está disponível em conjuntos de registros somente de encaminhamento. Para obter mais informações sobre conjuntos de registros somente encaminhamento, consulte [conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md).

Para mover o ponteiro de registro atual usando a posição absoluta, chame [CRecordset::SetAbsolutePosition](../../mfc/reference/crecordset-class.md#setabsoluteposition). Quando você passa um valor para `SetAbsolutePosition`, o registro correspondente a posição ordinal torna-se o registro atual.

> [!NOTE]
>  A posição absoluta de um registro é potencialmente não confiável. Se o usuário exclui registros do conjunto de registros, altera a posição ordinal de qualquer registro subsequente. Os indicadores são o método recomendado para mover o registro atual. Para obter mais informações, consulte [indicadores em MFC ODBC](#_core_bookmarks_in_mfc_odbc).

Para obter mais informações sobre navegação de conjunto de registros, consulte [conjunto de registros: rolando (ODBC)](../../data/odbc/recordset-scrolling-odbc.md).

## <a name="see-also"></a>Consulte também

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)