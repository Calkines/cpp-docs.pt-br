---
title: Definindo o estado do dia de um controle de calendário mensal
ms.date: 11/04/2016
f1_keywords:
- MCN_GETDAYSTATE
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
ms.openlocfilehash: b8a91c8b0c3bdef9256628b9226c5f3ff154ed7d
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907520"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Definindo o estado do dia de um controle de calendário mensal

Um dos atributos de um controle de calendário mensal é a capacidade de armazenar informações, conhecidas como o estado do dia do controle, para cada dia do mês. Essas informações são usadas para enfatizar determinadas datas para o mês exibido no momento.

> [!NOTE]
>  O `CMonthCalCtrl` objeto deve ter o estilo MCS_DAYSTATE para exibir informações de estado de dia.

As informações de estado do dia são expressas como um tipo de dados de 32 bits, **MONTHDAYSTATE**. Cada bit em um campo de **MONTHDAYSTATE** de bits (de 1 a 31) representa o estado de um dia em um mês. Se um bit for on, o dia correspondente será exibido em negrito; caso contrário, ele será exibido sem ênfase.

Há dois métodos para definir o estado do dia do controle de calendário mensal: explicitamente com uma chamada para [CMonthCalCtrl:: SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) ou manipulando a mensagem de notificação MCN_GETDAYSTATE.

## <a name="handling-the-mcn_getdaystate-notification-message"></a>Manipulando a mensagem de notificação MCN_GETDAYSTATE

A mensagem MCN_GETDAYSTATE é enviada pelo controle para determinar como os dias dentro dos meses visíveis devem ser exibidos.

> [!NOTE]
>  Como o controle armazena em cache os meses anteriores e seguintes, em relação ao mês visível, você receberá essa notificação toda vez que um novo mês for escolhido.

Para lidar corretamente com essa mensagem, você deve determinar a quantidade de meses em que as informações de estado do dia estão sendo solicitadas, inicializar uma matriz de estruturas **MONTHDAYSTATE** com os valores adequados e inicializar o membro da estrutura relacionada com o novo divulgação. O procedimento a seguir, detalhando as etapas necessárias, pressupõe que você tenha `CMonthCalCtrl` um objeto chamado *m_monthcal* e uma matriz de objetos **MONTHDAYSTATE** , *mdState*.

#### <a name="to-handle-the-mcn_getdaystate-notification-message"></a>Para manipular a mensagem de notificação MCN_GETDAYSTATE

1. Usando o [Assistente de classe](reference/mfc-class-wizard.md), adicione um manipulador de notificação para a mensagem MCN_GETDAYSTATE ao objeto *M_monthcal* (consulte [mapeando mensagens para funções](../mfc/reference/mapping-messages-to-functions.md)).

1. No corpo do manipulador, adicione o seguinte código:

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   O exemplo converte o ponteiro *pNMHDR* para o tipo apropriado e, em seguida, determina quantos meses de informações estão sendo`pDayState->cDayState`solicitados (). Para cada mês, o campo de bits`pDayState->prgDayState[i]`atual () é inicializado como zero e as datas necessárias são definidas (nesse caso, o 15º dia de cada mês).

## <a name="see-also"></a>Consulte também

[Usando CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
