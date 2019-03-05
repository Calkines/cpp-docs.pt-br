---
title: Classe CDBVariant
ms.date: 11/04/2016
f1_keywords:
- CDBVariant
- AFXDB/CDBVariant
- AFXDB/CDBVariant::CDBVariant
- AFXDB/CDBVariant::Clear
- AFXDB/CDBVariant::m_dwType
- AFXDB/CDBVariant::m_boolVal
- AFXDB/CDBVariant::m_chVal
- AFXDB/CDBVariant::m_dblVal
- AFXDB/CDBVariant::m_fltVal
- AFXDB/CDBVariant::m_iVal
- AFXDB/CDBVariant::m_lVal
- AFXDB/CDBVariant::m_pbinary
- AFXDB/CDBVariant::m_pdate
- AFXDB/CDBVariant::m_pstring
- AFXDB/CDBVariant::m_pstringA
- AFXDB/CDBVariant::m_pstringW
helpviewer_keywords:
- CDBVariant [MFC], CDBVariant
- CDBVariant [MFC], Clear
- CDBVariant [MFC], m_dwType
- CDBVariant [MFC], m_boolVal
- CDBVariant [MFC], m_chVal
- CDBVariant [MFC], m_dblVal
- CDBVariant [MFC], m_fltVal
- CDBVariant [MFC], m_iVal
- CDBVariant [MFC], m_lVal
- CDBVariant [MFC], m_pbinary
- CDBVariant [MFC], m_pdate
- CDBVariant [MFC], m_pstring
- CDBVariant [MFC], m_pstringA
- CDBVariant [MFC], m_pstringW
ms.assetid: de23609c-c560-4b24-bd6b-9d8903fd5b49
ms.openlocfilehash: 41ea20bcddc53142773d474af41021e9c71af1aa
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289852"
---
# <a name="cdbvariant-class"></a>Classe CDBVariant

Representa um tipo de dados variant para as classes MFC ODBC.

## <a name="syntax"></a>Sintaxe

```
class CDBVariant
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|[CDBVariant::CDBVariant](#cdbvariant)|Constrói um objeto `CDBVariant`.|

### <a name="public-methods"></a>Métodos Públicos

|Nome|Descrição|
|----------|-----------------|
|[CDBVariant::Clear](#clear)|Limpa o `CDBVariant` objeto.|

### <a name="public-data-members"></a>Membros de Dados Públicos

|Nome|Descrição|
|----------|-----------------|
|[CDBVariant::m_dwType](#m_dwtype)|Contém o tipo de dados do valor armazenado no momento. Digite `DWORD` no terminal integrado.|

### <a name="public-union-members"></a>Membros públicos de união

|Nome|Descrição|
|----------|-----------------|
|[CDBVariant::m_boolVal](#m_boolval)|Contém um valor do tipo **BOOL**.|
|[CDBVariant::m_chVal](#m_chval)|Contém um valor do tipo **unsigned char**.|
|[CDBVariant::m_dblVal](#m_dblval)|Contém um valor do tipo **duplas**.|
|[CDBVariant::m_fltVal](#m_fltval)|Contém um valor do tipo **float**.|
|[CDBVariant::m_iVal](#m_ival)|Contém um valor do tipo **curto**.|
|[CDBVariant::m_lVal](#m_lval)|Contém um valor do tipo **longo**.|
|[CDBVariant::m_pbinary](#m_pbinary)|Contém um ponteiro para um objeto do tipo `CLongBinary`.|
|[CDBVariant::m_pdate](#m_pdate)|Contém um ponteiro para um objeto do tipo **TIMESTAMP_STRUCT**.|
|[CDBVariant::m_pstring](#m_pstring)|Contém um ponteiro para um objeto do tipo `CString`.|
|[CDBVariant::m_pstringA](#m_pstringa)|Armazena um ponteiro para um ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.|
|[CDBVariant::m_pstringW](#m_pstringw)|Armazena um ponteiro para uma ampla [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.|

## <a name="remarks"></a>Comentários

`CDBVariant` não tem uma classe base.

`CDBVariant` é semelhante à [COleVariant](../../mfc/reference/colevariant-class.md); no entanto, `CDBVariant` não usa o OLE. `CDBVariant` permite que você armazene um valor sem se preocupar sobre o tipo de dados do valor. `CDBVariant` Controla o tipo de dados do valor atual, que é armazenado em uma união.

Classe [CRecordset](../../mfc/reference/crecordset-class.md) utiliza `CDBVariant` objetos em três funções de membro: `GetFieldValue`, `GetBookmark`, e `SetBookmark`. Por exemplo, `GetFieldValue` permite que você busque dinamicamente os dados em uma coluna. Porque o tipo de dados da coluna não pode ser conhecido no tempo de execução `GetFieldValue` usa um `CDBVariant` objeto para armazenar os dados da coluna.

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`CDBVariant`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxdb. h

##  <a name="cdbvariant"></a>  CDBVariant::CDBVariant

Cria um valor nulo `CDBVariant` objeto.

```
CDBVariant();
```

### <a name="remarks"></a>Comentários

Define o [m_dwType](#m_dwtype) membro de dados para DBVT_NULL.

##  <a name="clear"></a>  CDBVariant::Clear

Chame essa função de membro para limpar o `CDBVariant` objeto.

```
void Clear();
```

### <a name="remarks"></a>Comentários

Se o valor de [m_dwType](#m_dwtype) membro de dados é DBVT_DATE, DBVT_STRING ou DBVT_BINARY, `Clear` libera a memória associada com o membro do ponteiro de união. `Clear` define `m_dwType` para DBVT_NULL.

O `CDBVariant` chamadas de destruidor `Clear`.

##  <a name="m_boolval"></a>  CDBVariant::m_boolVal

Armazena um valor do tipo BOOL.

### <a name="remarks"></a>Comentários

O `m_boolVal` membro de dados pertence a uma união. Antes de acessar `m_boolVal`, verifique primeiro o valor da [CDBVariant::m_dwType](#m_dwtype). Se `m_dwType` é definido como DBVT_BOOL, em seguida, `m_boolVal` conterá um valor válido; caso contrário, acessando `m_boolVal` produzirá resultados não confiáveis.

##  <a name="m_chval"></a>  CDBVariant::m_chVal

Armazena um valor do tipo **unsigned char**.

### <a name="remarks"></a>Comentários

O `m_chVal` membro de dados pertence a uma união. Antes de acessar `m_chVal`, verifique primeiro o valor da [CDBVariant::m_dwType](#m_dwtype). Se `m_dwType` é definido como DBVT_UCHAR, em seguida, `m_chVal` contém um valor válido; caso contrário, acessando `m_chVal` produzirá resultados não confiáveis.

##  <a name="m_dblval"></a>  CDBVariant::m_dblVal

Armazena um valor do tipo **duplas**.

### <a name="remarks"></a>Comentários

O `m_dblVal` membro de dados pertence a uma união. Antes de acessar `m_dblVal`, verifique primeiro o valor da [CDBVariant::m_dwType](#m_dwtype). Se `m_dwType` é definido como DBVT_DOUBLE, em seguida, `m_dblVal` contém um valor válido; caso contrário, acessando `m_dblVal` produzirá resultados não confiáveis.

##  <a name="m_dwtype"></a>  CDBVariant::m_dwType

Este membro de dados contém o tipo de dados para o valor armazenado atualmente no `CDBVariant` membro de união de dados do objeto.

### <a name="remarks"></a>Comentários

Antes de acessar esta união, você deve verificar o valor de `m_dwType` para determinar qual membro de dados de união para acessar. A tabela a seguir lista os possíveis valores para `m_dwType` e o membro de dados de união correspondente.

|m_dwType|Membro de dados de união|
|---------------|-----------------------|
|DBVT_NULL|Nenhum membro de união é válido para o acesso.|
|DBVT_BOOL|[m_boolVal](#m_boolval)|
|DBVT_UCHAR|[m_chVal](#m_chval)|
|DBVT_SHORT|[m_iVal](#m_ival)|
|DBVT_LONG|[m_lVal](#m_lval)|
|DBVT_SINGLE|[m_fltVal](#m_fltval)|
|DBVT_DOUBLE|[m_dblVal](#m_dblval)|
|DBVT_DATE|[m_pdate](#m_pdate)|
|DBVT_STRING|[m_pstring](#m_pstring)|
|DBVT_BINARY|[m_pbinary](#m_pbinary)|
|DBVT_ASTRING|[m_pstringA](#m_pstringa)|
|DBVT_WSTRING|[m_pstringW](#m_pstringw)|

##  <a name="m_fltval"></a>  CDBVariant::m_fltVal

Armazena um valor do tipo **float**.

### <a name="remarks"></a>Comentários

O `m_fltVal` membro de dados pertence a uma união. Antes de acessar `m_fltVal`, verifique primeiro o valor da [CDBVariant::m_dwType](#m_dwtype). Se `m_dwType` é definido como DBVT_SINGLE, em seguida, `m_fltVal` contém um valor válido; caso contrário, acessando `m_fltVal` produzirá resultados não confiáveis.

##  <a name="m_ival"></a>  CDBVariant::m_iVal

Armazena um valor do tipo **curto**.

### <a name="remarks"></a>Comentários

O `m_iVal` membro de dados pertence a uma união. Antes de acessar `m_iVal`, verifique primeiro o valor da [CDBVariant::m_dwType](#m_dwtype). Se `m_dwType` é definido como DBVT_SHORT, em seguida, `m_iVal` contém um valor válido; caso contrário, acessando `m_iVal` produzirá resultados não confiáveis.

##  <a name="m_lval"></a>  CDBVariant::m_lVal

Armazena um valor do tipo **longo**.

### <a name="remarks"></a>Comentários

O `m_lVal` membro de dados pertence a uma união. Antes de acessar `m_lVal`, verifique primeiro o valor da [CDBVariant::m_dwType](#m_dwtype). Se `m_dwType` é definido como DBVT_LONG, em seguida, `m_lVal` contém um valor válido; caso contrário, acessando `m_lVal` produzirá resultados não confiáveis.

##  <a name="m_pbinary"></a>  CDBVariant::m_pbinary

Armazena um ponteiro para um objeto do tipo [CLongBinary](../../mfc/reference/clongbinary-class.md).

### <a name="remarks"></a>Comentários

O `m_pbinary` membro de dados pertence a uma união. Antes de acessar `m_pbinary`, verifique primeiro o valor da [CDBVariant::m_dwType](#m_dwtype). Se `m_dwType` é definido como DBVT_BINARY, em seguida, `m_pbinary` contém um ponteiro válido; caso contrário, acessando `m_pbinary` produzirá resultados não confiáveis.

##  <a name="m_pdate"></a>  CDBVariant::m_pdate

Armazena um ponteiro para um objeto do tipo TIMESTAMP_STRUCT.

### <a name="remarks"></a>Comentários

O `m_pdate` membro de dados pertence a uma união. Antes de acessar `m_pdate`, verifique primeiro o valor da [CDBVariant::m_dwType](#m_dwtype). Se `m_dwType` é definido como DBVT_DATE, em seguida, `m_pdate` contém um ponteiro válido; caso contrário, acessando `m_pdate` produzirá resultados não confiáveis.

Para obter mais informações sobre o tipo de dados TIMESTAMP_STRUCT, consulte o tópico [tipos de dados C](/previous-versions/windows/desktop/ms714556) no Apêndice D do *referência do programador de ODBC* no SDK do Windows.

##  <a name="m_pstring"></a>  CDBVariant::m_pstring

Armazena um ponteiro para um objeto do tipo [CString](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="remarks"></a>Comentários

O `m_pstring` membro de dados pertence a uma união. Antes de acessar `m_pstring`, verifique primeiro o valor da [CDBVariant::m_dwType](#m_dwtype). Se `m_dwType` é definido como DBVT_STRING, em seguida, `m_pstring` contém um ponteiro válido; caso contrário, acessando `m_pstring` produzirá resultados não confiáveis.

##  <a name="m_pstringa"></a>  CDBVariant::m_pstringA

Armazena um ponteiro para um ASCII [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.

### <a name="remarks"></a>Comentários

O `m_pstringA` membro de dados pertence a uma união. Antes de acessar `m_pstringA`, verifique primeiro o valor da [CDBVariant::m_dwType](#m_dwtype). Se `m_dwType` é definido como DBVT_ASTRING, em seguida, `m_pstringA` contém um ponteiro válido; caso contrário, acessando `m_pstringA` produzirá resultados não confiáveis.

##  <a name="m_pstringw"></a>  CDBVariant::m_pstringW

Armazena um ponteiro para uma ampla [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto.

### <a name="remarks"></a>Comentários

O `m_pstringW` membro de dados pertence a uma união. Antes de acessar `m_pstringW`, verifique primeiro o valor da [CDBVariant::m_dwType](#m_dwtype). Se `m_dwType` é definido como DBVT_WSTRING, em seguida, `m_pstringW` contém um ponteiro válido; caso contrário, acessando `m_pstringW` produzirá resultados não confiáveis.

## <a name="see-also"></a>Consulte também

[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classe CRecordset](../../mfc/reference/crecordset-class.md)
