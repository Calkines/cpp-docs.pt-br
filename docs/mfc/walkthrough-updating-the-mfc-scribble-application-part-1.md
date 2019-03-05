---
title: 'Passo a passo: Atualizando o aplicativo de rabisco MFC (parte 1)'
ms.date: 09/20/2018
helpviewer_keywords:
- examples [MFC], update existing application
- ribbon UI, porting to
- Office Fluent UI, porting to
- samples [MFC], update existing application
- MFC Feature Pack, update existing application
- walkthroughs [MFC], update existing application
ms.assetid: aa6330d3-6cfc-4c79-8fcb-0282263025f7
ms.openlocfilehash: 213bc8087b58eac232cc8fcfccc88e13785a807e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258756"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-1"></a>Passo a passo: Atualizando o aplicativo de rabisco MFC (parte 1)

Este passo a passo demonstra como modificar um aplicativo MFC existente para usar a interface do usuário da faixa de opções. Visual Studio oferece suporte a faixa de opções do Office 2007 e o Windows 7 Scenic Ribbon. Para obter mais informações sobre a interface do usuário da faixa de opções, consulte [faixas de opções](/windows/desktop/uxguide/cmd-ribbons).

Este passo a passo modifica o exemplo de rabisco MFC de 1.0 clássico que permite que você use o mouse para criar desenhos de linha. Esta parte do passo a passo mostra como modificar o exemplo de Scribble, para que ele exibe uma barra de faixa de opções. [Parte 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md) adiciona mais botões à barra de faixa de opções.

## <a name="prerequisites"></a>Pré-requisitos

O [exemplo de rabisco MFC de 1.0](http://download.microsoft.com/download/4/0/9/40946FEC-EE5C-48C2-8750-B0F8DA1C99A8/MFC/general/Scribble.zip.exe). Para obter ajuda sobre como converter para o Visual Studio 2017, consulte [guia de portabilidade: Scribble do MFC](../porting/porting-guide-mfc-scribble.md).

##  <a name="top"></a> Seções

Esta parte do passo a passo tem as seguintes seções:

- [Substituindo as Classes Base](#replaceclass)

- [Adicionando Bitmaps ao projeto](#addbitmap)

- [Adicionando um recurso de faixa de opções ao projeto](#addribbon)

- [Criação de uma instância da barra de faixa de opções](#createinstance)

- [Adicionando uma categoria de faixa de opções](#addcategory)

- [Definir a aparência do aplicativo](#setlook)

##  <a name="replaceclass"></a> Substituindo as Classes Base

Para converter um aplicativo que dá suporte a um menu a um aplicativo que dá suporte a uma faixa de opções, você deve derivar de classes base atualizadas o aplicativo, janela de quadro e classes de barra de ferramentas. (Recomendamos que você não modifique o exemplo de Scribble original. Em vez disso, limpe o projeto Scribble, copiá-lo para outro diretório e, em seguida, modificar a cópia.)

### <a name="to-replace-the-base-classes-in-the-scribble-application"></a>Para substituir as classes base do aplicativo de rabisco

1. No scribble.cpp, verifique `CScribbleApp::InitInstance` inclui uma chamada para [AfxOleInit](../mfc/reference/ole-initialization.md#afxoleinit).

1. Adicione o seguinte código ao arquivo Stdafx. h.

    ```cpp
    #include <afxcontrolbars.h>
    ```

1. No scribble.h, modifique a definição para o `CScribbleApp` classe, de modo que ela é derivada de [classe CWinAppEx](../mfc/reference/cwinappex-class.md).

    ```cpp
    class CScribbleApp: public CWinAppEx
    ```

1. Scribble 1.0 foi gravado quando aplicativos do Windows usado um arquivo de inicialização (. ini) para salvar os dados de preferência do usuário. Em vez de um arquivo de inicialização, modifique o Rabisco para armazenar as preferências do usuário no registro. Para definir a chave do registro e a base, digite o seguinte código no `CScribbleApp::InitInstance` depois que o `LoadStdProfileSettings()` instrução.

    ```cpp
    SetRegistryKey(_T("MFCNext\\Samples\\Scribble2"));
    SetRegistryBase(_T("Settings"));
    ```

1. O quadro principal para um aplicativo de interface MDI vários documentos não é derivado de `CMDIFrameWnd` classe. Em vez disso, é derivado de [CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md) classe.

    Nos arquivos mainfrm.h e mainfrm.cpp, substitua todas as referências aos `CMDIFrameWnd` com `CMDIFrameWndEx`.

1. Nos arquivos childfrm.h e childfrm.cpp, substitua `CMDIChildWnd` com `CMDIChildWndEx`.

    No childfrm. arquivo h, substitua `CSplitterWnd` com `CSplitterWndEx`.

1. Modificar as barras de ferramentas e barras de status para usar as novas classes MFC.

    No arquivo mainfrm.h:

    1. Substitua `CToolBar` por `CMFCToolBar`.

    1. Substitua `CStatusBar` por `CMFCStatusBar`.

1. No arquivo mainfrm.cpp:

    1. Substitua `m_wndToolBar.SetBarStyle` com `m_wndToolBar.SetPaneStyle`

    1. Substitua `m_wndToolBar.GetBarStyle` com `m_wndToolBar.GetPaneStyle`

    1. Substitua `DockControlBar(&m_wndToolBar)` com `DockPane(&m_wndToolBar)`

1. No arquivo ipframe.cpp, comente as três linhas de código a seguir.

    ```cpp
    m_wndToolBar.EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->EnableDocking(CBRS_ALIGN_ANY);
    pWndFrame->DockPane(&m_wndToolBar);
    ```

1. Salve as alterações e, em seguida, compilar e executar o aplicativo.

##  <a name="addbitmap"></a> Adicionando Bitmaps ao projeto

As próximas quatro etapas deste passo a passo exigem recursos de bitmap. Você pode obter os bitmaps apropriados de várias maneiras:

- Use o [editores de recursos](../windows/resource-editors.md) inventar seu próprio bitmaps. Ou use os editores de recursos para agrupar bitmaps das imagens portable network graphics (. png) que estão incluídos com o Visual Studio e podem ser baixadas do [biblioteca de imagens do Visual Studio](https://docs.microsoft.com/visualstudio/designers/the-visual-studio-image-library).

    No entanto, o **faixa de opções** interface do usuário requer que determinadas bitmaps dá suporte a imagens transparentes. Bitmaps transparentes utilizam pixels de 32 bits, em que 24 bits especificar os componentes vermelhos, verdes e azuis da cor e 8 bits definem um *canal alfa* que especifica a transparência da cor. Os editores de recursos atual podem exibir, mas não modificar bitmaps com pixels de 32 bits. Consequentemente, use um editor de imagem externa em vez dos editores de recursos para manipular os bitmaps transparentes.

- Copiar um arquivo de recurso apropriado de outro aplicativo para seu projeto e, em seguida, importe bitmaps desse arquivo.

Este passo a passo copia os arquivos de recurso do exemplo criado no [passo a passo: Criando um aplicativo de faixa de opções usando MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

### <a name="to-add-bitmaps-to-the-project"></a>Para adicionar os bitmaps ao projeto

1. Usar o Explorador de arquivos para copiar os seguintes arquivos. bmp de diretório de recursos (`res`) de exemplo da faixa de opções para o diretório de recursos (`res`) do projeto Scribble:

   1. Copie main.bmp ao seu projeto Scribble.

   1. Copie filesmall.bmp e filelarge.bmp ao seu projeto Scribble.

   1. Fazer novas cópias dos arquivos filelarge.bmp e filesmall.bmp, mas salvar as cópias no exemplo a faixa de opções. Renomeie a cópias homesmall.bmp e homelarge.bmp e, em seguida, mova as cópias ao seu projeto Scribble.

   1. Faça uma cópia do arquivo toolbar.bmp, mas salvar a cópia no exemplo a faixa de opções. Renomeie a cópia panelicons.bmp e, em seguida, transferir a cópia para o projeto Scribble.

1. Importe o bitmap de um aplicativo do MFC. No **exibição de recurso**, clique duas vezes o **scribble.rc** nó, clique duas vezes o **Bitmap** nó e, em seguida, clique **adicionar recurso**. Na caixa de diálogo que aparece, clique em **importação**. Navegue até a `res` diretório, selecione o arquivo main.bmp e, em seguida, clique em **aberto**.

   O bitmap main.bmp contém uma imagem de 26 x 26. Alterar a ID do bitmap a ser `IDB_RIBBON_MAIN`.

1. Importar os bitmaps para o menu de arquivo que está associado a **aplicativo** botão.

   1. Importe o arquivo filesmall.bmp, que contém onze 16 x 16 (16 x 176) imagens. Alterar a ID do bitmap a ser `IDB_RIBBON_FILESMALL`.

   > [!NOTE]
   > Como precisamos apenas as imagens de oito primeiros 16 x 16 (16 x 128), você pode cortar, opcionalmente, a largura do lado direito deste bitmap de 176 a 128.

   1. Importar filelarge.bmp, que contém os 32 x 32 (32 x 288) nove imagens. Alterar a ID do bitmap a ser `IDB_RIBBON_FILELARGE`.

1. Importe os bitmaps para as categorias de faixa de opções e os painéis. Cada guia na barra de faixa de opções é uma categoria e consiste em um rótulo de texto e uma imagem opcional.

   1. Importe o bitmap homesmall.bmp, que contém onze 16 x 16 imagens para bitmaps de botão pequeno. Alterar a ID do bitmap a ser `IDB_RIBBON_HOMESMALL`.

   1. Importe o bitmap homelarge.bmp, que contém nove 32 x 32 imagens para bitmaps de botão grande. Alterar a ID do bitmap a ser `IDB_RIBBON_HOMELARGE`.

1. Importar bitmaps para os painéis de faixa de opções redimensionada. Esses bitmaps ou ícones do painel, são usados após uma operação de redimensionamento, se a faixa de opções é muito pequena para exibir o painel inteiro.

   1. Importe o bitmap panelicons.bmp, que contém oito 16 x 16 imagens. No **propriedades** janela da **Editor de Bitmap**, ajuste a largura do bitmap para 64 (16 x 64). Alterar a ID do bitmap a ser `IDB_PANEL_ICONS`.

   > [!NOTE]
   > Como precisamos apenas as imagens de quatro primeiros 16 x 16 (16 x 64), você pode cortar, opcionalmente, a largura do lado direito deste bitmap de 128 para 64.

##  <a name="addribbon"></a> Adicionando um recurso de faixa de opções ao projeto

Quando você converte um aplicativo que usa um aplicativo que usa uma faixa de opções de menus, você não precisa remover ou desabilitar os menus existentes. Basta criar um recurso de faixa de opções, adicione botões de faixa de opções e, em seguida, associar os novos botões com os itens de menu existentes. Embora os menus não são mais visíveis, as mensagens da barra de faixa de opções são roteadas por meio dos menus e atalhos do menu continuam a funcionar.

Consiste em uma faixa de opções de **aplicativo** botão, que é o botão grande no lado superior esquerdo da faixa de opções e uma ou mais guias de categoria. Cada guia categoria contém um ou mais painéis que atuam como contêineres para controles e botões da faixa de opções. O procedimento a seguir mostra como criar um recurso de faixa de opções e, em seguida, personalizar o **aplicativo** botão.

### <a name="to-add-a-ribbon-resource-to-the-project"></a>Para adicionar um recurso de faixa de opções para o projeto

1. Com o projeto Scribble selecionado na **Gerenciador de soluções**, no **Project** menu, clique em **adicionar recurso**.

1. No **adicionar recurso** caixa de diálogo, selecione **faixa de opções** e, em seguida, clique em **New**.

   Visual Studio cria um recurso de faixa de opções e abre no modo de exibição design. É a ID do recurso da faixa de opções `IDR_RIBBON1`, que é exibido na **exibição de recurso**. A faixa de opções contém uma categoria e um painel.

1. Você pode personalizar o **aplicativo** botão modificando suas propriedades. As IDs de mensagem que são usadas nesse código já estão definidas no menu para o Rabisco 1.0.

1. No modo design, clique o **aplicativo** botão para exibir suas propriedades. Altere valores de propriedade da seguinte maneira: **Imagem** à `IDB_RIBBON_MAIN`, **Prompt** para `File`, **chaves** para `f`, **imagens grandes** para `IDB_RIBBON_FILELARGE`e **Imagens pequenas** para `IDB_RIBBON_FILESMALL`.

1. As modificações a seguir cria um menu que aparece quando o usuário clica o **aplicativo** botão. Clique no botão de reticências (**...** ) ao lado **Main itens** para abrir o **Editor itens**.

   1. Com o **Item** tipo **botão** selecionado, clique em **Add** para adicionar um botão. Alteração **legenda** à `&New`, **ID** para `ID_FILE_NEW`, **imagem** para `0`, **imagem grande** para `0`.

   1. Clique em **adicionar** para adicionar um botão. Alteração **legenda** à `&Save`, **ID** para `ID_FILE_SAVE`, **imagem** para `2`, e **imagem grande** para `2`.

   1. Clique em **adicionar** para adicionar um botão. Alteração **legenda** à `Save &As`, **ID** para `ID_FILE_SAVE_AS`, **imagem** para `3`, e **imagem grande** para `3`.

   1. Clique em **adicionar** para adicionar um botão. Alteração **legenda** à `&Print`, **ID** para `ID_FILE_PRINT`, **imagem** para `4`, e **imagem grande** para `4`.

   1. Alterar o **Item** de tipo para **separador** e, em seguida, clique em **adicionar**.

   1. Alterar o **Item** de tipo para **botão**. Clique em **adicionar** para adicionar um quinto botão. Alteração **legenda** à `&Close`, **ID** para `ID_FILE_CLOSE`, **imagem** para `5`, e **imagem grande** para `5`.

1. As modificações a seguir cria um submenu sob o **impressão** botão que você criou na etapa anterior.

   1. Clique o **Print** botão, altere o **Item** digite a **rótulo**e, em seguida, clique em **inserir**. Alteração **legenda** para `Preview and print the document`.

   1. Clique o **Print** botão, altere o **Item** digite a **botão**e clique em **inserir**. Alteração **legenda** à `&Print`, **ID** para `ID_FILE_PRINT`, **imagem** para `4`, e **imagem grande** para `4`.

   1. Clique o **Print** botão e, em seguida, clique em **inserir** para adicionar um botão. Alteração **legenda** à `&Quick Print`, **ID** para `ID_FILE_PRINT_DIRECT`, **imagem** para `7`, e **imagem grande** para `7`.

   1. Clique o **Print** botão e, em seguida, clique em **inserir** para adicionar outro botão. Alteração **legenda** à `Print Pre&view`, **ID** para `ID_FILE_PRINT_PREVIEW`, **imagem** para `6`, e **imagem grande** para `6`.

   1. Agora você tenha modificado o **Main itens**. Clique em **feche** para sair do **Editor de itens**.

1. A seguinte modificação cria um botão de sair que aparece na parte inferior a **aplicativo** menu do botão.

   1. No **propriedades** janela, clique no botão de reticências (**...** ) ao lado **botão** para abrir o **Editor itens**.

   1. Com o **Item** tipo **botão** selecionado, clique em **Add** para adicionar um botão. Alteração **legenda** à `E&xit`, **ID** para `ID_APP_EXIT`, **imagem** para `8`.

   1. Você modificou o **botões**. Clique em **feche** para sair do **Editor de itens**.

##  <a name="createinstance"></a> Criação de uma instância da barra de faixa de opções

As etapas a seguir mostram como criar uma instância da barra de faixa de opções quando o aplicativo for iniciado. Para adicionar uma barra de faixa de opções para um aplicativo, declare a barra de faixa de opções no arquivo mainfrm.h. Em seguida, no arquivo mainfrm.cpp, escreva código para carregar o recurso de faixa de opções.

### <a name="to-create-an-instance-of-the-ribbon-bar"></a>Para criar uma instância da barra de faixa de opções

1. No arquivo mainfrm.h, adicione um membro de dados para a seção protegida de `CMainFrame`, a definição de classe para o quadro principal. Esse membro é para a barra de faixa de opções.

    ```cpp
    // Ribbon bar for the application
    CMFCRibbonBar m_wndRibbonBar;
    ```

2. No arquivo mainfrm.cpp, adicione o seguinte código antes do final `return` instrução no final o `CMainFrame::OnCreate` função. Ele cria uma instância da barra de faixa de opções.

    ```cpp
    // Create the ribbon bar
    if (!m_wndRibbonBar.Create(this))
    {
        return -1;   //Failed to create ribbon bar
    }
    m_wndRibbonBar.LoadFromResource(IDR_RIBBON1);
    ```

##  <a name="addcategory"></a> Personalizando o recurso de faixa de opções

Agora que você criou o **aplicativo** botão, você pode adicionar elementos à faixa de opções.

> [!NOTE]
> Este passo a passo usa o mesmo ícone de painel para todos os painéis. No entanto, você pode usar outros índices de lista de imagem para exibir outros ícones.

### <a name="to-add-a-home-category-and-edit-panel"></a>Para adicionar uma categoria de Home e Editar painel

1. O programa de rabisco requer apenas uma categoria. Na exibição de design, nos **caixa de ferramentas**, clique duas vezes em **categoria** para adicioná-lo e exibir suas propriedades. Altere valores de propriedade da seguinte maneira: **Legenda** à `&Home`, **imagens grandes** para `IDB_RIBBON_HOMELARGE`, **imagens pequenas** para `IDB_RIBBON_HOMESMALL`.

1. Cada categoria de faixa de opções é organizada em painéis nomeados. Cada painel contém um conjunto de controles que operações relacionadas completa. Esta categoria tem um painel. Clique em **painel**e altere **legenda** para `Edit`.

1. Para o **editar** painel, adicione um botão responsável por limpar o conteúdo do documento. A ID da mensagem para que esse botão já foi definida no `IDR_SCRIBBTYPE` de recurso de menu. Especificar `Clear All` como o texto do botão e o índice do bitmap que decora o botão. Abra o **caixa de ferramentas**e, em seguida, arraste um **botão** para o **editar** painel. Clique no botão e, em seguida, altere **legenda** à `Clear All`, **ID** para `ID_EDIT_CLEAR_ALL`, **índice de imagem** para `0`, **índice da imagem grande**  para `0`.

1. Salve as alterações e, em seguida, compilar e executar o aplicativo. O aplicativo de rabisco deve ser exibido e ele deve ter uma barra de faixa de opções na parte superior da janela, em vez de uma barra de menus. A barra de faixa de opções deve ter uma categoria, **página inicial**, e **Home** deve ter um painel, **editar**. Os botões da faixa de opções que você adicionou devem ser associados com os manipuladores de eventos existente e o **aberto**, **Close**, **salvar**, **impressão**, e **Limpar tudo** botões devem funcionar conforme o esperado.

##  <a name="setlook"></a> Definir a aparência do aplicativo

Um *Gerenciador visual* é um objeto global que controla todos os desenhos de um aplicativo. Como o aplicativo de rabisco original usa o estilo de (UI) de interface de usuário do Office 2000, o aplicativo pode parecer antigo. Você pode redefinir o aplicativo para usar o Gerenciador visual do Office 2007 para que ele fique parecido com um aplicativo do Office 2007.

### <a name="to-set-the-look-of-the-application"></a>Para definir a aparência do aplicativo

1. No `CMainFrame::OnCreate` função, digite o seguinte código antes do `return 0;` instrução para alterar o Gerenciador visual padrão e o estilo.

    ```cpp
    // Set the default manager to Office 2007
    CMFCVisualManager::SetDefaultManager(RUNTIME_CLASS(CMFCVisualManagerOffice2007));
    CMFCVisualManagerOffice2007::SetStyle(CMFCVisualManagerOffice2007::Office2007_LunaBlue);
    ```

1. Salve as alterações e, em seguida, compilar e executar o aplicativo. O interface do usuário do aplicativo deve se parecer com a interface do usuário do Office 2007.

## <a name="next-steps"></a>Próximas etapas

Você modificou o clássico exemplo de rabisco MFC de 1.0 para usar o **Designer de faixa de opções**. Agora vá para [parte 2](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md).

## <a name="see-also"></a>Consulte também

[Explicações Passo a Passo](../mfc/walkthroughs-mfc.md)<br/>
[Passo a passo: Atualizando o aplicativo de rabisco MFC (parte 2)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-2.md)
