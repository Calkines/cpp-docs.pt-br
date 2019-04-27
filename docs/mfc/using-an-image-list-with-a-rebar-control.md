---
title: Usando uma lista de imagens com um controle rebar
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
ms.openlocfilehash: fa5307c201850fc42439c79a1c638a0707379913
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180486"
---
# <a name="using-an-image-list-with-a-rebar-control"></a>Usando uma lista de imagens com um controle rebar

Cada faixa de rebar pode conter, entre outras coisas, uma imagem de uma lista de imagens associado. O procedimento a seguir detalha as etapas necessárias para exibir uma imagem em uma faixa de rebar.

### <a name="to-display-images-in-a-rebar-band"></a>Para exibir imagens em uma faixa de rebar

1. Anexar uma lista de imagens no seu objeto de controle rebar, fazendo uma chamada para [SetImageList](../mfc/reference/crebarctrl-class.md#setimagelist), passando um ponteiro para uma lista de imagens existente.

1. Modificar a **REBARBANDINFO** estrutura para atribuir uma imagem para uma faixa de rebar:

   - Defina as *fMask* membro `RBBIM_IMAGE`, usando o operador OR bit a bit para incluir os sinalizadores adicionais conforme necessário.

   - Defina as *iImage* membro para o índice de lista de imagens da imagem a ser exibida.

1. Inicialize quaisquer membros de dados restantes, como o tamanho, o texto e o identificador da janela filho independente, com as informações necessárias.

1. Inserir a nova faixa (com a imagem) com uma chamada para [CReBarCtrl::InsertBand](../mfc/reference/crebarctrl-class.md#insertband), passando o **REBARBANDINFO** estrutura.

O exemplo a seguir pressupõe que um objeto de lista de imagem existente com duas imagens foi anexado ao objeto de controle rebar (`m_wndReBar`). Uma nova faixa de rebar (definido por `rbi`), que contém a primeira imagem, que é adicionado com uma chamada para `InsertBand`:

[!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]

## <a name="see-also"></a>Consulte também

[Usando CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
