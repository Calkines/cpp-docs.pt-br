---
title: Criando um controle de caixa de combinação estendido
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: d1e81664403f45a0a35cd24ceea16e1425b03403
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668761"
---
# <a name="creating-an-extended-combo-box-control"></a>Criando um controle de caixa de combinação estendido

Como o controle de caixa de combinação estendida é criado depende se você estiver usando o controle em uma caixa de diálogo ou criá-lo em uma janela nondialog.

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>Usar CComboBoxEx diretamente em uma caixa de diálogo

1. No editor de caixa de diálogo, adicione um controle de caixa de combinação estendido até o recurso de modelo de caixa de diálogo. Especifique sua ID de controle.

1. Especifique todos os estilos necessários, usando a caixa de diálogo Propriedades da caixa de combinação estendido.

1. Use o [Assistente para adição de variável de membro](../ide/adding-a-member-variable-visual-cpp.md) para adicionar uma variável de membro do tipo [CComboBoxEx](../mfc/reference/ccomboboxex-class.md) com a propriedade de controle. Você pode usar esse membro para chamar `CComboBoxEx` funções de membro.

1. Use a janela Propriedades para mapear as funções de manipulador na classe de caixa de diálogo de mensagens de notificação do controle qualquer combinação estendida caixa você precisa manipular (consulte [mapeando mensagens para funções](../mfc/reference/mapping-messages-to-functions.md)).

1. Na [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), defina todos os estilos adicionais para o `CComboBoxEx` objeto.

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>Para usar CComboBoxEx em uma janela de nondialog

1. Defina o controle na classe de janela ou exibição.

1. Chame o controle [Create](../mfc/reference/ctabctrl-class.md#create) função de membro, possivelmente em [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), possivelmente como antecipada como da janela pai [OnCreate](../mfc/reference/cwnd-class.md#oncreate) função do manipulador. Defina os estilos para o controle.

## <a name="see-also"></a>Consulte também

[Usando CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Controles](../mfc/controls-mfc.md)

