---
title: 'Servidores de automação: Problemas de tempo de vida do objeto'
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], lifetime
- lifetime, automation server
- Automation servers, object lifetime
- servers, lifetime of Automation
ms.assetid: 342baacf-4015-4a0e-be2f-321424f1cb43
ms.openlocfilehash: 74b4bf87b512d35c99942f4aa36174a8673079c5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509191"
---
# <a name="automation-servers-object-lifetime-issues"></a>Servidores de automação: Problemas de tempo de vida do objeto

Quando um cliente de automação cria ou ativa um item OLE, o servidor passa o ponteiro do cliente para esse objeto. O cliente estabelece uma referência ao objeto por meio de uma chamada para a função OLE [IUnknown:: AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref). Essa referência estará em vigor até que o cliente chame [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release). (Os aplicativos cliente escritos com as classes OLE do biblioteca MFC não precisam fazer essas chamadas; a estrutura faz isso.) O sistema OLE e o próprio servidor podem estabelecer referências ao objeto. Um servidor não deve destruir um objeto, desde que as referências externas ao objeto permaneçam em vigor.

A estrutura mantém uma contagem interna do número de referências a qualquer objeto de servidor derivado de [CCmdTarget](../mfc/reference/ccmdtarget-class.md). Essa contagem é atualizada quando um cliente de automação ou outra entidade adiciona ou libera uma referência ao objeto.

Quando a contagem de referência se torna 0, a estrutura chama a função virtual [CCmdTarget:: OnFinalRelease](../mfc/reference/ccmdtarget-class.md#onfinalrelease). A implementação padrão dessa função chama o operador **delete** para excluir esse objeto.

O biblioteca MFC fornece recursos adicionais para controlar o comportamento do aplicativo quando clientes externos têm referências aos objetos do aplicativo. Além de manter uma contagem de referências a cada objeto, os servidores mantêm uma contagem global de objetos ativos. As funções globais [AfxOleLockApp](../mfc/reference/application-control.md#afxolelockapp) e [AfxOleUnlockApp](../mfc/reference/application-control.md#afxoleunlockapp) atualizam a contagem de objetos ativos do aplicativo. Se essa contagem for diferente de zero, o aplicativo não será encerrado quando o usuário escolher fechar no menu do sistema ou sair do menu arquivo. Em vez disso, a janela principal do aplicativo é oculta (mas não destruída) até que todas as solicitações de cliente pendentes tenham sido concluídas. Normalmente, `AfxOleLockApp` e `AfxOleUnlockApp` são chamados nos construtores e destruidores, respectivamente, de classes que dão suporte à automação.

Às vezes, as circunstâncias forçam o servidor a terminar enquanto um cliente ainda tem uma referência a um objeto. Por exemplo, um recurso no qual o servidor depende pode ficar indisponível, fazendo com que o servidor encontre um erro. O usuário também pode fechar um documento de servidor que contém objetos aos quais outros aplicativos têm referências.

Na SDK do Windows, consulte `IUnknown::AddRef` e. `IUnknown::Release`

## <a name="see-also"></a>Consulte também

[Servidores de automação](../mfc/automation-servers.md)<br/>
[AfxOleCanExitApp](../mfc/reference/application-control.md#afxolecanexitapp)
