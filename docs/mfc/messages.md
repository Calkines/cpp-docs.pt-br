---
title: Mensagens
ms.date: 11/04/2016
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
ms.openlocfilehash: 8e1bfd1baa8ffef76ba31912fc619c4217696683
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384121"
---
# <a name="messages"></a>Mensagens

O loop de mensagem na `Run` função de membro da classe `CWinApp` recupera na fila de mensagens geradas por vários eventos. Por exemplo, quando o usuário clica com o mouse, o Windows envia várias mensagens relacionados ao mouse, como WM_LBUTTONDOWN quando o botão esquerdo do mouse é pressionado e WM_LBUTTONUP quando o botão esquerdo do mouse é liberado. A implementação da estrutura de loop de mensagem do aplicativo expede a mensagem na janela apropriada.

As categorias importantes de mensagens são descritas em [categorias de mensagem](../mfc/message-categories.md).

## <a name="see-also"></a>Consulte também

[Mensagens e comandos no Framework](../mfc/messages-and-commands-in-the-framework.md)
