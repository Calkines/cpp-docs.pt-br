---
title: Ilustração de roteamento do comando
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
ms.openlocfilehash: 56d131151f2284f12a3b46a9acd3cfbd3c8b0f47
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304633"
---
# <a name="command-routing-illustration"></a>Ilustração de roteamento do comando

Para ilustrar, considere uma mensagem de comando de um item de menu Limpar tudo no menu de editar um aplicativo MDI. Suponha que a função do manipulador para este comando, por acaso, é uma função de membro de classe de documento do aplicativo. Aqui está como esse comando atinge seu manipulador depois que o usuário escolhe o item de menu:

1. A janela do quadro principal recebe a mensagem de comando pela primeira vez.

1. A janela de quadro MDI principal dá a oportunidade de manipular o comando da janela filho da MDI ativa no momento.

1. O roteamento padrão de uma janela de quadro MDI filho oferece sua exibição a chance no comando antes de verificar seu próprio mapa de mensagem.

1. O modo de exibição verifica primeiro o seu próprio mapa de mensagem e, em seguida é não encontrar nenhum manipulador, encaminha o comando para seu documento associado.

1. O documento verifica seu mapa de mensagem e localiza um manipulador. Essa função de membro de documento é chamada e interrompe o roteamento.

Se o documento não tem um manipulador, em seguida rotearia o comando para seu modelo de documento. Em seguida, o comando retornará para o modo de exibição e, em seguida, a janela do quadro. Por fim, a janela do quadro deve verificar seu mapa de mensagem. Se essa verificação falha, bem, o comando será encaminhado para a janela de quadro MDI principal e, em seguida, para o objeto de aplicativo — o destino final dos comandos sem tratamento.

## <a name="see-also"></a>Consulte também

[Como o Framework chama um manipulador](../mfc/how-the-framework-calls-a-handler.md)
