---
title: "Como a impressão padrão é feita | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- default printing
- printing [MFC], default
- defaults, printing
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5001026f1e5fe9e1fed86a49b0565b09ddd6b555
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="how-default-printing-is-done"></a>Como a impressão padrão é feita
Este artigo explica o processo de impressão padrão no Windows em termos de estrutura MFC.  
  
 Em aplicativos MFC, a classe de exibição tem uma função de membro chamada `OnDraw` que contém todo o código de desenho. `OnDraw`usa um ponteiro para um [CDC](../mfc/reference/cdc-class.md) objeto como um parâmetro. Que `CDC` objeto representa o contexto de dispositivo para receber a imagem produzida por `OnDraw`. Quando a janela de exibição do documento recebe um [WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) da mensagem, a estrutura chama `OnDraw` e transmite um contexto de dispositivo para a tela (um [CPaintDC](../mfc/reference/cpaintdc-class.md) objeto, seja específico). Da mesma forma, `OnDraw`saída vai para a tela.  
  
 Na programação do Windows, enviando a saída para a impressora é muito semelhante ao envio de saída para a tela. Isso ocorre porque a interface de dispositivo de gráficos (GDI) do Windows é independente de hardware. Você pode usar as mesmas funções GDI para tela ou para impressão usando o contexto de dispositivo apropriados. Se o `CDC` o objeto `OnDraw` recebe representa a impressora `OnDraw`saída vai para a impressora.  
  
 Explica como aplicativos MFC podem executar a impressão simple sem a necessidade de esforço extra de sua parte. A estrutura se encarrega de exibir a caixa de diálogo de impressão e criar um contexto de dispositivo para a impressora. Quando o usuário seleciona o comando Imprimir do menu Arquivo, o modo de exibição passa este contexto de dispositivo para `OnDraw`, que desenha o documento na impressora.  
  
 No entanto, há algumas diferenças significativas entre a exibição de tela e da impressão. Quando você imprime, você precisa dividir o documento em páginas distintas e -los um por vez, em vez de exibir qualquer parte é visível em uma janela de exibição. Como resultado, você precisa estar ciente do tamanho do papel (se for tamanho de carta, legais ou um envelope). Convém imprimir em diferentes orientações, como o modo de paisagem ou retrato. A biblioteca Microsoft Foundation Class não pode prever como seu aplicativo tratará esses problemas, portanto, ele fornece um protocolo para adicionar esses recursos.  
  
 Se o protocolo é descrito no artigo [Multipage documentos](../mfc/multipage-documents.md).  
  
## <a name="see-also"></a>Consulte também  
 [Imprimindo](../mfc/printing.md)
