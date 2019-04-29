---
title: Recomendações para escolher entre ATL e MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
ms.openlocfilehash: e4e51f81bbdc54ff09980acfba22037df77abac9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261332"
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>Recomendações para escolher entre ATL e MFC

Ao desenvolver aplicativos e componentes, você pode escolher entre duas abordagens — ATL e MFC (a biblioteca Microsoft Foundation Class).

## <a name="using-atl"></a>Usando ATL

ATL é uma maneira rápida e fácil para criar um componente COM em C++ e manter uma superfície pequena. Use a ATL para criar um controle se não precisar de toda a funcionalidade interna que MFC fornece automaticamente.

## <a name="using-mfc"></a>Usando o MFC

MFC permite que você crie aplicativos completos, controles ActiveX e documentos ativos. Se você já tiver criado um controle com o MFC, você talvez queira continuar o desenvolvimento no MFC. Ao criar um novo controle, considere o uso da ATL, se você não precisa de todos de uma funcionalidade interna do MFC.

## <a name="using-atl-in-an-mfc-project"></a>Usando ATL em um projeto MFC

Você pode adicionar suporte para o uso de ATL em um projeto MFC existente executando um assistente. Para obter detalhes, consulte [adicionando o suporte ATL ao seu projeto do MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

## <a name="see-also"></a>Consulte também

[Introdução à ATL](../atl/introduction-to-atl.md)
