---
title: Usando listas de imagens com controles de cabeçalho
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
ms.openlocfilehash: 3d9a4a0c655fa46c15d8c4d9b2b4e90cd34c2937
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411533"
---
# <a name="using-image-lists-with-header-controls"></a>Usando listas de imagens com controles de cabeçalho

Itens de cabeçalho têm a capacidade de exibir uma imagem dentro de um item de cabeçalho. Essa imagem, armazenada em uma lista de imagens associado, é 16 x 16 pixels e tem as mesmas características que as imagens de ícone usadas em um controle de exibição de lista. Para implementar esse comportamento com êxito, primeiro crie e inicialize a lista de imagens, associar a lista de controle de cabeçalho e, em seguida, modifique os atributos do item de cabeçalho que exibirá a imagem.

O procedimento a seguir ilustra os detalhes, usando um ponteiro para um controle de cabeçalho (`m_pHdrCtrl`) e um ponteiro para uma lista de imagens (`m_pHdrImages`).

### <a name="to-display-an-image-in-a-header-item"></a>Para exibir uma imagem em um item de cabeçalho

1. Construir uma nova lista de imagens (ou usar um objeto de lista de imagem existente) usando o [CImageList](../mfc/reference/cimagelist-class.md) construtor, armazenando o ponteiro resultante.

1. Inicializar o novo objeto de lista de imagem chamando [CImageList::Create](../mfc/reference/cimagelist-class.md#create). O código a seguir é um exemplo dessa chamada.

   [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. Adicione as imagens para cada item de cabeçalho. O código a seguir adiciona duas imagens predefinidas.

   [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. Associar a lista de imagens com o controle de cabeçalho com uma chamada para [CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist).

1. Modifica o item de cabeçalho para exibir uma imagem da lista de imagens associado. O exemplo a seguir atribui a primeira imagem, de `m_phdrImages`, para o primeiro item de cabeçalho, `m_pHdrCtrl`.

   [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

Para obter informações detalhadas sobre os valores de parâmetro usados, consulte o pertinentes [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md).

> [!NOTE]
>  É possível ter vários controles usando a mesma lista de imagens. Por exemplo, um controle de exibição de lista padrão, pode haver uma lista de imagens (16 x 16 pixels de imagens de) usada pela exibição de ícone pequeno de um controle de exibição de lista e os itens de cabeçalho do controle de exibição de lista.

## <a name="see-also"></a>Consulte também

[Usando CHeaderCtrl](../mfc/using-cheaderctrl.md)
