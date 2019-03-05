---
title: Inicializando a caixa de diálogo
ms.date: 11/04/2016
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
ms.openlocfilehash: 87b3405f1441e730cf5c9ce7fc03d2c7372e55db
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289527"
---
# <a name="initializing-the-dialog-box"></a>Inicializando a caixa de diálogo

Depois da caixa de diálogo caixa e todos os seus controles são criados, mas antes da caixa de diálogo caixa (de qualquer tipo) é exibida na tela, o objeto de caixa de diálogo [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) função membro é chamada. Para uma caixa de diálogo modal, isso ocorre durante o `DoModal` chamar. Para uma caixa de diálogo sem janela restrita `OnInitDialog` é chamado quando `Create` é chamado. Você normalmente substitui `OnInitDialog` para inicializar os controles da caixa de diálogo, como definir o texto inicial de uma caixa de edição. Você deve chamar o `OnInitDialog` função de membro da classe base, `CDialog`, do seu `OnInitDialog` substituir.

Se você deseja definir a cor do plano de fundo da caixa de diálogo (e todas as outras caixas de diálogo em seu aplicativo), consulte [definindo a cor do plano de fundo da caixa de diálogo](../mfc/setting-the-dialog-boxs-background-color.md).

## <a name="see-also"></a>Consulte também

[Ciclo de vida de uma caixa de diálogo](../mfc/life-cycle-of-a-dialog-box.md)
