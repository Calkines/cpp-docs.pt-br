---
title: Manipulando notificação TTN_NEEDTEXT para dicas de ferramenta
ms.date: 11/04/2016
f1_keywords:
- TTN_NEEDTEXT
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
ms.openlocfilehash: 97db98322cd7c0d14e46f54a055bbc646c90d785
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268987"
---
# <a name="handling-ttnneedtext-notification-for-tool-tips"></a>Manipulando notificação TTN_NEEDTEXT para dicas de ferramenta

Como parte da [habilitando dicas de ferramenta](../mfc/enabling-tool-tips.md), você lidar com as **TTN_NEEDTEXT** mensagem adicionando a seguinte entrada ao mapa de mensagem da janela do proprietário:

[!code-cpp[NVC_MFCControlLadenDialog#40](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]

*memberFxn*<br/>
A função de membro a ser chamado quando o texto é necessário para que esse botão.

Observe que a ID de uma dica de ferramenta é sempre 0.

Declare a função de manipulador na definição de classe da seguinte maneira:

[!code-cpp[NVC_MFCControlLadenDialog#53](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]

onde estão os parâmetros em itálico:

*id*<br/>
Identificador do controle que enviou a notificação. Não usado. A id do controle é obtida dos **NMHDR** estrutura.

*pNMHDR*<br/>
Um ponteiro para o [NMTTDISPINFO](/windows/desktop/api/commctrl/ns-commctrl-tagnmttdispinfoa) estrutura. Essa estrutura também é discutida mais detalhadamente em [a estrutura TOOLTIPTEXT](../mfc/tooltiptext-structure.md).

*pResult*<br/>
Um ponteiro para o código de resultado que você pode definir antes de retornar. **TTN_NEEDTEXT** manipuladores podem ignorar o *pResult* parâmetro.

Como um exemplo de um manipulador de notificação de exibição de formulário:

[!code-cpp[NVC_MFCControlLadenDialog#54](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]

Chame `EnableToolTips` (este fragmento tirado `OnInitDialog`):

[!code-cpp[NVC_MFCControlLadenDialog#55](../mfc/codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]

## <a name="see-also"></a>Consulte também

[Dicas de ferramenta no Windows não derivadas de CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)
