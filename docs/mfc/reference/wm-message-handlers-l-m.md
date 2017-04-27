---
title: 'Manipuladores de mensagens WM _: L - M | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ON_WM_MENUSELECT
- ON_WM_MBUTTONDBLCLK
- ON_WM_MOUSEACTIVATE
- ON_WM_MOUSEMOVE
- ON_WM_MOVING
- ON_WM_LBUTTONUP
- ON_WM_LBUTTONDBLCLK
- ON_WM_MEASUREITEM
- ON_WM_MDIACTIVATE
- ON_WM_MOVE
- ON_WM_LBUTTONDOWN
- ON_WM_MBUTTONDOWN
- ON_WM_MENUCHAR
- ON_WM_MBUTTONUP
dev_langs:
- C++
helpviewer_keywords:
- ON_WM_MENUSELECT
- ON_WM_MBUTTONDBLCLK
- ON_WM_MOVE
- ON_WM_MOUSEACTIVATE
- ON_WM_MBUTTONUP
- ON_WM_MOUSEMOVE
- ON_WM_MENUCHAR
- ON_WM_MBUTTONDOWN
- ON_WM_MEASUREITEM
- ON_WM_MOVING
- ON_WM_LBUTTONDOWN
- ON_WM_MDIACTIVATE
- ON_WM_LBUTTONDBLCLK
- ON_WM_LBUTTONUP
- WM_ messages
ms.assetid: 96ecaaf1-6d13-4e12-a454-535635967489
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 645e8ef051624977571830f2f1b40e54c55603f0
ms.lasthandoff: 02/25/2017

---
# <a name="wm-message-handlers-l---m"></a>Manipuladores de mensagens WM_: L - M
As seguintes entradas de mapa à esquerda correspondem aos protótipos de função à direita:  
  
|Entrada de mapa|Protótipo da função|  
|---------------|------------------------|  
|ON_WM_LBUTTONDBLCLK()|void afx_msg [OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk)(UINT, CPoint);|  
|ON_WM_LBUTTONDOWN()|void afx_msg [OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)(UINT, CPoint);|  
|ON_WM_LBUTTONUP()|void afx_msg [OnLButtonUp](../../mfc/reference/cwnd-class.md#onlbuttonup)(UINT, CPoint);|  
|ON_WM_MBUTTONDBLCLK()|void afx_msg [OnMButtonDblClk](../../mfc/reference/cwnd-class.md#onmbuttondblclk)(UINT, CPoint);|  
|ON_WM_MBUTTONDOWN()|void afx_msg [OnMButtonDown](../../mfc/reference/cwnd-class.md#onmbuttondown)(UINT, CPoint);|  
|ON_WM_MBUTTONUP()|void afx_msg [OnMButtonUp](../../mfc/reference/cwnd-class.md#onmbuttonup)(UINT, CPoint);|  
|ON_WM_MDIACTIVATE()|void afx_msg [OnMDIActivate](../../mfc/reference/cwnd-class.md#onmdiactivate)(BOOL, CWnd * CWnd\*);|  
|ON_WM_MEASUREITEM()|void afx_msg [OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)(LPMEASUREITEMSTRUCT);|  
|ON_WM_MENUCHAR()|afx_msg LONGA [OnMenuChar](../../mfc/reference/cwnd-class.md#onmenuchar)(UINT, UINT, CMenu *);|  
|ON_WM_MENUDRAG()|UINT afx_msg [OnMenuDrag](../../mfc/reference/cwnd-class.md#onmenudrag)(UINT, CMenu *);|  
|ON_WM_MENUGETOBJECT()|UINT afx_msg [OnMenuGetObject](../../mfc/reference/cwnd-class.md#onmenugetobject)(MENUGETOBJECTINFO *);|  
|ON_WM_MENURBUTTONUP()|void afx_msg [OnMenuRButtonUp](../../mfc/reference/cwnd-class.md#onmenurbuttonup)(UINT, CMenu *);|  
|ON_WM_MENUSELECT()|void afx_msg [OnMenuSelect](../../mfc/reference/cwnd-class.md#onmenuselect)(UINT, UINT, HMENU);|  
|ON_WM_MOUSEACTIVATE()|int afx_msg [OnMouseActivate](../../mfc/reference/cwnd-class.md#onmouseactivate)(CWnd *, UINT, UINT);|  
|ON_WM_MOUSEHOVER()|void afx_msg [OnMouseHover](../../mfc/reference/cwnd-class.md#onmousehover)(UINT, CPoint);|  
|ON_WM_MOUSEHWHEEL()|void afx_msg [OnMouseHWheel](../../mfc/reference/cwnd-class.md#onmousehwheel)(UINT, short, CPoint);|  
|ON_WM_MOUSELEAVE()|void afx_msg [OnMouseLeave](../../mfc/reference/cwnd-class.md#onmouseleave)();|  
|ON_WM_MOUSEMOVE()|void afx_msg [OnMouseMove](../../mfc/reference/cwnd-class.md#onmousemove)(UINT, CPoint);|  
|ON_WM_MOUSEWHEEL()|BOOL afx_msg [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel)(UINT, short, CPoint);|  
|ON_WM_MOVE()|void afx_msg [OnMove](../../mfc/reference/cwnd-class.md#onmove)(int, int);|  
|ON_WM_MOVING()|void afx_msg [OnMoving](../../mfc/reference/cwnd-class.md#onmoving)(UINT, LPRECT);|  
  
## <a name="see-also"></a>Consulte também  
 [Mapas de mensagem](../../mfc/reference/message-maps-mfc.md)   
 [Manipuladores para mensagens WM _](../../mfc/reference/handlers-for-wm-messages.md)

