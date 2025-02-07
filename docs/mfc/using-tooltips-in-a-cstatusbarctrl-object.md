---
title: Usando dicas de ferramenta em um objeto CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: 3f9a1fec7eb951fa76c542e09df751b4c58ddb16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411429"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Usando dicas de ferramenta em um objeto CStatusBarCtrl

Para habilitar dicas de ferramenta para um controle de barra de status, crie o `CStatusBarCtrl` objeto com o estilo SBT_TOOLTIPS.

> [!NOTE]
>  Se você estiver usando um `CStatusBar` objeto para implementar sua barra de status, use o `CStatusBar::CreateEx` função. Ele permite que você especificar estilos adicionais para o embedded `CStatusBarCtrl` objeto.

Uma vez a `CStatusBarCtrl` objeto foi criado com êxito, use [CStatusBarCtrl::SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) e [CStatusBarCtrl::GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) para definir e recuperar o texto da dica para um painel específico.

Depois que a dica de ferramenta tiver sido definida, ele é exibido somente se a parte tem um ícone e nenhum texto, ou se todo o texto não pode ser exibido dentro da parte. Não há suporte para dicas de ferramenta no modo simples.

## <a name="see-also"></a>Consulte também

[Usando CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
