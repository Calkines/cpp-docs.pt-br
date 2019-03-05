---
title: Rotinas de troca dos dados da caixa de diálogo padrão
ms.date: 11/04/2016
helpviewer_keywords:
- standard dialog, data exchange routines
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
ms.openlocfilehash: 05eaa86133bb55cfbf62ec68f81e7ca7d9ab169b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274919"
---
# <a name="standard-dialog-data-exchange-routines"></a>Rotinas de troca dos dados da caixa de diálogo padrão

Este tópico lista as rotinas de exchange (DDX) de dados de caixa de diálogo padrão usadas para controles de caixa de diálogo comuns MFC.

> [!NOTE]
>  Rotinas de troca dos dados de caixa de diálogo padrão são definidas em afxdd_.h de arquivo de cabeçalho. No entanto, os aplicativos devem incluir afxwin. h.

### <a name="ddx-functions"></a>Funções DDX

|||
|-|-|
|[DDX_CBIndex](#ddx_cbindex)|Inicializa ou recupera o índice da seleção atual de um controle de caixa de combinação.|
|[DDX_CBString](#ddx_cbstring)|Inicializa ou recupera o conteúdo atual do campo de edição de um controle de caixa de combinação.|
|[DDX_CBStringExact](#ddx_cbstringexact)|Inicializa ou recupera o conteúdo atual do campo de edição de um controle de caixa de combinação.|
|[DDX_Check](#ddx_check)|Inicializa ou recupera o estado atual de um controle de caixa de seleção.|
|[DDX_Control](#ddx_control)|Subclasses de um determinado controle dentro de uma caixa de diálogo.|
|[DDX_DateTimeCtrl](#ddx_datetimectrl)|Inicializa ou recupera dados de data / hora de um controle de seletor de data e hora.|
|[DDX_IPAddress](#ddx_ipaddress)|Inicializa ou recupera o valor atual de um controle de endereço IP.|
|[DDX_LBIndex](#ddx_lbindex)|Inicializa ou recupera o índice da seleção atual de um controle de caixa de listagem.|
|[DDX_LBString](#ddx_lbstring)|Inicializa ou recupera a seleção atual dentro de um controle de caixa de listagem.|
|[DDX_LBStringExact](#ddx_lbstringexact)|Inicializa ou recupera a seleção atual dentro de um controle de caixa de listagem.|
|[DDX_ManagedControl](#ddx_managedcontrol)|Cria um controle do .NET correspondentes a ID do recurso. do controle|
|[DDX_MonthCalCtrl](#ddx_monthcalctrl)|Inicializa ou recupera o valor atual de um controle de calendário mensal.|
|[DDX_Radio](#ddx_radio)|Inicializa ou recupera o índice baseado em 0 do controle de rádio que já está em um grupo de controle de rádio.|
|[DDX_Scroll](#ddx_scroll)|Inicializa ou recupera a posição atual de controle de posição do controle de rolagem.|
|[DDX_Slider](#ddx_slider)|Inicializa ou recupera a posição atual de controle de posição do controle deslizante.|
|[DDX_Text](#ddx_text)|Inicializa ou recupera o valor atual de um controle de edição.|

##  <a name="ddx_cbindex"></a>  DDX_CBIndex

O `DDX_CBIndex` função gerencia a transferência de **int** dados entre um controle de caixa de combinação em uma caixa de diálogo, exibição ou objeto de exibição de controle de formulário e uma **int** membro de dados de controle, exibição de formulário ou caixa de diálogo objeto de exibição.

```
void AFXAPI DDX_CBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parâmetros

*pDX*<br/>
Um ponteiro para um `CDataExchange` objeto. A estrutura fornece esse objeto para estabelecer o contexto de troca de dados, incluindo sua direção.

*nIDC*<br/>
A ID de recurso de controle de caixa de combinação associado com a propriedade de controle.

*index*<br/>
Uma referência a uma variável de membro do objeto de exibição de controle com o qual os dados são trocados, exibição de formulário ou caixa de diálogo.

### <a name="remarks"></a>Comentários

Quando `DDX_CBIndex` é chamado, *índice* é definido como o índice da seleção atual de caixa de combinação. Se nenhum item for selecionado, *índice* é definido como 0.

Para obter mais informações sobre DDX, consulte [troca de dados de caixa de diálogo e validação](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Cabeçalho** afxdd_.h

##  <a name="ddx_cbstring"></a>  DDX_CBString

O `DDX_CBString` função gerencia a transferência de `CString` dados entre o controle de edição de um controle de caixa de combinação em uma caixa de diálogo, exibição ou objeto de exibição de controle de formulário e um `CString` membro de dados do objeto de exibição de controle, exibição de formulário ou caixa de diálogo.

```
void AFXAPI DDX_CBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parâmetros

*pDX*<br/>
Um ponteiro para um `CDataExchange` objeto. A estrutura fornece esse objeto para estabelecer o contexto de troca de dados, incluindo sua direção.

*nIDC*<br/>
A ID de recurso de controle de caixa de combinação associado com a propriedade de controle.

*value*<br/>
Uma referência a uma variável de membro do objeto de exibição de controle com o qual os dados são trocados, exibição de formulário ou caixa de diálogo.

### <a name="remarks"></a>Comentários

Quando `DDX_CBString` é chamado, *valor* é definido como a seleção atual de caixa de combinação. Se nenhum item for selecionado, *valor* é definido como uma cadeia de caracteres de comprimento zero.

> [!NOTE]
>  Se a caixa de combinação é uma caixa de listagem suspensa, o valor trocado é limitado a 255 caracteres.

Para obter mais informações sobre DDX, consulte [troca de dados de caixa de diálogo e validação](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Cabeçalho** afxdd_.h

##  <a name="ddx_cbstringexact"></a>  DDX_CBStringExact

O `DDX_CBStringExact` função gerencia a transferência de `CString` dados entre o controle de edição de um controle de caixa de combinação em uma caixa de diálogo, exibição ou objeto de exibição de controle de formulário e um `CString` membro de dados do objeto de exibição de controle, exibição de formulário ou caixa de diálogo.

```
void AFXAPI DDX_CBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parâmetros

*pDX*<br/>
Um ponteiro para um `CDataExchange` objeto. A estrutura fornece esse objeto para estabelecer o contexto de troca de dados, incluindo sua direção.

*nIDC*<br/>
A ID de recurso de controle de caixa de combinação associado com a propriedade de controle.

*value*<br/>
Uma referência a uma variável de membro do objeto de exibição de controle com o qual os dados são trocados, exibição de formulário ou caixa de diálogo.

### <a name="remarks"></a>Comentários

Quando `DDX_CBStringExact` é chamado, *valor* é definido como a seleção atual de caixa de combinação. Se nenhum item for selecionado, *valor* é definido como uma cadeia de caracteres de comprimento zero.

> [!NOTE]
>  Se a caixa de combinação é uma caixa de listagem suspensa, o valor trocado é limitado a 255 caracteres.

Para obter mais informações sobre DDX, consulte [troca de dados de caixa de diálogo e validação](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Cabeçalho** afxdd_.h

##  <a name="ddx_check"></a>  DDX_Check

O `DDX_Check` função gerencia a transferência de **int** dados entre um controle de caixa de seleção em uma caixa de diálogo, exibição ou objeto de exibição de controle de formulário e uma **int** membro de dados de controle, exibição de formulário ou caixa de diálogo objeto de exibição.

```
void AFXAPI DDX_Check(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parâmetros

*pDX*<br/>
Um ponteiro para um `CDataExchange` objeto. A estrutura fornece esse objeto para estabelecer o contexto de troca de dados, incluindo sua direção.

*nIDC*<br/>
A ID de recurso do controle de caixa de seleção associada com a propriedade de controle.

*value*<br/>
Uma referência a uma variável de membro do objeto de exibição de controle com o qual os dados são trocados, exibição de formulário ou caixa de diálogo.

### <a name="remarks"></a>Comentários

Quando `DDX_Check` é chamado, *valor* é definido como o estado atual do controle de caixa de seleção. Para obter uma lista dos valores de estado possíveis, consulte [BM_GETCHECK](/windows/desktop/Controls/bm-getcheck) no SDK do Windows.

Para obter mais informações sobre DDX, consulte [troca de dados de caixa de diálogo e validação](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Cabeçalho** afxdd_.h

##  <a name="ddx_control"></a>  DDX_Control

O `DDX_Control` função subclasses o controle especificado pela *nIDC*, do objeto de exibição de controle, exibição de formulário ou caixa de diálogo.

```
void AFXAPI DDX_Control(
    CDataExchange* pDX,
    int nIDC,
    CWnd& rControl);
```

### <a name="parameters"></a>Parâmetros

*pDX*<br/>
Um ponteiro para um [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto.

*nIDC*<br/>
A ID de recurso do controle para ser uma subclasse.

*rControl*<br/>
Uma referência a uma variável de membro do objeto de exibição de controle relacionadas ao controle especificado, exibição de formulário ou caixa de diálogo.

### <a name="remarks"></a>Comentários

O *pDX* objeto é fornecido pelo framework quando o `DoDataExchange` função é chamada. Portanto, `DDX_Control` só deve ser chamado dentro de sua substituição do `DoDataExchange`.

Para obter mais informações sobre DDX, consulte [troca de dados de caixa de diálogo e validação](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Cabeçalho** afxdd_.h

##  <a name="ddx_datetimectrl"></a>  DDX_DateTimeCtrl

O `DDX_DateTimeCtrl` função gerencia a transferência de dados de data / hora entre um controle de seletor de data e hora ( [CDateTimeCtrl](../../mfc/reference/cdatetimectrl-class.md)) em um objeto de exibição de formulário ou caixa de diálogo e a um [CTime](../../atl-mfc-shared/reference/ctime-class.md) ou um [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) membro de dados do objeto de exibição de formulário ou caixa de diálogo.

```
void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    CTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);

void AFXAPI DDX_DateTimeCtrl(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parâmetros

*pDX*<br/>
Um ponteiro para um [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. A estrutura fornece esse objeto para estabelecer o contexto de troca de dados, incluindo sua direção. Você não precisa excluir este objeto.

*nIDC*<br/>
A ID de recurso de controle do seletor de data e hora associado à variável de membro.

*value*<br/>
Nas duas primeiras versões, uma referência a um `CTime` ou `COleDateTime` variável de membro, caixa de diálogo, exibição de formulário ou objeto de exibição de controle com o qual os dados são trocados. Na terceira versão, uma referência a um `CString` objeto de exibição de controle de membro de dados.

### <a name="remarks"></a>Comentários

Quando `DDX_DateTimeCtrl` é chamado, *valor* é definido como o atual estado do controle de seletor de tempo e a data ou o controle é definido como *valor*, dependendo da direção da troca.

Na terceira versão acima, `DDX_DateTimeCtrl` gerencia a transferência de `CString` controle de tempo de dados entre uma data e uma [CString](../../atl-mfc-shared/reference/cstringt-class.md) membro de dados do objeto de exibição do controle. A cadeia de caracteres é formatada usando regras da localidade atual para formatar datas e horas.

Para obter mais informações sobre DDX, consulte [troca de dados de caixa de diálogo e validação](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Cabeçalho** afxdd_.h

## <a name="ddx_managedcontrol"></a>  DDX_ManagedControl

Cria um controle do .NET correspondentes a ID do recurso. do controle

### <a name="syntax"></a>Sintaxe

```
template <typename T>
void DDX_ManagedControl(
   CDataExchange* pDX,
   int nIDC,
   CWinFormsControl<T>& control );
```

### <a name="parameters"></a>Parâmetros

*pDX*<br/>
Um ponteiro para um [classe CDataExchange](cdataexchange-class.md) objeto. A estrutura fornece esse objeto para estabelecer o contexto de troca de dados, incluindo sua direção.

*nIDC*<br/>
A ID de recurso do controle associado com a propriedade de controle.

*control*<br/>
Uma referência a um [classe CWinFormsControl](cwinformscontrol-class.md) objeto.

### <a name="remarks"></a>Comentários

`DDX_ManagedControl` chamadas [CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol) para criar um controle que corresponda a ID de controle de recurso. Use `DDX_ManagedControl` para criar controles de IDs de recurso no [CDialog::OnInitDialog](cdialog-class.md#oninitdialog). Troca de dados, você não precisa usar as funções DDX/DDV com controles de Windows Forms.

Para obter mais informações, confira [Como: Fazer a ligação de dados DDX/DDV com o Windows Forms](../../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md).

### <a name="requirements"></a>Requisitos

**Cabeçalho:** afxwinforms.h

##  <a name="ddx_ipaddress"></a>  DDX_IPAddress

O `DDX_IPAddress` função gerencia a transferência de dados entre um controle de endereço IP e um membro de dados do objeto de exibição do controle.

```
void AFXAPI DDX_IPAddress(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);
```

### <a name="parameters"></a>Parâmetros

*pDX*<br/>
Um ponteiro para um `CDataExchange` objeto. A estrutura fornece esse objeto para estabelecer o contexto de troca de dados, incluindo sua direção.

*nIDC*<br/>
A ID de recurso do controle de endereço IP associado com a propriedade de controle.

*value*<br/>
Uma referência para o DWORD que contém o valor do campo de quatro do controle de endereço IP. Os campos são preenchidos ou ler da seguinte maneira.

|Campo|Que contém o valor do campo de bits|
|-----------|-------------------------------------|
|3|0 a 7|
|2|8 a 15|
|1|16 por meio do 23|
|0|24 a 31|

Usar o Win32 [IPM_GETADDRESS](/windows/desktop/Controls/ipm-getaddress) para ler o valor ou use [IPM_SETADDRESS](/windows/desktop/Controls/ipm-setaddress) para preencher o valor. Essas mensagens são descritas no SDK do Windows.

### <a name="remarks"></a>Comentários

Quando `DDX_IPAddress` é chamado, *valor* é lida por qualquer um do controle de endereço IP, ou *valor* é gravado para o controle, dependendo da direção da troca.

Para obter mais informações sobre DDX, consulte [troca de dados de caixa de diálogo e validação](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Cabeçalho** afxdd_.h

##  <a name="ddx_lbindex"></a>  DDX_LBIndex

O `DDX_LBIndex` função gerencia a transferência de **int** dados entre um controle de caixa de listagem em uma caixa de diálogo, exibição ou objeto de exibição de controle de formulário e um **int** membro de dados de controle, exibição de formulário ou caixa de diálogo objeto de exibição.

```
void AFXAPI DDX_LBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index);
```

### <a name="parameters"></a>Parâmetros

*pDX*<br/>
Um ponteiro para um `CDataExchange` objeto. A estrutura fornece esse objeto para estabelecer o contexto de troca de dados, incluindo sua direção.

*nIDC*<br/>
A ID de recurso de controle de caixa de listagem associado com a propriedade de controle.

*index*<br/>
Uma referência a uma variável de membro do objeto de exibição de controle com o qual os dados são trocados, exibição de formulário ou caixa de diálogo.

### <a name="remarks"></a>Comentários

Quando `DDX_LBIndex` é chamado, *índice* é definido como o índice da seleção da caixa de lista atual. Se nenhum item for selecionado, *índice* é definido como -1.

Para obter mais informações sobre DDX, consulte [troca de dados de caixa de diálogo e validação](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Cabeçalho** afxdd_.h

##  <a name="ddx_lbstring"></a>  DDX_LBString

O `DDX_LBString` função gerencia a transferência de `CString` dados entre um controle de caixa de listagem em uma caixa de diálogo, exibição ou objeto de exibição de controle de formulário e um `CString` membro de dados do objeto de exibição de controle, exibição de formulário ou caixa de diálogo.

```
void AFXAPI DDX_LBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parâmetros

*pDX*<br/>
Um ponteiro para um `CDataExchange` objeto. A estrutura fornece esse objeto para estabelecer o contexto de troca de dados, incluindo sua direção.

*nIDC*<br/>
A ID de recurso de controle de caixa de listagem associado com a propriedade de controle.

*value*<br/>
Uma referência a uma variável de membro do objeto de exibição de controle com o qual os dados são trocados, exibição de formulário ou caixa de diálogo.

### <a name="remarks"></a>Comentários

Quando `DDX_LBString` é chamado para transferir dados para um controle de caixa de listagem, o primeiro item no controle cujo início corresponde à *valor* está selecionado. (Para corresponder o item inteiro em vez de apenas um prefixo, use [DDX_LBStringExact](#ddx_lbstringexact).) Se não houver nenhuma correspondência, nenhum item estiver selecionado. A correspondência diferencia maiusculas de minúsculas.

Quando `DDX_LBString` é chamado para transferir dados de um controle de caixa de listagem *valor* é definido como a seleção da caixa de lista atual. Se nenhum item for selecionado, *valor* é definido como uma cadeia de caracteres de comprimento zero.

> [!NOTE]
>  Se a caixa de listagem é uma caixa de listagem suspensa, o valor trocado é limitado a 255 caracteres.

Para obter mais informações sobre DDX, consulte [troca de dados de caixa de diálogo e validação](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Cabeçalho** afxdd_.h

##  <a name="ddx_lbstringexact"></a>  DDX_LBStringExact

O `DDX_CBStringExact` função gerencia a transferência de `CString` dados entre o controle de edição de um controle de caixa de listagem em uma caixa de diálogo, exibição ou objeto de exibição de controle de formulário e um `CString` membro de dados do objeto de exibição de controle, exibição de formulário ou caixa de diálogo.

```
void AFXAPI DDX_LBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value);
```

### <a name="parameters"></a>Parâmetros

*pDX*<br/>
Um ponteiro para um `CDataExchange` objeto. A estrutura fornece esse objeto para estabelecer o contexto de troca de dados, incluindo sua direção.

*nIDC*<br/>
A ID de recurso de controle de caixa de listagem associado com a propriedade de controle.

*value*<br/>
Uma referência a uma variável de membro do objeto de exibição de controle com o qual os dados são trocados, exibição de formulário ou caixa de diálogo.

### <a name="remarks"></a>Comentários

Quando `DDX_LBStringExact` é chamado para transferir dados para um controle de caixa de listagem, o primeiro item no controle que corresponde à *valor* está selecionado. (Para corresponder a apenas um prefixo em vez do item inteiro, use [DDX_LBString](#ddx_lbstring).) Se não houver nenhuma correspondência, nenhum item estiver selecionado. A correspondência diferencia maiusculas de minúsculas.

Quando `DDX_CBStringExact` é chamado para transferir dados de um controle de caixa de listagem *valor* é definido como a seleção da caixa de lista atual. Se nenhum item for selecionado, *valor* é definido como uma cadeia de caracteres de comprimento zero.

> [!NOTE]
>  Se a caixa de listagem é uma caixa de listagem suspensa, o valor trocado é limitado a 255 caracteres.

Para obter mais informações sobre DDX, consulte [troca de dados de caixa de diálogo e validação](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Cabeçalho** afxdd_.h

##  <a name="ddx_monthcalctrl"></a>  DDX_MonthCalCtrl

O `DDX_MonthCalCtrl` função gerencia a transferência de dados de data entre um controle de calendário mensal ( [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md)) em uma caixa de diálogo, exibição de formulário ou objeto de exibição de controle e um [CTime](../../atl-mfc-shared/reference/ctime-class.md) ou um [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) membro de dados do objeto de exibição de controle, exibição de formulário ou caixa de diálogo.

```
void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,
    int nIDC,
    CTime& value);

void AFXAPI DDX_MonthCalCtrl(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);
```

### <a name="parameters"></a>Parâmetros

*pDX*<br/>
Um ponteiro para um [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. A estrutura fornece esse objeto para estabelecer o contexto de troca de dados, incluindo sua direção. Você não precisa excluir este objeto.

*nIDC*<br/>
A ID do recurso de controle de calendário mensal associado com a variável de membro.

*value*<br/>
Uma referência a um `CTime` ou `COleDateTime` variável de membro do objeto de exibição de controle com o qual os dados são trocados, exibição de formulário ou caixa de diálogo.

### <a name="remarks"></a>Comentários

> [!NOTE]
>  O controle gerencia um valor de data. Os campos de hora em que o objeto de tempo estão definido para refletir a hora de criação da janela de controle, ou qualquer tempo foi definido no controle com uma chamada para `CMonthCalCtrl::SetCurSel`.

Quando `DDX_MonthCalCtrl` é chamado, *valor* é definido como o estado atual do controle de calendário mensal.

Para obter mais informações sobre DDX, consulte [troca de dados de caixa de diálogo e validação](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Cabeçalho** afxdd_.h

##  <a name="ddx_radio"></a>  DDX_Radio

O `DDX_Radio` função gerencia a transferência de **int** dados entre um grupo de controle de opção em uma caixa de diálogo, exibição ou objeto de exibição de controle de formulário e uma **int** membro de dados de controle, exibição de formulário ou caixa de diálogo objeto de exibição. O valor de **int** membro de dados é determinado de acordo com qual opção botão dentro do grupo é selecionado.

```
void AFXAPI DDX_Radio(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parâmetros

*pDX*<br/>
Um ponteiro para um `CDataExchange` objeto. A estrutura fornece esse objeto para estabelecer o contexto de troca de dados, incluindo sua direção.

*nIDC*<br/>
A ID de recurso do primeiro controle de rádio no grupo.

*value*<br/>
Uma referência a uma variável de membro do objeto de exibição de controle com o qual os dados são trocados, exibição de formulário ou caixa de diálogo.

### <a name="remarks"></a>Comentários

Quando `DDX_Radio` é chamado, *valor* é definido como o estado atual do grupo de controle de opção. O valor é definido como um índice baseado em 0 do controle de rádio que fez check- ou -1 se nenhum controle de rádio são verificadas.

Por exemplo, no caso em que o primeiro botão de opção no grupo é verificado (o botão com estilo WS_GROUP) o valor da **int** membro é 0 e assim por diante.

Para obter mais informações sobre DDX, consulte [troca de dados de caixa de diálogo e validação](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Cabeçalho** afxdd_.h

##  <a name="ddx_scroll"></a>  DDX_Scroll

O `DDX_Scroll` função gerencia a transferência de **int** dados entre um controle de barra de rolagem em uma caixa de diálogo, exibição ou objeto de exibição de controle de formulário e um **int** membro de dados de controle, exibição de formulário ou caixa de diálogo objeto de exibição.

```
void AFXAPI DDX_Scroll(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parâmetros

*pDX*<br/>
Um ponteiro para um `CDataExchange` objeto. A estrutura fornece esse objeto para estabelecer o contexto de troca de dados, incluindo sua direção.

*nIDC*<br/>
A ID de recurso do controle de barra de rolagem associado com a propriedade de controle.

*value*<br/>
Uma referência a uma variável de membro da caixa de diálogo, a exibição de formulário ou controle exibir objeto com o qual os dados são trocados.

### <a name="remarks"></a>Comentários

Quando `DDX_Scroll` é chamado, *valor* é definido como a posição atual de controle de posição do controle. Para obter mais informações sobre os valores associados com a posição atual de controle de posição do controle, consulte [GetScrollPos](/windows/desktop/api/winuser/nf-winuser-getscrollpos) no SDK do Windows.

Para obter mais informações sobre DDX, consulte [troca de dados de caixa de diálogo e validação](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Cabeçalho** afxdd_.h

##  <a name="ddx_slider"></a>  DDX_Slider

O `DDX_Slider` função gerencia a transferência de **int** dados entre um controle deslizante em uma exibição de formulário ou caixa de diálogo e uma **int** membro de dados do objeto de exibição de formulário ou caixa de diálogo.

```
void AFXAPI DDX_Slider(
    CDataExchange* pDX,
    int nIDC,
    int& value);
```

### <a name="parameters"></a>Parâmetros

*pDX*<br/>
Um ponteiro para um [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. A estrutura fornece esse objeto para estabelecer o contexto de troca de dados, incluindo sua direção.

*nIDC*<br/>
A ID de recurso do controle deslizante.

*value*<br/>
Uma referência para o valor a ser trocado. Este parâmetro contém ou define a posição atual do controle controle deslizante.

### <a name="remarks"></a>Comentários

Quando `DDX_Slider` é chamado, *valor* é definido como a posição atual do controle de posição do controle, ou o valor recebe a posição, dependendo da direção da troca.

Para obter mais informações sobre DDX, consulte [troca de dados de caixa de diálogo e validação](../../mfc/dialog-data-exchange-and-validation.md). Para obter informações sobre controles deslizantes, consulte [usando CSliderCtrl](../../mfc/using-csliderctrl.md).

### <a name="requirements"></a>Requisitos

  **Cabeçalho** afxdd_.h

##  <a name="ddx_text"></a>  DDX_Text

O `DDX_Text` função gerencia a transferência de **int**, **UINT**, **long**, DWORD, `CString`, **float**, ou **duplas** dados entre um controle de edição em uma caixa de diálogo exibição de formulário ou controle de exibição e uma [CString](../../atl-mfc-shared/reference/cstringt-class.md) membro de dados do objeto de exibição de controle, exibição de formulário ou caixa de diálogo.

```
void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    short& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    int& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    UINT& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    long& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    CString& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    float& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    double& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value);

void AFXAPI DDX_Text(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value);
```

### <a name="parameters"></a>Parâmetros

*pDX*<br/>
Um ponteiro para um [CDataExchange](../../mfc/reference/cdataexchange-class.md) objeto. A estrutura fornece esse objeto para estabelecer o contexto de troca de dados, incluindo sua direção.

*nIDC*<br/>
A ID de um controle de edição na caixa de diálogo, exibição de formulário ou objeto de exibição do controle.

*value*<br/>
Uma referência a um membro de dados no objeto de exibição de controle, exibição de formulário ou caixa de diálogo. O tipo de dados *valor* depende de qual das versões sobrecarregadas do `DDX_Text` você usar.

### <a name="remarks"></a>Comentários

Para obter mais informações sobre DDX, consulte [troca de dados de caixa de diálogo e validação](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Requisitos

  **Cabeçalho** afxdd_.h

## <a name="see-also"></a>Consulte também

[Rotinas de validação dos dados da caixa de diálogo padrão](standard-dialog-data-validation-routines.md)<br/>
[Macros e globais](mfc-macros-and-globals.md)<br/>
[CWinFormsControl::CreateManagedControl](cwinformscontrol-class.md#createmanagedcontrol)<br/>
[CDialog::OnInitDialog](cdialog-class.md#oninitdialog)
