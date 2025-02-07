---
title: Relacionamento com a API da linguagem C
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
ms.openlocfilehash: 8601dd034dbd73ac035084ad57c51f62e333fd32
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511858"
---
# <a name="relationship-to-the-c-language-api"></a>Relacionamento com a API da linguagem C

A característica única que define a biblioteca MFC (Microsoft Foundation Class) de outras bibliotecas de classes para o Windows é o mapeamento muito próximo para a API do Windows escrita na linguagem C. Além disso, geralmente é possível misturar chamadas para a biblioteca de classes livremente com chamadas diretas para a API do Windows. No entanto, esse acesso direto não implica que as classes sejam uma substituição completa para essa API. Os desenvolvedores ainda devem, ocasionalmente, fazer chamadas diretas para algumas funções do Windows, como [SetCursor](/windows/win32/api/winuser/nf-winuser-setcursor) e [GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics), por exemplo. Uma função do Windows é encapsulada por uma função membro de classe somente quando há uma vantagem clara de fazer isso.

Como às vezes você precisa fazer chamadas de função nativas do Windows, deve ter acesso à documentação da API do Windows em linguagem C. Esta documentação está incluída no Microsoft Visual C++.

> [!NOTE]
>  Para obter uma visão geral de como funciona a estrutura de biblioteca do MFC, consulte [usando as classes para escrever aplicativos para o Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

## <a name="see-also"></a>Consulte também

[Filosofia de design da classe geral](../mfc/general-class-design-philosophy.md)
