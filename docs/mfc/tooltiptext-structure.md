---
title: Estrutura TOOLTIPTEXT
ms.date: 11/04/2016
f1_keywords:
- TOOLTIPTEXT
helpviewer_keywords:
- TOOLTIPTEXT structure [MFC]
- tool tips [MFC], notifications
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
ms.openlocfilehash: d184b1d507579309051cd6c70ea6525463c44881
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676506"
---
# <a name="tooltiptext-structure"></a>Estrutura TOOLTIPTEXT

Escrever seus [manipulador de notificação de dica de ferramenta](../mfc/handling-ttn-needtext-notification-for-tool-tips.md), você precisa usar o **TOOLTIPTEXT** estrutura. Os membros de **TOOLTIPTEXT** estrutura são:

```cpp
typedef struct {
    NMHDR     hdr;        // required for all WM_NOTIFY messages
    LPTSTR    lpszText;   // see below
    TCHAR     szText[80]; // buffer for tool tip text
    HINSTANCE hinst;      // see below
    UINT      uflags;     // flag indicating how to interpret the
                          // idFrom member of the NMHDR structure
                          // that is included in the structure
} TOOLTIPTEXT, FAR *LPTOOLTIPTEXT;
```

*HDR*<br/>
Identifica a ferramenta de que precisa de texto. O único membro dessa estrutura, que talvez seja necessário é a ID de comando. do controle ID de comando do controle estará na *idFrom* membro do **NMHDR** estrutura, acessada com a sintaxe `hdr.idFrom`. Ver [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) para uma discussão sobre os membros a **NMHDR** estrutura.

*lpszText*<br/>
Endereço de uma cadeia de caracteres para receber o texto para uma ferramenta.

*szText*<br/>
Buffer que recebe o texto da dica de ferramenta. Um aplicativo pode copiar o texto a esse buffer como uma alternativa para especificar um endereço de cadeia de caracteres.

*HINST*<br/>
Identificador da instância que contém uma cadeia de caracteres a ser usado como o texto da dica de ferramenta. Se *lpszText* é o endereço do texto da dica de ferramenta, esse membro é NULL.

Quando você manipula a `TTN_NEEDTEXT` notificação de mensagem, especifique a cadeia de caracteres a ser exibido em uma das seguintes maneiras:

- Copie o texto para o buffer especificado o *szText* membro.

- Copie o endereço do buffer que contém o texto para o *lpszText* membro.

- Copie o identificador de um recurso de cadeia de caracteres para o *lpszText* membro e copie o identificador da instância que contém o recurso para o *hinst* membro.

## <a name="see-also"></a>Consulte também

[Dicas de ferramenta no Windows não derivadas de CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)

