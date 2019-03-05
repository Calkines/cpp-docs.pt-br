---
title: Criando o controle de seletor de data e hora
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
ms.openlocfilehash: b3dd04d917667ff04001a455263d2a2f4af9bf9c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282065"
---
# <a name="creating-the-date-and-time-picker-control"></a>Criando o controle de seletor de data e hora

Como o controle de seletor de data e hora é criado depende se você estiver usando o controle em uma caixa de diálogo ou criá-lo em uma janela nondialog.

### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>Usar CDateTimeCtrl diretamente em uma caixa de diálogo

1. No editor de caixa de diálogo, adicione uma data e o controle de seletor de tempo até o recurso de modelo de caixa de diálogo. Especifique sua ID de controle.

1. Especifique todos os estilos necessários, usando a caixa de diálogo Propriedades do controle de seletor de data e hora.

1. Use o [Assistente para adição de variável de membro](../ide/adding-a-member-variable-visual-cpp.md) para adicionar uma variável de membro do tipo [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md) com a propriedade de controle. Você pode usar esse membro para chamar `CDateTimeCtrl` funções de membro.

1. Use a janela Propriedades para mapear as funções de manipulador na classe de caixa de diálogo de qualquer controle de seletor de tempo de data [notificação](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md) mensagens que você precisa manipular (consulte [mapeando mensagens para funções](../mfc/reference/mapping-messages-to-functions.md)).

1. Na [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), defina todos os estilos adicionais para o `CDateTimeCtrl` objeto.

### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>Para usar CDateTimeCtrl em uma janela de nondialog

1. Declare o controle na classe de janela ou exibição.

1. Chame o controle [Create](../mfc/reference/ctabctrl-class.md#create) função de membro, possivelmente em [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), possivelmente como antecipada como da janela pai [OnCreate](../mfc/reference/cwnd-class.md#oncreate) função do manipulador (se você estiver Criando subclasses de controle). Defina os estilos para o controle.

## <a name="see-also"></a>Consulte também

[Usando CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
