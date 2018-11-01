---
title: Definindo variáveis de membro para controles de caixa de diálogo (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog Editor [C++], defining member variables for controls
ms.assetid: 84347c63-c33c-4b04-91f5-6d008c45ba58
ms.openlocfilehash: 56a7d01d26656c8cf9def3bf09e3ccb18fb436fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449446"
---
# <a name="defining-member-variables-for-dialog-controls-c"></a>Definindo variáveis de membro para controles de caixa de diálogo (C++)

Para definir uma variável de membro de qualquer controle de caixa de diálogo, exceto os botões, você pode usar o método a seguir.

> [!NOTE]
> Este artigo se aplica somente a controles de caixa de diálogo dentro de um projeto MFC. Projetos ATL devem usar o **novas mensagens do Windows e manipuladores de eventos** caixa de diálogo.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>Para definir uma variável de membro para um controle de caixa de diálogo (não-botão)

1. No [editor de caixa de diálogo](../windows/dialog-editor.md), selecione um controle.

2. Ao pressionar o **Ctrl** da chave, clique duas vezes o controle de caixa de diálogo.

   O [assistente Adicionar variável de membro](../ide/add-member-variable-wizard.md) é exibida.

3. Digite as informações apropriadas na **Adicionar variável de membro** assistente. Para obter mais informações, consulte [troca de dados de caixa de diálogo](../mfc/dialog-data-exchange.md).

4. Clique em **Okey** para retornar para o **caixa de diálogo** editor.

   > [!TIP]
   > Para saltar de qualquer controle de caixa de diálogo para seu manipulador existente, clique duas vezes no controle.

Você também pode usar o **variáveis de membro** guia **MFC Class Wizard** para adicionar novas variáveis de membro para uma classe especificada e exibir os que já foi definido.

## <a name="requirements"></a>Requisitos

MFC

## <a name="see-also"></a>Consulte também

[Mapeando mensagens para funções](../mfc/reference/mapping-messages-to-functions.md)<br/>
[Adicionando funcionalidade com assistentes de código](../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Assistente de classe do MFC](../mfc/reference/mfc-class-wizard.md)<br/>
[Adicionando uma classe](../ide/adding-a-class-visual-cpp.md)<br/>
[Adicionando uma função de membro](../ide/adding-a-member-function-visual-cpp.md)<br/>
[Adicionando uma variável de membro](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Substituindo uma função virtual](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Manipulador de mensagens do MFC](../mfc/reference/adding-an-mfc-message-handler.md)