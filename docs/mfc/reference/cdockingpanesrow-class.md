---
title: Classe CDockingPanesRow
ms.date: 10/18/2018
f1_keywords:
- CDockingPanesRow
- AFXDOCKINGPANESROW/CDockingPanesRow
- AFXDOCKINGPANESROW/CDockingPanesRow::AddPane
- AFXDOCKINGPANESROW/CDockingPanesRow::AddPaneFromRow
- AFXDOCKINGPANESROW/CDockingPanesRow::ArrangePanes
- AFXDOCKINGPANESROW/CDockingPanesRow::CalcFixedLayout
- AFXDOCKINGPANESROW/CDockingPanesRow::Create
- AFXDOCKINGPANESROW/CDockingPanesRow::ExpandStretchedPanes
- AFXDOCKINGPANESROW/CDockingPanesRow::ExpandStretchedPanesRect
- AFXDOCKINGPANESROW/CDockingPanesRow::FixupVirtualRects
- AFXDOCKINGPANESROW/CDockingPanesRow::GetAvailableLength
- AFXDOCKINGPANESROW/CDockingPanesRow::GetAvailableSpace
- AFXDOCKINGPANESROW/CDockingPanesRow::GetClientRect
- AFXDOCKINGPANESROW/CDockingPanesRow::GetDockSite
- AFXDOCKINGPANESROW/CDockingPanesRow::GetExtraSpace
- AFXDOCKINGPANESROW/CDockingPanesRow::GetGroupFromPane
- AFXDOCKINGPANESROW/CDockingPanesRow::GetID
- AFXDOCKINGPANESROW/CDockingPanesRow::GetMaxPaneSize
- AFXDOCKINGPANESROW/CDockingPanesRow::GetPaneCount
- AFXDOCKINGPANESROW/CDockingPanesRow::GetPaneList
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowAlignment
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowHeight
- AFXDOCKINGPANESROW/CDockingPanesRow::GetRowOffset
- AFXDOCKINGPANESROW/CDockingPanesRow::GetVisibleCount
- AFXDOCKINGPANESROW/CDockingPanesRow::GetWindowRect
- AFXDOCKINGPANESROW/CDockingPanesRow::HasPane
- AFXDOCKINGPANESROW/CDockingPanesRow::IsEmpty
- AFXDOCKINGPANESROW/CDockingPanesRow::IsExclusiveRow
- AFXDOCKINGPANESROW/CDockingPanesRow::IsHorizontal
- AFXDOCKINGPANESROW/CDockingPanesRow::IsVisible
- AFXDOCKINGPANESROW/CDockingPanesRow::Move
- AFXDOCKINGPANESROW/CDockingPanesRow::MovePane
- AFXDOCKINGPANESROW/CDockingPanesRow::OnResizePane
- AFXDOCKINGPANESROW/CDockingPanesRow::RedrawAll
- AFXDOCKINGPANESROW/CDockingPanesRow::RemovePane
- AFXDOCKINGPANESROW/CDockingPanesRow::ReplacePane
- AFXDOCKINGPANESROW/CDockingPanesRow::RepositionPanes
- AFXDOCKINGPANESROW/CDockingPanesRow::Resize
- AFXDOCKINGPANESROW/CDockingPanesRow::ResizeByPaneDivider
- AFXDOCKINGPANESROW/CDockingPanesRow::ScreenToClient
- AFXDOCKINGPANESROW/CDockingPanesRow::SetExtra
- AFXDOCKINGPANESROW/CDockingPanesRow::ShowDockSiteRow
- AFXDOCKINGPANESROW/CDockingPanesRow::ShowPane
- AFXDOCKINGPANESROW/CDockingPanesRow::UpdateVisibleState
helpviewer_keywords:
- CDockingPanesRow [MFC], AddPane
- CDockingPanesRow [MFC], AddPaneFromRow
- CDockingPanesRow [MFC], ArrangePanes
- CDockingPanesRow [MFC], CalcFixedLayout
- CDockingPanesRow [MFC], Create
- CDockingPanesRow [MFC], ExpandStretchedPanes
- CDockingPanesRow [MFC], ExpandStretchedPanesRect
- CDockingPanesRow [MFC], FixupVirtualRects
- CDockingPanesRow [MFC], GetAvailableLength
- CDockingPanesRow [MFC], GetAvailableSpace
- CDockingPanesRow [MFC], GetClientRect
- CDockingPanesRow [MFC], GetDockSite
- CDockingPanesRow [MFC], GetExtraSpace
- CDockingPanesRow [MFC], GetGroupFromPane
- CDockingPanesRow [MFC], GetID
- CDockingPanesRow [MFC], GetMaxPaneSize
- CDockingPanesRow [MFC], GetPaneCount
- CDockingPanesRow [MFC], GetPaneList
- CDockingPanesRow [MFC], GetRowAlignment
- CDockingPanesRow [MFC], GetRowHeight
- CDockingPanesRow [MFC], GetRowOffset
- CDockingPanesRow [MFC], GetVisibleCount
- CDockingPanesRow [MFC], GetWindowRect
- CDockingPanesRow [MFC], HasPane
- CDockingPanesRow [MFC], IsEmpty
- CDockingPanesRow [MFC], IsExclusiveRow
- CDockingPanesRow [MFC], IsHorizontal
- CDockingPanesRow [MFC], IsVisible
- CDockingPanesRow [MFC], Move
- CDockingPanesRow [MFC], MovePane
- CDockingPanesRow [MFC], OnResizePane
- CDockingPanesRow [MFC], RedrawAll
- CDockingPanesRow [MFC], RemovePane
- CDockingPanesRow [MFC], ReplacePane
- CDockingPanesRow [MFC], RepositionPanes
- CDockingPanesRow [MFC], Resize
- CDockingPanesRow [MFC], ResizeByPaneDivider
- CDockingPanesRow [MFC], ScreenToClient
- CDockingPanesRow [MFC], SetExtra
- CDockingPanesRow [MFC], ShowDockSiteRow
- CDockingPanesRow [MFC], ShowPane
- CDockingPanesRow [MFC], UpdateVisibleState
ms.assetid: e7a17832-0ebb-4bce-b799-cec9b60f76fe
ms.openlocfilehash: a2d9c7894327a66c24fae3890856dbb95a6d10e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450122"
---
# <a name="cdockingpanesrow-class"></a>Classe CDockingPanesRow

Gerencia uma lista de painéis que estão localizados na mesma linha horizontal ou vertical (coluna) de um local de encaixe.

Para obter mais detalhes, consulte o código-fonte localizado na **VC\\atlmfc\\src\\mfc** pasta de instalação do Visual Studio.

## <a name="syntax"></a>Sintaxe

```
class CDockingPanesRow : public CObject
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|`CDockingPanesRow::CDockingPanesRow`|Construtor padrão.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CDockingPanesRow::AddPane](#addpane)||
|[CDockingPanesRow::AddPaneFromRow](#addpanefromrow)||
|[CDockingPanesRow::ArrangePanes](#arrangepanes)|Organiza os painéis em uma linha de acordo com os parâmetros de espaçamento e margem especificada.|
|[CDockingPanesRow::CalcFixedLayout](#calcfixedlayout)||
|[CDockingPanesRow::Create](#create)||
|[CDockingPanesRow::ExpandStretchedPanes](#expandstretchedpanes)||
|[CDockingPanesRow::ExpandStretchedPanesRect](#expandstretchedpanesrect)||
|[CDockingPanesRow::FixupVirtualRects](#fixupvirtualrects)||
|[CDockingPanesRow::GetAvailableLength](#getavailablelength)||
|[CDockingPanesRow::GetAvailableSpace](#getavailablespace)||
|[CDockingPanesRow::GetClientRect](#getclientrect)||
|[CDockingPanesRow::GetDockSite](#getdocksite)||
|[CDockingPanesRow::GetExtraSpace](#getextraspace)||
|[CDockingPanesRow::GetGroupFromPane](#getgroupfrompane)||
|[CDockingPanesRow::GetID](#getid)||
|[CDockingPanesRow::GetMaxPaneSize](#getmaxpanesize)||
|[CDockingPanesRow::GetPaneCount](#getpanecount)||
|[CDockingPanesRow::GetPaneList](#getpanelist)||
|[CDockingPanesRow::GetRowAlignment](#getrowalignment)||
|[CDockingPanesRow::GetRowHeight](#getrowheight)||
|[CDockingPanesRow::GetRowOffset](#getrowoffset)||
|[CDockingPanesRow::GetVisibleCount](#getvisiblecount)||
|[CDockingPanesRow::GetWindowRect](#getwindowrect)||
|[CDockingPanesRow::HasPane](#haspane)||
|[CDockingPanesRow::IsEmpty](#isempty)||
|[CDockingPanesRow::IsExclusiveRow](#isexclusiverow)||
|[CDockingPanesRow::IsHorizontal](#ishorizontal)||
|[CDockingPanesRow::IsVisible](#isvisible)||
|[CDockingPanesRow::Move](#move)||
|[CDockingPanesRow::MovePane](#movepane)||
|[CDockingPanesRow::OnResizePane](#onresizepane)||
|[CDockingPanesRow::RedrawAll](#redrawall)||
|[CDockingPanesRow::RemovePane](#removepane)||
|[CDockingPanesRow::ReplacePane](#replacepane)||
|[CDockingPanesRow::RepositionPanes](#repositionpanes)||
|[CDockingPanesRow::Resize](#resize)||
|[CDockingPanesRow::ResizeByPaneDivider](#resizebypanedivider)||
|[CDockingPanesRow::ScreenToClient](#screentoclient)||
|[CDockingPanesRow::SetExtra](#setextra)||
|[CDockingPanesRow::ShowDockSiteRow](#showdocksiterow)||
|[CDockingPanesRow::ShowPane](#showpane)||
|[CDockingPanesRow::UpdateVisibleState](#updatevisiblestate)||

## <a name="remarks"></a>Comentários

`CDockingPanesRow` objetos são criados internamente por objetos do site de encaixe.

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra como obter um `CDockingPanesRow` do objeto de um `CMFCAutoHideBar` objeto.

[!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cdockingpanesrow-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxDockingPanesRow.h

##  <a name="addpane"></a>  CDockingPanesRow::AddPane

```
virtual void AddPane(
    CPane* pControlBar,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL,
    BOOL bAddLast = FALSE);
```

### <a name="parameters"></a>Parâmetros

[in] *pControlBar*<br/>

[in] *dockMethod*<br/>

[in] *lpRect*<br/>

[in] *bAddLast*<br/>

### <a name="remarks"></a>Comentários

##  <a name="addpanefromrow"></a>  CDockingPanesRow::AddPaneFromRow

```
virtual void AddPaneFromRow(
    CPane* pControlBar,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Parâmetros

[in] *pControlBar*<br/>

[in] *dockMethod*<br/>

### <a name="remarks"></a>Comentários

##  <a name="arrangepanes"></a>  CDockingPanesRow::ArrangePanes

Organiza os painéis em uma linha de acordo com a margem especificada de encaixe e espaçamento de parâmetros.

```
virtual void ArrangePanes(
    int nMargin,
    int nSpacing);
```

### <a name="parameters"></a>Parâmetros

*nMargin*<br/>
[in] Especifica o deslocamento, em pixels, do primeiro painel no canto superior esquerdo da linha.

*nSpacing*<br/>
[in] Especifica o espaçamento, em pixels, entre os painéis.

### <a name="remarks"></a>Comentários

Chame esse método para organizar painéis na linha onde eles serão encaixado. Depois de chamar esse método, você deve chamar `CDockingPanesRow::FixupVirtualRects(FALSE, NULL)`.

##  <a name="calcfixedlayout"></a>  CDockingPanesRow::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parâmetros

[in] *bStretch*<br/>

[in] *bHorz*<br/>

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="cdockingpanesrow"></a>  CDockingPanesRow::CDockingPanesRow

```
CDockingPanesRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nHeight);
```

### <a name="parameters"></a>Parâmetros

[in] *pParentDockBar*<br/>

[in] *nOffset*<br/>

[in] *nHeight*<br/>

### <a name="remarks"></a>Comentários

##  <a name="create"></a>  CDockingPanesRow::Create

```
virtual BOOL Create();
```

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="expandstretchedpanes"></a>  CDockingPanesRow::ExpandStretchedPanes

```
void ExpandStretchedPanes();
```

### <a name="remarks"></a>Comentários

##  <a name="expandstretchedpanesrect"></a>  CDockingPanesRow::ExpandStretchedPanesRect

```
void ExpandStretchedPanesRect();
```

### <a name="remarks"></a>Comentários

##  <a name="fixupvirtualrects"></a>  CDockingPanesRow::FixupVirtualRects

```
void FixupVirtualRects(
    bool bMoveBackToVirtualRect,
    CPane* pBarToExclude = NULL);
```

### <a name="parameters"></a>Parâmetros

[in] *bMoveBackToVirtualRect*<br/>

[in] *pBarToExclude*<br/>

### <a name="remarks"></a>Comentários

##  <a name="getavailablelength"></a>  CDockingPanesRow::GetAvailableLength

```
virtual int GetAvailableLength(BOOL bUseVirtualRect = FALSE) const;
```

### <a name="parameters"></a>Parâmetros

[in] *bUseVirtualRect*<br/>

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="getavailablespace"></a>  CDockingPanesRow::GetAvailableSpace

```
virtual void GetAvailableSpace(CRect& rect);
```

### <a name="parameters"></a>Parâmetros

[in] *rect*<br/>

### <a name="remarks"></a>Comentários

##  <a name="getclientrect"></a>  CDockingPanesRow::GetClientRect

```
void GetClientRect(CRect& rect) const;
```

### <a name="parameters"></a>Parâmetros

[in] *rect*<br/>

### <a name="remarks"></a>Comentários

##  <a name="getdocksite"></a>  CDockingPanesRow::GetDockSite

```
CDockSite* GetDockSite() const;
```

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="getextraspace"></a>  CDockingPanesRow::GetExtraSpace

```
int GetExtraSpace() const;
```

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="getgroupfrompane"></a>  CDockingPanesRow::GetGroupFromPane

```
void GetGroupFromPane(
    CPane* pBar,
    CObList& lst);
```

### <a name="parameters"></a>Parâmetros

[in] *pBar*<br/>

[in] *lst*<br/>

### <a name="remarks"></a>Comentários

##  <a name="getid"></a>  CDockingPanesRow::GetID

```
int GetID() const;
```

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="getmaxpanesize"></a>  CDockingPanesRow::GetMaxPaneSize

```
int GetMaxPaneSize(BOOL bSkipHiddenBars = TRUE) const;
```

### <a name="parameters"></a>Parâmetros

[in] *bSkipHiddenBars*<br/>

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="getpanecount"></a>  CDockingPanesRow::GetPaneCount

```
int GetPaneCount() const;
```

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="getpanelist"></a>  CDockingPanesRow::GetPaneList

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="getrowalignment"></a>  CDockingPanesRow::GetRowAlignment

```
DWORD GetRowAlignment() const;
```

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="getrowheight"></a>  CDockingPanesRow::GetRowHeight

```
int GetRowHeight() const;
```

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="getrowoffset"></a>  CDockingPanesRow::GetRowOffset

```
int GetRowOffset() const;
```

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="getvisiblecount"></a>  CDockingPanesRow::GetVisibleCount

```
virtual int GetVisibleCount();
```

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="getwindowrect"></a>  CDockingPanesRow::GetWindowRect

```
void GetWindowRect(CRect& rect) const;
```

### <a name="parameters"></a>Parâmetros

[in] *rect*<br/>

### <a name="remarks"></a>Comentários

##  <a name="haspane"></a>  CDockingPanesRow::HasPane

```
BOOL HasPane(CBasePane* pControlBar);
```

### <a name="parameters"></a>Parâmetros

[in] *pControlBar*<br/>

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="isempty"></a>  CDockingPanesRow::IsEmpty

```
virtual BOOL IsEmpty() const;
```

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="isexclusiverow"></a>  CDockingPanesRow::IsExclusiveRow

```
virtual BOOL IsExclusiveRow() const;
```

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="ishorizontal"></a>  CDockingPanesRow::IsHorizontal

```
bool IsHorizontal() const;
```

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="isvisible"></a>  CDockingPanesRow::IsVisible

```
virtual BOOL IsVisible() const;
```

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="move"></a>  CDockingPanesRow::Move

```
virtual void Move(int nOffset);
```

### <a name="parameters"></a>Parâmetros

[in] *nOffset*<br/>

### <a name="remarks"></a>Comentários

##  <a name="movepane"></a>  CDockingPanesRow::MovePane

```
void MovePane(
    CPane* pControlBar,
    CPoint ptOffset,
    BOOL bSwapControlBars,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    CRect rectTarget,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    int nOffset,
    bool bForward,
    HDWP& hdwp);

void MovePane(
    CPane* pControlBar,
    int nAbsolutOffset,
    HDWP& hdwp);
```

### <a name="parameters"></a>Parâmetros

[in] *pControlBar*<br/>

[in] *ptOffset*<br/>

[in] *bSwapControlBars*<br/>

[in] *hdwp*<br/>

[in] *rectTarget*<br/>

[in] *nOffset*<br/>

[in] *bForward*<br/>

[in] *nAbsolutOffset*<br/>

### <a name="remarks"></a>Comentários

##  <a name="onresizepane"></a>  CDockingPanesRow::OnResizePane

```
virtual void OnResizePane(CBasePane* pControlBar);
```

### <a name="parameters"></a>Parâmetros

[in] *pControlBar*<br/>

### <a name="remarks"></a>Comentários

##  <a name="redrawall"></a>  CDockingPanesRow::RedrawAll

```
void RedrawAll();
```

### <a name="remarks"></a>Comentários

##  <a name="removepane"></a>  CDockingPanesRow::RemovePane

```
virtual void RemovePane(CPane* pControlBar);
```

### <a name="parameters"></a>Parâmetros

[in] *pControlBar*<br/>

### <a name="remarks"></a>Comentários

##  <a name="replacepane"></a>  CDockingPanesRow::ReplacePane

```
virtual BOOL ReplacePane(
    CPane* pBarOld,
    CPane* pBarNew);
```

### <a name="parameters"></a>Parâmetros

[in] *pBarOld*<br/>

[in] *pBarNew*<br/>

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="repositionpanes"></a>  CDockingPanesRow::RepositionPanes

```
virtual void RepositionPanes(
    CRect& rectNewParentBarArea,
    UINT nSide = (UINT)-1,
    BOOL bExpand = FALSE,
    int nOffset = 0);
```

### <a name="parameters"></a>Parâmetros

[in] *rectNewParentBarArea*<br/>

[in] *Xplorando o*<br/>

[in] *bExpand*<br/>

[in] *nOffset*<br/>

### <a name="remarks"></a>Comentários

##  <a name="resize"></a>  CDockingPanesRow::Resize

```
virtual int Resize(int nOffset);
```

### <a name="parameters"></a>Parâmetros

[in] *nOffset*<br/>

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="resizebypanedivider"></a>  CDockingPanesRow::ResizeByPaneDivider

```
virtual int ResizeByPaneDivider(int /*ignored*/);
```

### <a name="parameters"></a>Parâmetros

[in] *ignorado*<br/>

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="screentoclient"></a>  CDockingPanesRow::ScreenToClient

```
void ScreenToClient(CRect& rect) const;
```

### <a name="parameters"></a>Parâmetros

[in] *rect*<br/>

### <a name="remarks"></a>Comentários

##  <a name="setextra"></a>  CDockingPanesRow::SetExtra

```
void SetExtra(
    int nExtraSpace,
    AFX_ROW_ALIGNMENT rowExtraAlign);
```

### <a name="parameters"></a>Parâmetros

[in] *nExtraSpace*<br/>

[in] *rowExtraAlign*<br/>

### <a name="remarks"></a>Comentários

##  <a name="showdocksiterow"></a>  CDockingPanesRow::ShowDockSiteRow

```
virtual void ShowDockSiteRow(
    BOOL bShow,
    BOOL bDelay);
```

### <a name="parameters"></a>Parâmetros

[in] *bMostrar*<br/>

[in] *bDelay*<br/>

### <a name="remarks"></a>Comentários

##  <a name="showpane"></a>  CDockingPanesRow::ShowPane

```
virtual BOOL ShowPane(
    CPane* pControlBar,
    BOOL bShow,
    BOOL bDelay = FALSE);
```

### <a name="parameters"></a>Parâmetros

[in] *pControlBar*<br/>

[in] *bMostrar*<br/>

[in] *bDelay*<br/>

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="updatevisiblestate"></a>  CDockingPanesRow::UpdateVisibleState

```
virtual void UpdateVisibleState(BOOL bDelay);
```

### <a name="parameters"></a>Parâmetros

[in] *bDelay*<br/>

### <a name="remarks"></a>Comentários

## <a name="see-also"></a>Consulte também

[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Classe CDockSite](../../mfc/reference/cdocksite-class.md)<br/>
[Classe CPane](../../mfc/reference/cpane-class.md)
