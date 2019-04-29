---
title: Classe CMFCDragFrameImpl
ms.date: 10/18/2018
f1_keywords:
- CMFCDragFrameImpl
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
ms.openlocfilehash: 05b4426da6bee0443a407cff583f47bee60262e4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348608"
---
# <a name="cmfcdragframeimpl-class"></a>Classe CMFCDragFrameImpl

O `CMFCDragFrameImpl` classe desenha o retângulo que aparece quando o usuário arrasta um painel no modo padrão do dock.
Para obter mais detalhes, consulte o código-fonte localizado na **VC\\atlmfc\\src\\mfc** pasta de instalação do Visual Studio.

## <a name="syntax"></a>Sintaxe

```
class CMFCDragFrameImpl
```

## <a name="remarks"></a>Comentários

Um objeto dessa classe é inserido em cada [classe CPane](../../mfc/reference/cpane-class.md) objeto. Assim, cada painel que usa o `CanFloat` método exibe um retângulo de arrastar quando o usuário arrasta-lo.

Você pode controlar a espessura do retângulo de arrastar usando [AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat) e [AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock).

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)

## <a name="requirements"></a>Requisitos

**Header:** afxdragframeimpl.h

##  <a name="enddrawdragframe"></a>  CMFCDragFrameImpl::EndDrawDragFrame

```
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```

### <a name="parameters"></a>Parâmetros

[in] *bClearInternalRects*<br/>

### <a name="remarks"></a>Comentários

##  <a name="init"></a>  CMFCDragFrameImpl::Init

```
void Init(CWnd* pDraggedWnd);
```

### <a name="parameters"></a>Parâmetros

[in] *pDraggedWnd*<br/>

### <a name="remarks"></a>Comentários

##  <a name="movedragframe"></a>  CMFCDragFrameImpl::MoveDragFrame

```
void MoveDragFrame(BOOL bForceMove = FALSE);
```

### <a name="parameters"></a>Parâmetros

[in] *bForceMove*<br/>

### <a name="remarks"></a>Comentários

##  <a name="placetabpredocking"></a>  CMFCDragFrameImpl::PlaceTabPreDocking

```
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,
    BOOL bFirstTime);

void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```

### <a name="parameters"></a>Parâmetros

[in] *pTabbedBar*<br/>

[in] *bFirstTime*<br/>

[in] *pCBarToPlaceOn*<br/>

### <a name="remarks"></a>Comentários

##  <a name="removetabpredocking"></a>  CMFCDragFrameImpl::RemoveTabPreDocking

```
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```

### <a name="parameters"></a>Parâmetros

[in] *pOldTargetBar*<br/>

### <a name="remarks"></a>Comentários

##  <a name="resetstate"></a>  CMFCDragFrameImpl::ResetState

```
void ResetState();
```

### <a name="remarks"></a>Comentários

## <a name="see-also"></a>Consulte também

[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CPane](../../mfc/reference/cpane-class.md)
