---
title: Teclas de acesso específicas de thread
ms.date: 11/04/2016
helpviewer_keywords:
- CHotKeyCtrl class [MFC], thread-specific hot keys
- keyboard shortcuts [MFC], hot keys
- threading [MFC], hot keys in CHotKeyCtrl
- access keys [MFC], hot keys
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
ms.openlocfilehash: 4b393fe1af060a4b235162ce8cdfd94a1a391085
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594149"
---
# <a name="thread-specific-hot-keys"></a>Teclas de acesso específicas de thread

Um aplicativo define uma tecla de acesso específicas de thread ([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)) usando o Windows `RegisterHotKey` função. Quando o usuário pressiona uma tecla de acesso específicas de thread, o Windows lança um [WM_HOTKEY](/windows/desktop/inputdev/wm-hotkey) mensagem para o início da fila de mensagens do thread específico. A mensagem WM_HOTKEY contém o código de tecla virtual, o estado de deslocamento e a ID definida pelo usuário de que a tecla de acesso específica que foi pressionada. Para obter uma lista de códigos de tecla virtuais padrão, consulte WinUser. h. Para obter mais informações sobre esse método, consulte [RegisterHotKey](https://msdn.microsoft.com/library/windows/desktop/ms646309).

Observe que o estado de deslocamento sinalizadores usado na chamada para `RegisterHotKey` não são iguais aos retornados pela [GetHotKey](../mfc/reference/chotkeyctrl-class.md#gethotkey) a função de membro; você terá que converter esses sinalizadores antes de chamar `RegisterHotKey`.

## <a name="see-also"></a>Consulte também

[Usando CHotKeyCtrl](../mfc/using-chotkeyctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

