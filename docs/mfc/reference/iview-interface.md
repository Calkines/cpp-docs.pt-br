---
title: Interface IView
ms.date: 11/04/2016
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
ms.openlocfilehash: 7684ef034acd247355b3f572c86fcb80cb126b0c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594344"
---
# <a name="iview-interface"></a>Interface IView

Implementa vários métodos que [CWinFormsView](../../mfc/reference/cwinformsview-class.md) usa para enviar notificações de exibição para um controle gerenciado.

## <a name="syntax"></a>Sintaxe

```
interface class IView
```

## <a name="members"></a>Membros

### <a name="public-methods"></a>Métodos Públicos

|Nome|Descrição|
|----------|-----------------|
|[IView::OnActivateView](#onactivateview)|Chamado pelo MFC quando uma exibição é ativada ou desativada.|
|[IView::OnInitialUpdate](#oninitialupdate)|Chamado pelo framework depois que o modo de exibição é anexado pela primeira vez no documento, mas antes que o modo de exibição é exibido inicialmente.|
|[IView::OnUpdate](#onupdate)|Chamado pelo MFC, depois que o documento do modo de exibição tiver sido modificado; Essa função permite que o modo de exibição atualizar sua exibição para refletir as modificações.|

## <a name="remarks"></a>Comentários

`IView` implementa vários métodos que `CWinFormsView` usa para encaminhar as notificações de exibição comuns para um controle gerenciado hospedado. Esses são [OnInitialUpdate](#oninitialupdate), [OnUpdate](#onupdate) e [OnActivateView](#onactivateview).

`IView` é semelhante à [CView](../../mfc/reference/cview-class.md), mas é usado somente com exibições gerenciadas e controles.

Para obter mais informações sobre como usar o Windows Forms, consulte [usando um controle de usuário do Windows Form no MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="requirements"></a>Requisitos

Cabeçalho: afxwinforms.h (definido no assembly atlmfc\lib\mfcmifc80.dll)

## <a name="onactivateview"></a> IView::OnActivateView

Chamado pelo MFC quando uma exibição é ativada ou desativada.
```
void OnActivateView(bool activate);
```

## <a name="parameters"></a>Parâmetros

*Ativar*<br/>
Indica se o modo de exibição está sendo ativada ou desativada.

## <a name="oninitialupdate"></a> IView::OnInitialUpdate

Chamado pelo framework depois que o modo de exibição é anexado pela primeira vez no documento, mas antes que o modo de exibição é exibido inicialmente.
```
void OnInitialUpdate();
```

## <a name="onupdate"></a> IView::OnUpdate

Chamado pelo MFC depois que o documento da exibição foi modificado.
```
void OnUpdate();
```

## <a name="remarks"></a>Comentários

Essa função permite que o modo de exibição atualizar sua exibição para refletir as modificações.

## <a name="see-also"></a>Consulte também

[Classe CWinFormsView](../../mfc/reference/cwinformsview-class.md)<br/>
[Classe CView](../../mfc/reference/cview-class.md)
