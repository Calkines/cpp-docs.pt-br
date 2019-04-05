---
title: Classe CMFCDesktopAlertWndButton
ms.date: 11/04/2016
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
helpviewer_keywords:
- CMFCDesktopAlertWndButton [MFC], IsCaptionButton
- CMFCDesktopAlertWndButton [MFC], IsCloseButton
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
ms.openlocfilehash: 639342e0a09a6e970478fce1b5aac629f03c2015
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776928"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>Classe CMFCDesktopAlertWndButton

Permite que os botões a serem adicionados a uma caixa de diálogo de alerta da área de trabalho.

## <a name="syntax"></a>Sintaxe

```
class CMFCDesktopAlertWndButton : public CMFCButton
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|||
|-|-|
|Nome|Descrição|
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|Construtor padrão.|
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Destruidor.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nome|Descrição|
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|Determina se o botão é exibido na área de legenda da caixa de diálogo de alerta.|
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|Determina se o botão fecha a caixa de diálogo de alerta.|

### <a name="data-members"></a>Membros de Dados

|||
|-|-|
|Nome|Descrição|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Um valor booliano que especifica se o botão é exibido na área de legenda da caixa de diálogo de alerta.|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Um valor booliano que especifica se o botão fecha a caixa de diálogo de alerta.|

### <a name="remarks"></a>Comentários

Por padrão, o construtor define a `m_bIsCaptionButton` e `m_bIsCloseButton` membros de dados como FALSE. O pai `CMFCDesktopAlertDialog` conjuntos de objetos `m_bIsCaptionButton` como TRUE se o botão é posicionado na área de legenda da caixa de diálogo de alerta. O `CMFCDesktopAlertDialog` classe cria um `CMFCDesktopAlertWndButton` objeto que serve como o botão que fecha a caixa de diálogo alerta caixa e define `m_bIsCloseButton` como TRUE.

Adicione `CMFCDesktopAlertWndButton` objetos para um `CMFCDesktopAlertDialog` como faria ao adicionar qualquer botão do objeto. Para obter mais informações sobre `CMFCDesktopAlertDialog`, consulte [classe CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra como usar o `SetImage` método no `CMFCDesktopAlertWndButton` classe. Este trecho de código faz parte do [amostra de demonstração de alerta da área de trabalho](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxdesktopalertwnd.h

##  <a name="iscaptionbutton"></a>  CMFCDesktopAlertWndButton::IsCaptionButton

Determina se o botão é exibido na área de legenda da caixa de diálogo de alerta.

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>Valor de retorno

Diferente de zero se o botão é exibido na área de legenda da caixa de diálogo de alerta; Caso contrário, 0.

##  <a name="isclosebutton"></a>  CMFCDesktopAlertWndButton::IsCloseButton

Determina se o botão fecha a caixa de diálogo de alerta.

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>Valor de retorno

Diferente de zero se o botão fechar a caixa de diálogo de alerta; Caso contrário, 0.

## <a name="see-also"></a>Consulte também

[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)
