---
title: Criando uma dica de ferramenta para um botão de barra de ferramentas (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [C++], adding to toolbar buttons
- "\nin tool tip"
- toolbar buttons [C++], tool tips
- buttons [C++], tool tips
- Toolbar editor [C++], creating tool tips
ms.assetid: 0af65342-fd78-4e78-8d0d-dc68f7fc462e
ms.openlocfilehash: 9179dfcc47f69b9f5db131467f0216da6363085c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557996"
---
# <a name="creating-a-tool-tip-for-a-toolbar-button-c"></a>Criando uma dica de ferramenta para um botão de barra de ferramentas (C++)

### <a name="to-create-a-tool-tip"></a>Para criar uma dica de ferramenta

1. Selecione o botão de barra de ferramentas.

2. No [janela de propriedades](/visualstudio/ide/reference/properties-window), no **Prompt** campo de propriedade, adicione uma descrição do botão de barra de status; após a mensagem, adicione `\n` e o nome de dica de ferramenta.

Um exemplo comum de uma dica de ferramenta é o **Print** botão na **WordPad**:

1. Abra **WordPad**.

2. Passe o ponteiro do mouse sobre o **impressão** botão da barra de ferramentas.

3. Observe que a palavra `Print` agora está flutuando sob o ponteiro do mouse.

4. Observe a barra de status (na parte inferior do **WordPad** janela)-Observe que ele agora mostra o texto `Prints the active document`.

O `Print` na **etapa 3** é o "nome de dica de ferramenta" e o `Prints the active document` da **etapa 4** é a "Descrição do botão da barra de status de".

Se você quiser que esse efeito usando o **barra de ferramentas** editor, defina as **Prompt** propriedade `Prints the active document\nPrint`.

> [!NOTE]
> Você pode editar o texto de aviso usando o [janela de propriedades](/visualstudio/ide/reference/properties-window).

Para obter informações sobre como adicionar recursos a projetos gerenciados, consulte [recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index) na *guia do desenvolvedor do .NET Framework*. Para obter informações sobre como adicionar manualmente os arquivos de recursos a projetos gerenciados, acessar recursos, exibir recursos estáticos e atribuir cadeias de caracteres de recurso a propriedades, consulte [criando arquivos de recursos para aplicativos de área de trabalho](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obter informações sobre globalização e localização de recursos em aplicativos gerenciados, consulte [Globalizing e Localizando aplicativos do .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

MFC ou ATL

## <a name="see-also"></a>Consulte também

[Criando, movendo e editando botões da barra de ferramentas](../windows/creating-moving-and-editing-toolbar-buttons.md)<br/>
[Editor de barra de ferramentas](../windows/toolbar-editor.md)