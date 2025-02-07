---
title: Criando o controle de cabeçalho
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
ms.openlocfilehash: 22739e5671fb0300011de84d976eff0ce26eaedb
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907581"
---
# <a name="creating-the-header-control"></a>Criando o controle de cabeçalho

O controle de cabeçalho não está diretamente disponível no editor da caixa de diálogo (embora você possa adicionar um controle de lista, que inclui um controle de cabeçalho).

### <a name="to-put-a-header-control-in-a-dialog-box"></a>Para colocar um controle de cabeçalho em uma caixa de diálogo

1. Insira manualmente uma variável de membro do tipo [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) em sua classe de caixa de diálogo.

1. No [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), crie e defina os estilos para o `CHeaderCtrl`, posicione-o e exiba-o.

1. Adicione itens ao controle de cabeçalho.

1. Use o [Assistente de classe](reference/mfc-class-wizard.md) para mapear funções de manipulador na classe de caixa de diálogo para qualquer mensagem de notificação de controle de cabeçalho que você precise manipular (consulte [mapeando mensagens para funções](../mfc/reference/mapping-messages-to-functions.md)).

### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>Para colocar um controle de cabeçalho em uma exibição (não um CListView)

1. Insira um objeto [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) em sua classe View.

1. Estilo, posição e exibição da janela de controle de cabeçalho na função de membro [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) da exibição.

1. Adicione itens ao controle de cabeçalho.

1. Use o [Assistente de classe](reference/mfc-class-wizard.md) para mapear funções de manipulador na classe de exibição para qualquer mensagem de notificação de controle de cabeçalho que você precisa manipular (consulte [mapeando mensagens para funções](../mfc/reference/mapping-messages-to-functions.md)).

Em ambos os casos, o objeto de controle inserido é criado quando o objeto View ou Dialog é criado. Em seguida, você deve chamar [CHeaderCtrl:: Create](../mfc/reference/cheaderctrl-class.md#create) para criar a janela de controle. Para posicionar o controle, chame [CHeaderCtrl:: layout](../mfc/reference/cheaderctrl-class.md#layout) para determinar o tamanho inicial do controle e a posição e [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos) para definir a posição desejada. Em seguida, adicione itens conforme descrito em [adicionando itens ao controle de cabeçalho](../mfc/adding-items-to-the-header-control.md).

Para obter mais informações, consulte [criando um controle de cabeçalho](/windows/win32/Controls/header-controls) na SDK do Windows.

## <a name="see-also"></a>Consulte também

[Usando CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
