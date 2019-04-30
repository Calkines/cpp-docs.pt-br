---
title: Classes de janela com moldura (arquitetura)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], document/view architecture
ms.assetid: 5da01fb4-f531-46cc-914f-e422e4f07f5d
ms.openlocfilehash: affa217f481cc6d9e125d526f1b97be9120e0990
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392837"
---
# <a name="frame-window-classes-architecture"></a>Classes de janela com moldura (arquitetura)

Arquitetura de exibição de documentos, janelas com moldura são janelas que contêm uma janela de exibição. Eles também dão suporte a ter controle barras anexadas a eles.

Em vários aplicativos MDI (interface MDI) de documento, a janela principal é derivada de `CMDIFrameWnd`. Ele contém indiretamente quadros dos documentos, que são `CMDIChildWnd` objetos. O `CMDIChildWnd` objetos, por sua vez, contêm modos de exibição de documentos.

Em aplicativos de interface (SDI) único documento, a janela principal, derivada de `CFrameWnd`, contém a exibição do documento atual.

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
A classe base para a janela do quadro principal de um aplicativo SDI. Também é a classe base para todas as outras classes de janela de quadro.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
A classe base para a janela do quadro principal de um aplicativo MDI.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
A classe base para janelas de quadro do documento de um aplicativo MDI.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Fornece a janela do quadro para um modo de exibição quando um documento do servidor está sendo editado no local.

## <a name="see-also"></a>Consulte também

[Visão geral da classe](../mfc/class-library-overview.md)
