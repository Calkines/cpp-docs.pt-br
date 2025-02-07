---
title: Usando uma lista de imagens
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
ms.openlocfilehash: cb95de134939e1b06e2a8b827424c986f8c48ef3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180460"
---
# <a name="using-an-image-list"></a>Usando uma lista de imagens

Um uso típico de uma lista de imagens segue o padrão abaixo:

- Construir uma [CImageList](../mfc/reference/cimagelist-class.md) do objeto e chame uma das sobrecargas de seus [Create](../mfc/reference/cimagelist-class.md#create) função para criar uma lista de imagens e anexá-lo para o `CImageList` objeto.

- Se você não adicionar imagens ao criar a lista de imagens, adicionar imagens à lista de imagens por meio da chamada a [Add](../mfc/reference/cimagelist-class.md#add) ou [leitura](../mfc/reference/cimagelist-class.md#read) função de membro.

- Associar a lista de imagens com um controle, chamando a função de membro apropriado desse controle ou desenhar imagens da lista de imagens por conta própria usando a lista de imagens [desenhar](../mfc/reference/cimagelist-class.md#draw) função de membro.

- Talvez, permitir que o usuário arrasta uma imagem, usando o suporte interno a da lista de imagens para serem arrastados.

> [!NOTE]
>  Se a lista de imagens foi criada com o **novos** operador, você deve destruir a `CImageList` objeto quando você terminar com ele.

## <a name="see-also"></a>Consulte também

[Usando CImageList](../mfc/using-cimagelist.md)<br/>
[Controles](../mfc/controls-mfc.md)
