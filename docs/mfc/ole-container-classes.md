---
title: Classes Container OLE
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
ms.openlocfilehash: 87db824e5ab4daec15870b245ea8341be7442109
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292537"
---
# <a name="ole-container-classes"></a>Classes Container OLE

Essas classes são usadas por aplicativos de contêiner. Ambos `COleLinkingDoc` e `COleDocument` gerenciar coleções de `COleClientItem` objetos. Em vez de derivar de sua classe de documento de `CDocument`, você vai derive-a da `COleLinkingDoc` ou `COleDocument`, dependendo se você quiser suporte para obter links para os objetos inseridos no documento.

Use um `COleClientItem` objeto para representar cada item OLE no documento que é incorporado a partir de outro documento ou é um link para outro documento.

[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)<br/>
Dá suporte a contenção de documento ativo.

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
Usado para a implementação de documento composto, bem como suporte a contêiner básico. Serve como um contêiner para as classes derivadas de `CDocItem`. Essa classe pode ser usada como a classe base para o contêiner de documentos e é a classe base para `COleServerDoc`.

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
Uma classe derivada de `COleDocument` que fornece a infraestrutura para vinculação. Você deve derivar as classes de documento para seus aplicativos de contêiner a partir dessa classe em vez de partir `COleDocument` se você deseja dar suporte a links para os objetos inseridos.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Mantém a lista de itens de cliente OLE que estão no controle de edição rica. Usado com [CRichEditView](../mfc/reference/cricheditview-class.md) e [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Classe abstrata base de `COleClientItem` e `COleServerItem`. Objetos de classes derivados de `CDocItem` representam as partes de documentos.

[COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
Uma classe de item do cliente que representa o lado do cliente da conexão a um item OLE inserido ou vinculado. Derive seus itens de cliente dessa classe.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Fornece acesso de cliente para uma item armazenada em um controle de edição rico quando usado com OLE `CRichEditView` e `CRichEditDoc`.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Uma exceção resultante de uma falha no processamento de OLE. Essa classe é usada por contêineres e servidores.

## <a name="see-also"></a>Consulte também

[Visão geral da classe](../mfc/class-library-overview.md)
