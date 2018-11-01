---
title: Quebras de palavra em controles de edição avançada
ms.date: 11/04/2016
helpviewer_keywords:
- CRichEditCtrl class [MFC], word breaks in
- word breaks
- breaking words in CRichEditCtrl
- rich edit controls [MFC], word breaks in
ms.assetid: 641dcf9e-7b40-4dc0-85f7-575a8c142f73
ms.openlocfilehash: efe4a0a2c06c14d913d43c51d1f0100f27c6a537
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632590"
---
# <a name="word-breaks-in-rich-edit-controls"></a>Quebras de palavra em controles de edição avançada

Controle de edição de uma avançada ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) chama uma função de chamada de "procedimento de quebra de palavra" para encontrar quebras entre as palavras e determinar onde ele pode quebrar a linha. O controle usa essas informações ao executar operações de quebra automática e ao processar as combinações de teclas CTRL + esquerda e CTRL + seta para direita. Um aplicativo pode enviar mensagens para um controle rich edit para substituir o procedimento de quebra de palavras do padrão, para recuperar informações de quebra de palavras e para determinar o que um determinado caractere de linha cai.

## <a name="see-also"></a>Consulte também

[Usando CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

