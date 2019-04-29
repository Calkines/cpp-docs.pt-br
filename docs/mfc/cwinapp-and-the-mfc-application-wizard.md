---
title: CWinApp e o Assistente de Aplicativo MFC
ms.date: 11/04/2016
f1_keywords:
- CWinApp
helpviewer_keywords:
- application wizards [MFC], and CWinApp
- CWinApp class [MFC], and MFC Application Wizard
- MFC, wizards
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
ms.openlocfilehash: cb45c8ffae15628b0b99a1ebcd962d88d845f83b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241570"
---
# <a name="cwinapp-and-the-mfc-application-wizard"></a>CWinApp e o Assistente de Aplicativo MFC

Quando ele cria um aplicativo de esqueleto, o Assistente de aplicativo do MFC declara uma classe de aplicativo derivada de [CWinApp](../mfc/reference/cwinapp-class.md). O Assistente de aplicativo do MFC também gera um arquivo de implementação que contém os seguintes itens:

- Um mapa de mensagem para a classe de aplicativo.

- Um construtor de classe vazia.

- Uma variável que declara um e apenas o objeto da classe.

- Uma implementação padrão de seu `InitInstance` função de membro.

A classe do aplicativo é colocada no cabeçalho do projeto e arquivos de origem principal. Os nomes da classe e os arquivos criados são baseados no nome do projeto que você fornecer no Assistente de aplicativo MFC. A maneira mais fácil para exibir o código para essas classes é por meio [modo de exibição de classe](/visualstudio/ide/viewing-the-structure-of-code).

O mapa de mensagem fornecida e implementações padrão são adequadas para muitas finalidades, mas você pode modificá-los conforme necessário. Essas implementações mais interessantes é a `InitInstance` função de membro. Normalmente, você adicionará código para a implementação de esqueleto de `InitInstance`.

## <a name="see-also"></a>Consulte também

[CWinApp: a classe do aplicativo](../mfc/cwinapp-the-application-class.md)<br/>
[Funções de membro CWinApp substituíveis](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Serviços CWinApp especiais](../mfc/special-cwinapp-services.md)
