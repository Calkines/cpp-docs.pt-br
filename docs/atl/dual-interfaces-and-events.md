---
title: Interfaces duplas e eventos
ms.date: 11/04/2016
helpviewer_keywords:
- events [C++], dual interfaces
- dual interfaces, events
ms.assetid: bb382f7c-e885-4274-bf07-83f3602615d2
ms.openlocfilehash: f94e87f077846af8d61b06145f776f385051e79f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640590"
---
# <a name="dual-interfaces-and-events"></a>Interfaces duplas e eventos

Embora seja possível criar uma interface de eventos como um duplo, há um número de design bons motivos para não fazê-lo. O motivo pelo qual fundamental é que a origem do evento será disparado somente o evento por meio de vtable ou `Invoke`, não ambos. Se a origem do evento dispara o evento como uma chamada de método direto vtable, o `IDispatch` métodos nunca serão usados e é claro que a interface deve ter sido uma interface vtable puro. Se a origem do evento dispara o evento como uma chamada para `Invoke`, os métodos de vtable nunca serão usados e é claro que a interface deve ter sido um dispinterface. Se você definir suas interfaces de evento como duals, você vai exigir que os clientes implementem a parte de uma interface que nunca será usada.

> [!NOTE]
>  Esse argumento não se aplica a interfaces duplas, em geral. Da perspectiva de implementação, duals são uma maneira rápida, conveniente e bem suportada da implementação de interfaces que são acessíveis a uma ampla variedade de clientes.

Há mais razões para evitar interfaces de evento dupla; nem o Visual Basic nem o Internet Explorer dão suporte a eles.

## <a name="see-also"></a>Consulte também

[Interfaces duplas e a ATL](../atl/dual-interfaces-and-atl.md)

