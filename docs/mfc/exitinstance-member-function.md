---
title: Função de membro ExitInstance
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: c76f588b22ad8ffd1d3dae954c5113feffb62a3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405814"
---
# <a name="exitinstance-member-function"></a>Função de membro ExitInstance

O [ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance) função de membro da classe [CWinApp](../mfc/reference/cwinapp-class.md) é chamado sempre que uma cópia do seu aplicativo é encerrado, geralmente como resultado do encerramento do aplicativo de usuário.

Substituir `ExitInstance` se precisar de processamento de limpeza especial, como liberar recursos de interface (GDI) do dispositivo de gráficos ou desalocar a memória usada durante a execução do programa. Limpeza de itens padrão como documentos e exibições, no entanto, é fornecida pela estrutura, com outras funções substituíveis para fazer a limpeza especial específica a esses objetos.

## <a name="see-also"></a>Consulte também

[CWinApp: a classe do aplicativo](../mfc/cwinapp-the-application-class.md)
