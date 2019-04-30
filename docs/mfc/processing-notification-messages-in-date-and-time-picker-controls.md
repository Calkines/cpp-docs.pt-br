---
title: Processando mensagens de notificação em controles de seletor de data e hora
ms.date: 11/04/2016
f1_keywords:
- DTN_CLOSEUP
- DTN_DATETIMECHANGE
- DTN_DROPDOWN
helpviewer_keywords:
- DTN_DROPDOWN notification [MFC]
- DTN_DATETIMECHANGE notification [MFC]
- DTN_CLOSEUP notification [MFC]
- DateTimePicker control [MFC], handling notifications
- CDateTimeCtrl class [MFC], handling notifications
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
ms.openlocfilehash: ce84863744629d30248f94b94448d776177f9841
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64339545"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>Processando mensagens de notificação em controles de seletor de data e hora

Conforme os usuários interagem com a data e controle de seletor de tempo, o controle (`CDateTimeCtrl`) envia mensagens de notificação à sua janela pai, normalmente, um objeto de exibição ou a caixa de diálogo. Se você quiser fazer algo em resposta, lidar com essas mensagens. Por exemplo, quando o usuário abre o seletor de data e hora para exibir o controle de calendário mensal inserido, a DTN_DROPDOWN (notificação) é enviada.

Use a janela Propriedades para adicionar manipuladores de notificação para a classe pai para essas mensagens que você deseja implementar.

A lista a seguir descreve as várias notificações enviadas pelo controle de seletor de data e hora.

- DTN_DROPDOWN notifica o pai que o controle de calendário do mês inserido está prestes a ser exibido. Essa notificação é enviada somente quando o estilo DTS_UPDOWN não foi definido. Para obter mais informações sobre essa notificação, consulte [acessando o controle de calendário mensal inserido](../mfc/accessing-the-embedded-month-calendar-control.md).

- DTN_CLOSEUP notifica o pai que o controle de calendário do mês inserido está prestes a ser fechado. Essa notificação é enviada somente quando o estilo DTS_UPDOWN não foi definido.

- DTN_DATETIMECHANGE notifica o pai que ocorreu uma alteração no controle.

- DTN_FORMAT notifica o pai que o texto é necessário a ser exibido em um campo de retorno de chamada. Para obter mais informações sobre essa notificação e os campos de retorno de chamada, consulte [usando os campos de retorno de chamada em uma data e o controle de seletor de tempo](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).

- DTN_FORMATQUERY solicita o pai para fornecer o tamanho máximo permitido da cadeia de caracteres que será exibido em um campo de retorno de chamada. Manipular essa notificação permite que o controle corretamente a saída de exibição em todos os momentos, reduzindo a cintilação dentro de exibição do controle. Para obter mais informações sobre essa notificação, consulte [usando os campos de retorno de chamada em uma data e o controle de seletor de tempo](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md).

- DTN_USERSTRING notifica o pai que o usuário termina de editar o conteúdo do controle de seletor de data e hora. Essa notificação é enviada somente quando o estilo DTS_APPCANPARSE tiver sido definido.

- DTN_WMKEYDOWN notifica o pai quando o usuário digita em um campo de retorno de chamada. Manipule essa notificação para emular a mesma resposta teclado suportada para campos de retorno de chamada não em um controle de seletor de data e hora. Para obter mais informações sobre essa notificação, consulte [que dão suporte a campos de retorno de chamada em um controle DTP](/windows/desktop/Controls/date-and-time-picker-controls) no SDK do Windows.

## <a name="see-also"></a>Consulte também

[Usando CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
