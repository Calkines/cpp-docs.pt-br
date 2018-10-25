---
title: Componentes da caixa de diálogo no Framework | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6936a48d1a3e1845d56c73524c84800d9d605155
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065498"
---
# <a name="dialog-box-components-in-the-framework"></a>Componentes da caixa de diálogo no Framework

No framework MFC, uma caixa de diálogo tem dois componentes:

- Um recurso de modelo de caixa de diálogo que especifica os controles da caixa de diálogo e seu posicionamento.

   O recurso de caixa de diálogo armazena um modelo de caixa de diálogo do qual o Windows cria a janela da caixa de diálogo e exibe-o. O modelo especifica as características da caixa de diálogo, incluindo seu tamanho, local, estilo e os tipos e posições dos controles da caixa de diálogo. Você normalmente usará um modelo de caixa de diálogo armazenado como um recurso, mas você também pode criar seu próprio modelo na memória.

- Uma classe de caixa de diálogo, derivada de [CDialog](../mfc/reference/cdialog-class.md), para fornecer uma interface programática para o gerenciamento de caixa de diálogo.

   Uma caixa de diálogo é uma janela e será anexada a uma janela do Windows quando visível. Quando a janela de diálogo é criada, o recurso de modelo de caixa de diálogo é usado como um modelo para a criação de controles de janela da caixa de diálogo de filho.

## <a name="see-also"></a>Consulte também

[Caixas de diálogo](../mfc/dialog-boxes.md)<br/>
[Ciclo de vida de uma caixa de diálogo](../mfc/life-cycle-of-a-dialog-box.md)

