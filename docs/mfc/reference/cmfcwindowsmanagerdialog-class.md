---
title: Classe CMFCWindowsManagerDialog
ms.date: 11/04/2016
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
ms.openlocfilehash: 5089decc7a118cd867aa14df51f5d7e269221108
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62373655"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>Classe CMFCWindowsManagerDialog

O `CMFCWindowsManagerDialog` objeto permite que um usuário gerencie janelas filho MDI em um aplicativo MDI.

## <a name="syntax"></a>Sintaxe

```
class CMFCWindowsManagerDialog : public CDialog
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](#cmfcwindowsmanagerdialog)|Constrói um objeto `CMFCWindowsManagerDialog`.|

## <a name="remarks"></a>Comentários

O `CMFCWindowsManagerDialog` contém uma lista de janelas filho MDI que estão abertos no aplicativo. O usuário pode controlar manualmente o estado das janelas filho MDI usando essa caixa de diálogo.

`CMFCWindowsManagerDialog` é incorporado dentro do [classe CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md). O `CMFCWindowsManagerDialog` não é uma classe que você deve criar manualmente. Em vez disso, chame a função [CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog), e irá criar e exibir um `CMFCWindowsManagerDialog` objeto.

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra como criar uma `CMFCWindowsManagerDialog` objeto chamando `CMDIFrameWndEx::ShowWindowsDialog`. Este trecho de código faz parte do [amostra de demonstração do Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxWindowsManagerDialog.h

##  <a name="cmfcwindowsmanagerdialog"></a>  CMFCWindowsManagerDialog::CMFCWindowsManagerDialog

Constrói uma [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md) objeto.

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>Parâmetros

*pMDIFrame*<br/>
[in] Um ponteiro para a janela pai ou proprietária.

*bHelpButton*<br/>
[in] Um parâmetro booliano que especifica se o framework exibe uma **ajudar** botão.

### <a name="remarks"></a>Comentários

Para obter mais informações sobre gerenciadores de visual, consulte [Gerenciador de visualização](../../mfc/visualization-manager.md).

## <a name="see-also"></a>Consulte também

[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)
