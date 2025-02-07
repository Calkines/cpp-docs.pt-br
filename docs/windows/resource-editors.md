---
title: Editores de recursos (C++)
ms.date: 02/14/2019
f1_keywords:
- vs.editors.resource
- vc.resvw.resource.editors
- vs.resvw.resource.editors
- vs.resourceview
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
helpviewer_keywords:
- editors [C++], resource
- editors [C++]
- resource editors
- Windows [C++], application resource editing
- resources [C++], viewing
- layouts, previewing resource
- resource editors [C++], viewing resources
- .rc files [C++], viewing resources
- resources [C++], editing
- properties [C++], resources
- resources [C++], properties
ms.assetid: e20a29ec-d6fb-4ead-98f3-431a0e23aaaf
ms.openlocfilehash: 850d4b72ddb45551528526cd9e02345aee74d751
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344223"
---
# <a name="resource-editors-c"></a>Editores de recursos (C++)

Um editor de recursos é um ambiente especializado para criar ou modificar os recursos que estão incluídos em um projeto do Visual Studio. Os editores de recursos do Visual Studio compartilham técnicas e interfaces para ajudá-lo a criar e modificar recursos do aplicativo de forma rápida e fácil. Editores de recursos permitem que você exiba e edite recursos nos recursos apropriados do editor e versão prévia.

O editor apropriado é aberto automaticamente quando você criar ou abrir um recurso.

> [!NOTE]
> Porque os projetos gerenciados não usam arquivos de script de recurso, você deve abrir seus recursos do **Gerenciador de soluções**. Você pode usar o [Editor de imagens](../windows/image-editor-for-icons.md) e o [Editor binário](binary-editor.md) para trabalhar com arquivos de recursos em projetos gerenciados. Todos os recursos gerenciados que você deseja editar devem ser recursos vinculados. Os editores de recursos do Visual Studio não oferecem suporte à edição de recursos inseridos.

|Use o...|Para editar...|
|----------------|----------------|
|[Editor de aceleradores](../windows/accelerator-editor.md)|Tabelas de aceleradores no Visual Studio C++ projetos.|
|[Editor binário](binary-editor.md)|Informações de dados binários e recursos personalizados em projetos do Visual C++, Visual Basic ou Visual c#.|
|[Editor de caixa de diálogo](../windows/dialog-editor.md)|Caixas de diálogo do Visual Studio C++ projetos.|
|[Editor de Imagens](../windows/image-editor-for-icons.md)|Bitmaps, ícones, cursores e outros arquivos de imagem em projetos do Visual C++, Visual Basic ou Visual c#.|
|[Editor de Menu](../windows/menu-editor.md)|Recursos de menu no Visual Studio C++ projetos.|
|[Ribbon Editor](../mfc/ribbon-designer-mfc.md)|Recursos de faixa de opções em projetos MFC.|
|[Editor de cadeias de caracteres](../windows/string-editor.md)|Tabelas no Visual Studio de cadeia de caracteres C++ projetos.|
|[Editor de barra de ferramentas](../windows/toolbar-editor.md)|Recursos da barra de ferramentas no Visual Studio C++ projetos. O **barra de ferramentas do Editor** faz parte do **Editor de imagens**.|
|[Editor de informações de versão](../windows/version-information-editor.md)|Informações de versão no Visual Studio C++ projetos.|

> [!NOTE]
> Se seu projeto já não contiver um arquivo. RC, consulte [como: Criar recursos](../windows/how-to-create-a-resource-script-file.md).

## <a name="view-and-edit-resources"></a>Modo de exibição e edição de recursos

Cada tipo de recurso tem um editor de recursos específico para esse tipo de recurso. Você pode reorganizar, redimensionar, adicionar controles e recursos ou caso contrário, modificar os aspectos de um recurso usando o editor associado. Você também pode editar um recurso no [formato de texto](../windows/how-to-open-a-resource-script-file-in-text-format.md) e [formato binário](../windows/opening-a-resource-for-binary-editing.md).

Alguns tipos de recurso são arquivos individuais que podem ser importados e usados de várias maneiras; Isso inclui bitmaps, ícones, cursores, barras de ferramentas e arquivos html. Esses recursos têm nomes de arquivo e [identificadores de recurso](../windows/symbols-resource-identifiers.md). Outros, como caixas de diálogo, menus e tabelas de cadeia de caracteres em projetos do Win32, existem apenas como parte de um arquivo de script (. rc) do recurso ou o arquivo de modelo (. rct) do recurso.

Os recursos também podem ser editados fora do projeto sem a necessidade de abrir o projeto, consulte [como: Criar recursos](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

> [!NOTE]
> Propriedades de um recurso podem ser modificadas usando o **propriedades** janela.

- Para editar as propriedades de um recurso, na [exibição de recurso](how-to-create-a-resource-script-file.md#create-resources), com o recurso que você deseja editar e escolha o botão direito **propriedades**.  Em seguida, nos [janela de propriedades](/visualstudio/ide/reference/properties-window), alterar as propriedades do recurso.

- Para desfazer uma alteração feita nas propriedades de um recurso, verifique se o recurso tem o foco no **exibição de recurso** e escolha **desfazer** do **editar** menu.

### <a name="win32-resources"></a>Recursos do Win32

Você pode acessar os recursos do Win32 na [exibição de recurso](how-to-create-a-resource-script-file.md#create-resources) painel.

#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>Para exibir um recurso do Win32 em um editor de recursos

1. Vá ao menu **modo de exibição** > **exibição de recurso**.

1. Se o **exibição de recurso** janela não é a janela principal, selecione o **exibição de recurso** guia para colocá-lo na parte superior.

1. Partir **exibição de recurso**, expanda a pasta do projeto que contém os recursos que você deseja exibir. Por exemplo, se você quiser exibir um recurso de caixa de diálogo, expanda o **caixa de diálogo** pasta.

1. Clique duas vezes no recurso, por exemplo, **IDD_ABOUTBOX**.

   O recurso é aberto no editor apropriado. Por exemplo, para recursos de caixa de diálogo, o recurso é aberto dentro do **Editor de caixa de diálogo**.

#### <a name="to-delete-an-existing-win32-resource"></a>Para excluir um recurso existente do Win32

1. Na **exibição de recurso**, expanda o nó para um tipo de recurso.

1. Clique com botão direito no recurso que você deseja excluir e escolha **excluir**.

> [!TIP]
> Você também pode usar esse método quando você tem o arquivo. rc abrir em uma janela de documento fora de um projeto.

### <a name="managed-project-resources"></a>Recursos de projeto gerenciado

Como os projetos gerenciados não usam arquivos de script de recurso, você deve abrir seus recursos do **Gerenciador de soluções**. Use o [Editor de imagens](../windows/image-editor-for-icons.md) e o [Editor binário](binary-editor.md) para trabalhar com arquivos de recursos em projetos gerenciados. Todos os recursos gerenciados que deseja editar devem ser recursos vinculados e editores de recursos do Visual Studio não oferecem suporte a edição de recursos inseridos.

- Para exibir um recurso gerenciado em um editor de recursos, no **Gerenciador de soluções**, clique duas vezes no recurso, por exemplo, *Bitmap1.bmp*, e o recurso é aberto no editor apropriado.

- Para excluir um recurso gerenciado existente no **Gerenciador de soluções**, com o recurso que deseja excluir e escolha o botão direito **excluir**.

## <a name="preview-resources"></a>Recursos de visualização

Visualize seus recursos para que você possa exibir recursos gráficos sem abri-los. Visualizando também é útil para executáveis depois que você tenha compilado, porque os identificadores de recurso Alterar para números. Pois esses identificadores numéricos geralmente não fornecem informações suficientes, visualizando os recursos ajuda a identificar rapidamente-los.

Os tipos de recursos a seguir fornecem uma visualização do layout visual: Bitmap, caixa de diálogo, ícone, Menu, Cursor, barra de ferramentas

Os seguintes recursos não fornecem uma visualização visual: Acelerador, informações de versão do manifesto, tabela de cadeia de caracteres

> [!NOTE]
> Para visualizar recursos requer Win32.

### <a name="to-preview-resources"></a>Para visualizar os recursos

1. Na [exibição de recurso](how-to-create-a-resource-script-file.md#create-resources) ou uma janela de documento, selecione o recurso, por exemplo, **IDD_ABOUTBOX**.

1. No [janela de propriedades](/visualstudio/ide/reference/properties-window), selecione o **páginas de propriedade** botão.

   > [!TIP]
   > Usar um atalho, vá ao menu **modo de exibição** > **páginas de propriedade**.

   O **propriedade** página para o recurso é aberta exibindo uma visualização desse recurso. Você pode usar o **para cima** e **para baixo** teclas de direção para navegar na árvore de controle na **exibição de recurso** ou a janela do documento. O **propriedade** página permanecer aberta e mostrar qualquer recurso que tem o foco e pode ser visualizado.

## <a name="requirements"></a>Requisitos

Nenhum

## <a name="see-also"></a>Consulte também

[Trabalhando com arquivos de recurso](../windows/working-with-resource-files.md)<br/>
[Arquivos de recurso](../windows/resource-files-visual-studio.md)<br/>
[Identificadores de recursos (símbolos)](../windows/symbols-resource-identifiers.md)<br/>