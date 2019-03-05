---
title: Usando listas de imagens em um controle de caixa de combinação estendido
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], combo boxes
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
ms.openlocfilehash: 6e4d983d53e49fc8d9c80c206f1a23078eb82f61
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266985"
---
# <a name="using-image-lists-in-an-extended-combo-box-control"></a>Usando listas de imagens em um controle de caixa de combinação estendido

O principal recurso de controles de caixa de combinação estendido é a capacidade de associar imagens a partir de uma lista de imagens a itens individuais em um controle de caixa de combinação. Cada item é capaz de exibir três imagens diferentes: um para seu estado selecionado, um para seu estado não selecionado e um terceiro para uma imagem de sobreposição.

O procedimento a seguir associa uma lista de imagens a um controle de caixa de combinação estendido:

### <a name="to-associate-an-image-list-with-an-extended-combo-box-control"></a>Para associar uma lista de imagens com um controle de caixa de combinação estendido

1. Construir uma nova lista de imagens (ou usar um objeto de lista de imagem existente), usando o [CImageList](../mfc/reference/cimagelist-class.md) construtor e armazenar o ponteiro resultante.

1. Inicializar o novo objeto de lista de imagem chamando [CImageList::Create](../mfc/reference/cimagelist-class.md#create). O código a seguir é um exemplo dessa chamada.

   [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_1.cpp)]

1. Adicionar imagens opcionais para cada estado possível: selecionado ou não selecionados e uma sobreposição. O código a seguir adiciona três imagens predefinidas.

   [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_2.cpp)]

1. Associar a lista de imagens com o controle com uma chamada para [CComboBoxEx::SetImageList](../mfc/reference/ccomboboxex-class.md#setimagelist).

Depois que a lista de imagens foi associada com o controle, você pode especificar individualmente as imagens de que cada item será usado para os três estados possíveis. Para obter mais informações, consulte [definindo as imagens para um Item Individual](../mfc/setting-the-images-for-an-individual-item.md).

## <a name="see-also"></a>Consulte também

[Usando CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Controles](../mfc/controls-mfc.md)
