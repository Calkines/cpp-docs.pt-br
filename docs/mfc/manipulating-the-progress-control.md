---
title: Manipulando o controle de progresso
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], working with
- progress controls [MFC], manipulating
- CProgressCtrl class [MFC], manipulating
- controlling progress controls [MFC]
- CProgressCtrl class [MFC], using
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
ms.openlocfilehash: c9da6f8048adf1c7da184570ff7f94deee7441e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279184"
---
# <a name="manipulating-the-progress-control"></a>Manipulando o controle de progresso

Há três maneiras de alterar a posição atual de um controle de progresso ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)).

- A posição pode ser alterada por um valor de incremento predefinidos.

- A posição pode ser alterada por uma quantidade arbitrária.

- A posição pode ser alterada para um valor específico.

### <a name="to-change-the-position-by-a-preset-amount"></a>Para alterar a posição em um valor predefinido

1. Use o [SetStep](../mfc/reference/cprogressctrl-class.md#setstep) a função de membro para definir o valor de incremento. Por padrão, esse valor é 10. Normalmente, esse valor é definido como uma das configurações iniciais para o controle. O valor da etapa pode ser negativo.

1. Use o [StepIt](../mfc/reference/cprogressctrl-class.md#stepit) a função de membro para incrementar a posição. Isso faz com que o controle para redesenhar a mesmo.

    > [!NOTE]
    >  `StepIt` fará com que a posição seja ajustada. Por exemplo, dado um intervalo de 1 -100, uma etapa de 20 e uma posição de 90, `StepIt` definirá a posição como 10.

### <a name="to-change-the-position-by-an-arbitrary-amount"></a>Para alterar a posição por uma quantidade arbitrária

1. Use o [OffsetPos](../mfc/reference/cprogressctrl-class.md#offsetpos) a função de membro para alterar a posição. `OffsetPos` aceitará valores negativos.

    > [!NOTE]
    >  `OffsetPos`, ao contrário de `StepIt`, não será encapsulado para a posição. A nova posição é ajustada para permanecer dentro do intervalo.

### <a name="to-change-the-position-to-a-specific-value"></a>Para alterar a posição com um valor específico

1. Use o [SetPos](../mfc/reference/cprogressctrl-class.md#setpos) a função de membro para definir a posição com um valor específico. Se necessário, a nova posição é ajustada para ficar dentro do intervalo.

Normalmente, o controle de progresso é usado unicamente para saída. Para obter a posição atual sem especificar um novo valor, use [GetPos](../mfc/reference/cprogressctrl-class.md#getpos).

## <a name="see-also"></a>Consulte também

[Usando CProgressCtrl](../mfc/using-cprogressctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
