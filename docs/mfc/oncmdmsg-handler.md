---
title: Manipulador OnCmdMsg
ms.date: 11/04/2016
f1_keywords:
- OnCmdMsg
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
ms.openlocfilehash: 6ed2e4c09e2fe413d29ad9953dbb8a03c106e86c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385278"
---
# <a name="oncmdmsg-handler"></a>Manipulador OnCmdMsg

Para fazer o roteamento de comandos, cada destino do comando chama o `OnCmdMsg` função de membro de destino do comando Avançar na sequência. Comando destina-se usar `OnCmdMsg` para determinar se eles podem lidar com um comando e encaminhá-lo para outro destino de comando se ele não podem lidar com eles.

Cada classe de destino do comando pode substituir o `OnCmdMsg` função de membro. As substituições permitem que os comandos de rota cada classe para um destino específico de Avançar. Uma janela do quadro, por exemplo, sempre roteia comandos em sua janela filho da atual ou o modo de exibição, conforme mostrado na tabela [rota de comando padrão](../mfc/command-routing.md).

O padrão `CCmdTarget` implementação de `OnCmdMsg` usa o mapa da mensagem da classe de destino de comando para procurar por uma função de manipulador para cada mensagem de comando, ele recebe — da mesma forma que as mensagens padrão serão pesquisadas. Se ele encontrar uma correspondência, ele chama o manipulador. Pesquisa de mapa de mensagem é explicado em [como o Framework pesquisa mapas de mensagem](../mfc/how-the-framework-searches-message-maps.md).

## <a name="see-also"></a>Consulte também

[Como o Framework chama um manipulador](../mfc/how-the-framework-calls-a-handler.md)
