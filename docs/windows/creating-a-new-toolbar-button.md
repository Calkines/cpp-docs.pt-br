---
title: Criando um novo botão de barra de ferramentas (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.toolbar
helpviewer_keywords:
- Toolbar editor [C++], creating buttons
- toolbar buttons [C++], button image
- toolbar buttons [C++], creating
- toolbar buttons (in Toolbar editor)
ms.assetid: 46c120fe-4f2a-4887-a08f-bd1fea04b3f4
ms.openlocfilehash: 1fe3e960ea9d2cec36e1c0d1ee9edb30bcc354d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512496"
---
# <a name="creating-a-new-toolbar-button-c"></a>Criando um novo botão de barra de ferramentas (C++)

### <a name="to-create-a-new-toolbar-button"></a>Para criar um novo botão de barra de ferramentas

1. Na [exibição de recurso](../windows/resource-view-window.md) expanda a pasta de recurso (por exemplo, Project1.rc).

   > [!NOTE]
   > Se seu projeto já não contiver um arquivo. RC, consulte [criando um novo arquivo de Script de recurso](../windows/how-to-create-a-resource-script-file.md).

2. Expanda o **barra de ferramentas** pasta e selecione uma barra de ferramentas para editar.

3. Atribua uma ID para o botão em branco na extremidade direita da barra de ferramentas. Você pode fazer isso editando o **ID** propriedade no [janela propriedades](/visualstudio/ide/reference/properties-window). Por exemplo, você talvez queira dar a mesma ID de uma opção de menu a um botão de barra de ferramentas. Nesse caso, use a caixa de listagem suspensa para selecionar o **ID** da opção de menu.

   -ou-

   Selecione o botão em branco na extremidade direita da barra de ferramentas (na **modo de exibição da barra de ferramentas** painel) e começar a desenhar. Uma ID de comando do botão padrão é atribuída (ID_BUTTON\<n >).

Você pode, também, copiar e colar uma imagem em uma barra de ferramentas, como um novo botão.

### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Para adicionar uma imagem para uma barra de ferramentas, como um botão

1. Na [exibição de recurso](../windows/resource-view-window.md), abra a barra de ferramentas clicando duas vezes nele.

2. Em seguida, abra a imagem que você deseja adicionar à barra de ferramentas.

   > [!NOTE]
   > Se você abrir a imagem no Visual Studio, ele será aberto na **imagem** editor. Você também pode abrir a imagem em outros programas de elementos gráficos.

3. Dos **edite** menu, escolha **cópia**.

4. Alterne para sua barra de ferramentas clicando na guia na parte superior da janela de origem.

5. Dos **edite** menu, escolha **colar**.

   A imagem será exibida na barra de ferramentas, como um novo botão.

Para obter informações sobre como adicionar recursos a projetos gerenciados, consulte [recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index) na *guia do desenvolvedor do .NET Framework*. Para obter informações sobre como adicionar manualmente os arquivos de recursos a projetos gerenciados, acessar recursos, exibir recursos estáticos e atribuir cadeias de caracteres de recurso a propriedades, consulte [criando arquivos de recursos para aplicativos de área de trabalho](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obter informações sobre globalização e localização de recursos em aplicativos gerenciados, consulte [Globalizing e Localizando aplicativos do .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

MFC ou ATL

## <a name="see-also"></a>Consulte também

[Propriedades do botão de barra de ferramentas](../windows/toolbar-button-properties.md)<br/>
[Criando, movendo e editando botões da barra de ferramentas](../windows/creating-moving-and-editing-toolbar-buttons.md)<br/>
[Editor de barra de ferramentas](../windows/toolbar-editor.md)