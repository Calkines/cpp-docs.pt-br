---
title: Visão geral do controle de edição avançada
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: 7f307674645ad68455123b801fef8e4ae24b5b41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548272"
---
# <a name="overview-of-the-rich-edit-control"></a>Visão geral do controle de edição avançada

> [!IMPORTANT]
>  Se você estiver usando um controle de edição rica em uma caixa de diálogo (independentemente de seu aplicativo é SDI, MDI, ou baseado em diálogo), você deve chamar [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) depois antes da caixa de diálogo caixa é exibida. Em geral para chamar essa função é em seu programa `InitInstance` função de membro. Você não precisa chamá-lo para cada vez que você exibe a caixa de diálogo, apenas na primeira vez. Você não precisa chamar `AfxInitRichEdit` se você estiver trabalhando com `CRichEditView`.

Controles de edição avançada ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) fornecem uma interface de programação para formatação de texto. No entanto, um aplicativo deve implementar quaisquer componentes de interface do usuário necessários para tornar as operações de formatação disponíveis para o usuário. Ou seja, a edição avançada controle oferece suporte a alterar os atributos de caractere ou de parágrafo do texto selecionado. Alguns exemplos de caractere são atributos negrito, itálico, família de fontes e tamanho de ponto. Alinhamento, margens e paradas de tabulação são exemplos de atributos de parágrafo. No entanto, ele cabe a você para fornecer a interface do usuário, independentemente de ser botões de barra de ferramentas, itens de menu ou uma caixa de diálogo de caracteres de formato. Também há funções para consultar o controle de edição rica para os atributos da seleção atual. Use essas funções para exibir as configurações atuais para os atributos, por exemplo, definindo uma marca de seleção sobre o comando da interface do usuário, se a seleção tem o atributo de formatação de caracteres em negrito.

Para obter mais informações sobre caracteres e formatação de parágrafo, consulte [formatação de caractere](../mfc/character-formatting-in-rich-edit-controls.md) e [formatação de parágrafo](../mfc/paragraph-formatting-in-rich-edit-controls.md) mais adiante neste tópico.

Edição avançada controles suporte quase todas as operações e mensagens de notificação usadas com controles de edição de várias linhas. Assim, os aplicativos que já use controles de edição podem ser facilmente alterados para usar rich controles de edição. Notificações e mensagens adicionais permitem que aplicativos acessar os controles de edição exclusivo para rica de funcionalidade. Para obter informações sobre controles de edição, consulte [CEdit](../mfc/reference/cedit-class.md).

Para obter mais informações sobre as notificações, consulte [as notificações de um controle de edição de Rich](../mfc/notifications-from-a-rich-edit-control.md) mais adiante neste tópico.

## <a name="see-also"></a>Consulte também

[Usando CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

