---
title: Selecionando um objeto gráfico em um contexto de dispositivo
ms.date: 11/04/2016
helpviewer_keywords:
- graphic objects [MFC], selecting into device context
- SelectObject method [MFC]
- GDI objects [MFC], device contexts
- lifetime, graphic objects [MFC]
- device contexts, selecting graphic objects into
- device contexts, graphic objects [MFC]
ms.assetid: cf54a330-63ef-421f-83eb-90ec7bd82eef
ms.openlocfilehash: c879369d445a9330139eff89be4ad8153252bfa1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438812"
---
# <a name="selecting-a-graphic-object-into-a-device-context"></a>Selecionando um objeto gráfico em um contexto de dispositivo

Este tópico aplica-se ao uso de objetos gráficos no contexto de dispositivo de uma janela. Depois que você [criar um objeto de desenho](../mfc/one-stage-and-two-stage-construction-of-objects.md), você deve selecioná-lo no contexto de dispositivo no lugar do objeto padrão armazenado lá:

[!code-cpp[NVC_MFCDocViewSDI#7](../mfc/codesnippet/cpp/selecting-a-graphic-object-into-a-device-context_1.cpp)]

## <a name="lifetime-of-graphic-objects"></a>Tempo de vida de objetos gráficos

O objeto gráfico retornado por [SelectObject](../mfc/reference/cdc-class.md#selectobject) é "temporário". Ou seja, ele será excluído pela [OnIdle](../mfc/reference/cwinapp-class.md#onidle) função de membro da classe `CWinApp` na próxima vez que o programa obtém ocioso de tempo. Desde que você use o objeto retornado por `SelectObject` em uma única função sem devolver o controle para o loop de mensagem principal, você não terá nenhum problema.

### <a name="what-do-you-want-to-know-more-about"></a>O que você deseja saber mais sobre

- [Objetos gráficos](../mfc/graphic-objects.md)

- [Construção de um e dois estágios de objetos gráficos](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Contextos de dispositivo](../mfc/device-contexts.md)

- [Desenhando em uma exibição](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>Consulte também

[Objetos gráficos](../mfc/graphic-objects.md)

