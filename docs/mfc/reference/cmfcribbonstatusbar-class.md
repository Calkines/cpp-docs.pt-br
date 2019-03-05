---
title: Classe CMFCRibbonStatusBar
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddDynamicElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddSeparator
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::Create
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::CreateEx
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindByID
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExtendedArea
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetSpace
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsBottomFrame
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsInformationMode
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RecalcLayout
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveAll
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::SetInformation
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::OnDrawInformation
helpviewer_keywords:
- CMFCRibbonStatusBar [MFC], AddDynamicElement
- CMFCRibbonStatusBar [MFC], AddElement
- CMFCRibbonStatusBar [MFC], AddExtendedElement
- CMFCRibbonStatusBar [MFC], AddSeparator
- CMFCRibbonStatusBar [MFC], Create
- CMFCRibbonStatusBar [MFC], CreateEx
- CMFCRibbonStatusBar [MFC], FindByID
- CMFCRibbonStatusBar [MFC], FindElement
- CMFCRibbonStatusBar [MFC], GetCount
- CMFCRibbonStatusBar [MFC], GetElement
- CMFCRibbonStatusBar [MFC], GetExCount
- CMFCRibbonStatusBar [MFC], GetExElement
- CMFCRibbonStatusBar [MFC], GetExtendedArea
- CMFCRibbonStatusBar [MFC], GetSpace
- CMFCRibbonStatusBar [MFC], IsBottomFrame
- CMFCRibbonStatusBar [MFC], IsExtendedElement
- CMFCRibbonStatusBar [MFC], IsInformationMode
- CMFCRibbonStatusBar [MFC], RecalcLayout
- CMFCRibbonStatusBar [MFC], RemoveAll
- CMFCRibbonStatusBar [MFC], RemoveElement
- CMFCRibbonStatusBar [MFC], SetInformation
- CMFCRibbonStatusBar [MFC], OnDrawInformation
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
ms.openlocfilehash: b927012f241c30b1beec23ff7e0bbc9e8302d8da
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287629"
---
# <a name="cmfcribbonstatusbar-class"></a>Classe CMFCRibbonStatusBar

O `CMFCRibbonStatusBar` classe implementa um controle de barra de status que pode exibir os elementos da faixa de opções.

## <a name="syntax"></a>Sintaxe

```
class CMFCRibbonStatusBar : public CMFCRibbonBar
```

## <a name="members"></a>Membros

### <a name="public-methods"></a>Métodos Públicos

|Nome|Descrição|
|----------|-----------------|
|[CMFCRibbonStatusBar::AddDynamicElement](#adddynamicelement)|Adiciona um elemento dinâmico para a barra de status da faixa de opções.|
|[CMFCRibbonStatusBar::AddElement](#addelement)|Adiciona um novo elemento de faixa de opções para a barra de status da faixa de opções.|
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|Adiciona um elemento de faixa de opções para a área estendida da barra de status da faixa de opções.|
|[CMFCRibbonStatusBar::AddSeparator](#addseparator)|Adiciona um separador à barra de status da faixa de opções.|
|[CMFCRibbonStatusBar::Create](#create)|Cria uma barra de status da faixa de opções.|
|[CMFCRibbonStatusBar::CreateEx](#createex)|Cria uma barra de status da faixa de opções com um estilo estendido.|
|[CMFCRibbonStatusBar::FindByID](#findbyid)||
|[CMFCRibbonStatusBar::FindElement](#findelement)|Retorna um ponteiro para o elemento que tem a ID do comando especificado.|
|[CMFCRibbonStatusBar::GetCount](#getcount)|Retorna o número de elementos que estão localizados na área principal da barra de status da faixa de opções.|
|[CMFCRibbonStatusBar::GetElement](#getelement)|Retorna um ponteiro para o elemento que está localizado em um índice especificado.|
|[CMFCRibbonStatusBar::GetExCount](#getexcount)|Retorna o número de elementos que estão localizados na área estendida da barra de status da faixa de opções.|
|[CMFCRibbonStatusBar::GetExElement](#getexelement)|Retorna um ponteiro para o elemento que está localizado em um índice especificado na área estendida da barra de status da faixa de opções.|
|[CMFCRibbonStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCRibbonStatusBar::GetSpace](#getspace)||
|[CMFCRibbonStatusBar::IsBottomFrame](#isbottomframe)||
|[CMFCRibbonStatusBar::IsExtendedElement](#isextendedelement)||
|[CMFCRibbonStatusBar::IsInformationMode](#isinformationmode)|Determina se o modo de informações está habilitado para a barra de status da faixa de opções.|
|[CMFCRibbonStatusBar::RecalcLayout](#recalclayout)|(Substitui [CMFCRibbonBar::RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout).)|
|[CMFCRibbonStatusBar::RemoveAll](#removeall)|Remove todos os elementos da barra de status da faixa de opções.|
|[CMFCRibbonStatusBar::RemoveElement](#removeelement)|Remove o elemento que tem uma ID de comando especificada na barra de status da faixa de opções.|
|[CMFCRibbonStatusBar::SetInformation](#setinformation)|Habilita ou desabilita o modo de informações para a barra de status da faixa de opções.|

### <a name="protected-methods"></a>Métodos Protegidos

|Nome|Descrição|
|----------|-----------------|
|[CMFCRibbonStatusBar::OnDrawInformation](#ondrawinformation)|Exibe a cadeia de caracteres de informações é exibida no status da faixa de opções da barra quando o modo de informações está habilitado.|

## <a name="remarks"></a>Comentários

Os usuários podem alterar a visibilidade dos elementos da faixa de opções em uma barra de status da faixa de opções usando o menu de contexto interno para a barra de status da faixa de opções. Você pode adicionar ou remover elementos dinamicamente.

Uma barra de status da faixa de opções tem duas áreas: uma área principal e uma área estendida. Área estendida é exibida no lado direito da barra de status da faixa de opções e aparece em uma cor diferente do que a área principal.

Normalmente, a principal área da barra de status exibe notificações de status e a área estendida exibe controles de exibição. A área estendida permanece visível maior tempo possível quando o usuário redimensiona a barra de status da faixa de opções.

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra como usar vários métodos no `CMFCRibbonStatusBar` classe. O exemplo mostra como adicionar um novo elemento de faixa de opções para a barra de status da faixa de opções, adicione um elemento de faixa de opções para a área estendida da barra de status da faixa de opções, adicione um separador e habilitar o modo normal para a barra de status da faixa de opções.

[!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_1.cpp)]
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)

[CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxribbonstatusbar. h

##  <a name="adddynamicelement"></a>  CMFCRibbonStatusBar::AddDynamicElement

Adiciona um elemento dinâmico para a barra de status da faixa de opções.

```
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>Parâmetros

*pElement*<br/>
[in] Um ponteiro para um elemento dinâmico.

### <a name="remarks"></a>Comentários

Diferentemente dos elementos regulares, elementos dinâmicos não são personalizáveis e personalizar o menu da barra de status não exibi-los.

##  <a name="addelement"></a>  CMFCRibbonStatusBar::AddElement

Adiciona um novo elemento de faixa de opções para a barra de status da faixa de opções.

```
void AddElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parâmetros

*pElement*<br/>
[in] Um ponteiro para o elemento adicionado.

*lpszLabel*<br/>
[in] Um rótulo de texto do elemento.

*bIsVisible*<br/>
[in] TRUE se você deseja adicionar o elemento como visível, FALSE se você deseja adicionar o elemento como oculto.

##  <a name="addextendedelement"></a>  CMFCRibbonStatusBar::AddExtendedElement

Adiciona um elemento de faixa de opções para a área estendida da barra de status da faixa de opções.

```
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parâmetros

*pElement*<br/>
[in] Um ponteiro para o elemento adicionado.

*lpszLabel*<br/>
[in] O rótulo de texto do elemento.

*bIsVisible*<br/>
[in] TRUE se você deseja adicionar o elemento como visível, FALSE se você deseja adicionar o elemento como oculto.

### <a name="remarks"></a>Comentários

A área estendida está do lado direito do controle da barra de status.

##  <a name="addseparator"></a>  CMFCRibbonStatusBar::AddSeparator

Adiciona um separador à barra de status da faixa de opções.

```
void AddSeparator();
```

### <a name="remarks"></a>Comentários

O framework adiciona um separador após o método [CMFCRibbonStatusBar::AddElement](#addelement). Insere o último elemento.

##  <a name="create"></a>  CMFCRibbonStatusBar::Create

Cria uma barra de status da faixa de opções.

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parâmetros

*pParentWnd*<br/>
[in] Um ponteiro para a janela pai.

*dwStyle*<br/>
[in] Uma combinação de OR lógica de estilos de controle.

*nID*<br/>
[in] A ID do controle da barra de status.

### <a name="return-value"></a>Valor de retorno

TRUE se a barra de status é criada com êxito, FALSE caso contrário.

##  <a name="createex"></a>  CMFCRibbonStatusBar::CreateEx

Cria uma barra de status de faixa de opções que tem um estilo estendido.

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle=0,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parâmetros

*pParentWnd*<br/>
Um ponteiro para a janela pai.

*dwCtrlStyle*<br/>
Uma combinação de OR lógica de estilos adicionais para criar o objeto de barra de status.

*dwStyle*<br/>
O estilo de controle da barra de status.

*nID*<br/>
A ID do controle da barra de status.

### <a name="return-value"></a>Valor de retorno

TRUE se a barra de status é criada com êxito, FALSE caso contrário.

##  <a name="findbyid"></a>  CMFCRibbonStatusBar::FindByID

Para obter mais detalhes, consulte o código-fonte localizado na **VC\\atlmfc\\src\\mfc** pasta de instalação do Visual Studio.

```
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```

### <a name="parameters"></a>Parâmetros

[in] *uiCmdID*<br/>
[in] *BOOL*<br/>

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="findelement"></a>  CMFCRibbonStatusBar::FindElement

Retorna um ponteiro para o elemento que tem a ID do comando especificado.

```
CMFCRibbonBaseElement* FindElement(UINT uiID);
```

### <a name="parameters"></a>Parâmetros

*uiID*<br/>
[in] A ID do elemento.

### <a name="return-value"></a>Valor de retorno

Um ponteiro para o elemento que tem a ID do comando especificado. NULL se não houver nenhum tal elemento.

##  <a name="getcount"></a>  CMFCRibbonStatusBar::GetCount

Retorna o número de elementos que estão localizados na área principal da barra de status da faixa de opções.

```
int GetCount() const;
```

### <a name="return-value"></a>Valor de retorno

O número de elementos que estão localizados na área principal da barra de status da faixa de opções.

##  <a name="getelement"></a>  CMFCRibbonStatusBar::GetElement

Retorna um ponteiro para o elemento que está localizado em um índice especificado.

```
CMFCRibbonBaseElement* GetElement(int nIndex);
```

### <a name="parameters"></a>Parâmetros

*nIndex*<br/>
[in] Especifica um índice baseado em zero de um elemento que está localizado na área principal do controle de barra de status.

### <a name="return-value"></a>Valor de retorno

Um ponteiro para o elemento que está localizado no índice especificado. NULL se o índice for negativo ou excede o número de elementos na barra de status.

### <a name="remarks"></a>Comentários

##  <a name="getexcount"></a>  CMFCRibbonStatusBar::GetExCount

Retorna o número de elementos que estão localizados na área estendida da barra de status da faixa de opções.

```
int GetExCount() const;
```

### <a name="return-value"></a>Valor de retorno

O número de elementos que estão localizados na área estendida da barra de status da faixa de opções.

##  <a name="getexelement"></a>  CMFCRibbonStatusBar::GetExElement

Retorna um ponteiro para o elemento que está localizado em um índice especificado na área estendida da barra de status da faixa de opções. A área estendida está do lado direito do controle da barra de status.

```
CMFCRibbonBaseElement* GetExElement(int nIndex);
```

### <a name="parameters"></a>Parâmetros

*nIndex*<br/>
[in] Especifica o índice baseado em zero de um elemento que está localizado na área estendida do controle de barra de status.

### <a name="return-value"></a>Valor de retorno

Um ponteiro para o elemento que está localizado em um índice especificado na área estendida da barra de status da faixa de opções. NULL se *nIndex* for negativo ou exceder o número de elementos na área estendida da barra de status da faixa de opções.

### <a name="remarks"></a>Comentários

##  <a name="getextendedarea"></a>  CMFCRibbonStatusBar::GetExtendedArea

Para obter mais detalhes, consulte o código-fonte localizado na **VC\\atlmfc\\src\\mfc** pasta de instalação do Visual Studio.

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parâmetros

[in] *rect*<br/>

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="getspace"></a>  CMFCRibbonStatusBar::GetSpace

Para obter mais detalhes, consulte o código-fonte localizado na **VC\\atlmfc\\src\\mfc** pasta de instalação do Visual Studio.

```
int GetSpace() const;
```

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="isbottomframe"></a>  CMFCRibbonStatusBar::IsBottomFrame

Para obter mais detalhes, consulte o código-fonte localizado na **VC\\atlmfc\\src\\mfc** pasta de instalação do Visual Studio.

```
BOOL IsBottomFrame() const;
```

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="isextendedelement"></a>  CMFCRibbonStatusBar::IsExtendedElement

Para obter mais detalhes, consulte o código-fonte localizado na **VC\\atlmfc\\src\\mfc** pasta de instalação do Visual Studio.

```
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;
```

### <a name="parameters"></a>Parâmetros

[in] *pElement*<br/>

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="isinformationmode"></a>  CMFCRibbonStatusBar::IsInformationMode

Determina se o modo de informações está habilitado para a barra de status da faixa de opções.

```
BOOL IsInformationMode() const;
```

### <a name="return-value"></a>Valor de retorno

TRUE se a barra de status pode trabalhar no modo de informações. Caso contrário, FALSE.

### <a name="remarks"></a>Comentários

No modo de informações, a barra de status oculta todos os painéis regulares e exibe uma cadeia de caracteres de mensagem.

##  <a name="ondrawinformation"></a>  CMFCRibbonStatusBar::OnDrawInformation

Exibe a cadeia de caracteres que aparece sobre o status de faixa de opções da barra quando o modo de informações está habilitado.

```
virtual void OnDrawInformation(
    CDC* pDC,
    CString& strInfo,
    CRect rectInfo);
```

### <a name="parameters"></a>Parâmetros

*pDC*<br/>
[in] Um ponteiro para um contexto de dispositivo.

*strInfo*<br/>
[in] A cadeia de caracteres de informações.

*rectInfo*<br/>
[in] O retângulo delimitador.

### <a name="remarks"></a>Comentários

Substitua este método em uma classe derivada se você quiser personalizar a aparência da cadeia de caracteres de informações na barra de status. Use o [CMFCRibbonStatusBar::SetInformation](#setinformation) método para colocar a barra de status no modo de informações. Nesse modo, a barra de status oculta todos os painéis e exibe a cadeia de caracteres de informações especificada por *strInfo*.

##  <a name="recalclayout"></a>  CMFCRibbonStatusBar::RecalcLayout

Para obter mais detalhes, consulte o código-fonte localizado na **VC\\atlmfc\\src\\mfc** pasta de instalação do Visual Studio.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Comentários

##  <a name="removeall"></a>  CMFCRibbonStatusBar::RemoveAll

Remove todos os elementos da barra de status da faixa de opções.

```
void RemoveAll();
```

##  <a name="removeelement"></a>  CMFCRibbonStatusBar::RemoveElement

Remove o elemento que tem uma ID de comando especificada na barra de status da faixa de opções.

```
BOOL RemoveElement(UINT uiID);
```

### <a name="parameters"></a>Parâmetros

*uiID*<br/>
[in] A ID do elemento a ser removido da barra de status.

### <a name="return-value"></a>Valor de retorno

TRUE se um elemento com a especificada *uiID* é removido. FALSE caso contrário.

##  <a name="setinformation"></a>  CMFCRibbonStatusBar::SetInformation

Habilita ou desabilita o modo de informações para a barra de status da faixa de opções.

```
void SetInformation(LPCTSTR lpszInfo);
```

### <a name="parameters"></a>Parâmetros

*lpszInfo*<br/>
[in] A cadeia de caracteres de informações.

### <a name="remarks"></a>Comentários

Use esse método para colocar a barra de status no modo de informações. Nesse modo, a barra de status oculta todos os painéis e exibe a cadeia de caracteres de informações especificada por *lpszInfo*.

Quando lpszInfo for NULL, a barra de status será revertido para o modo normal.

## <a name="see-also"></a>Consulte também

[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)<br/>
[Classe CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[Classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)
