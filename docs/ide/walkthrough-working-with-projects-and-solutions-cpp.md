---
title: 'Passo a passo: Como trabalhar com Projetos e Soluções (C++)'
ms.date: 05/14/2019
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
ms.openlocfilehash: 6d9ee71e2608c2ed4935e7a5a3c54af45921e5d2
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108406"
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Passo a passo: Como trabalhar com Projetos e Soluções (C++)

Veja como criar um projeto em C++ no Visual Studio, adicionar código e, em seguida, compilar e executar o projeto. O projeto neste passo a passo é um programa que acompanha quantas pessoas estão jogando jogos de cartas diferentes.

No Visual Studio, o trabalho é organizado em projetos e soluções. Uma solução pode ter mais de um projeto, por exemplo, uma DLL e um executável que referencia essa DLL. Para obter mais informações, consulte [Soluções e projetos](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="before-you-start"></a>Antes de começar

Para concluir este passo a passo, você precisará do Visual Studio 2017 ou posterior. Se você precisar de uma cópia, aqui está um breve guia: [Instalar o suporte ao C++ no Visual Studio](../build/vscpp-step-0-installation.md). Se você ainda não fez isso, siga as próximas etapas após a instalação até o tutorial "Olá, Mundo" para verificar se os componentes do C++ foram instalados corretamente e que tudo funciona.

Será útil se você entender os conceitos básicos da linguagem C++ e saber a função de um compilador, de um vinculador e de um depurador. O tutorial também pressupõe que você esteja familiarizado com o Windows e como usar menus, caixas de diálogo,

## <a name="create-a-project"></a>Criar um projeto

Para criar um projeto, escolha primeiro um modelo de tipo de projeto. Para cada tipo de projeto, o Visual Studio define configurações do compilador e – dependendo do tipo – gera o código inicial que você pode modificar posteriormente. As etapas a seguir variam dependendo da versão do Visual Studio que você está usando. Verifique se o seletor de versão no canto superior esquerdo desta página está definido como a versão correta.

::: moniker range="vs-2019"

### <a name="to-create-a-project-in-visual-studio-2019"></a>Para criar um projeto no Visual Studio 2019

1. No menu principal, escolha **Arquivo** > **Novo** > **Projeto** para abrir a caixa de diálogo **Criar um projeto**.

1. Na parte superior da caixa de diálogo, defina **Linguagem** como **C++** , **Plataforma** como **Windows** e **Tipo de projeto** como **Console**.

1. Na lista filtrada de tipos de projeto, escolha **Aplicativo de Console** e, em seguida, escolha **Avançar**. Na próxima página, insira *Jogo* como o nome do projeto.

   Você pode aceitar a localização padrão na lista suspensa **Local**, inserir outro local ou escolher o botão **Procurar** para procurar um diretório em que deseja salvar o projeto.

   Quando você cria um projeto, o Visual Studio coloca o projeto em uma solução. Por padrão, a solução tem o mesmo nome do projeto. Você pode alterar o nome na caixa **Nome da solução**, mas, para este exemplo, mantenha o nome padrão.

1. Escolha o botão **Criar** para criar o projeto.

   O Visual Studio cria a solução e os arquivos de projeto e abre o editor no arquivo de código-fonte Game.cpp que ele gerou.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017"></a>Para criar um projeto no Visual Studio 2017

1. Na barra de menus, escolha **Arquivo** > **Novo** > **Projeto**.

1. No painel esquerdo da caixa de diálogo **Novo Projeto**, expanda **Instalado** e selecione **Visual C++** , caso ele ainda não esteja aberto.

1. Na lista de modelos instalados no painel central, selecione **Aplicativo de Console do Windows**.

1. Insira um nome para o projeto na caixa **Nome**. Para este exemplo, insira *Game*.

   Você pode aceitar a localização padrão na lista suspensa **Local**, inserir outro local ou escolher o botão **Procurar** para procurar um diretório em que deseja salvar o projeto.

   Quando você cria um projeto, o Visual Studio coloca o projeto em uma solução. Por padrão, a solução tem o mesmo nome do projeto. Você pode alterar o nome na caixa **Nome da solução**, mas, para este exemplo, mantenha o nome padrão.

1. Escolha o botão **OK** para criar o projeto.

   O Visual Studio cria a solução e os arquivos de projeto e abre o editor no arquivo de código-fonte Game.cpp que ele gerou.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-project-in-visual-studio-2015"></a>Para criar um projeto no Visual Studio 2015

1. Na barra de menus, escolha **Arquivo** > **Novo** > **Projeto**.

1. No painel esquerdo da caixa de diálogo **Novo Projeto**, expanda **Instalado** e selecione **Visual C++** , caso ele ainda não esteja aberto.

1. Na lista de modelos instalados no painel central, selecione **Aplicativo do Console Win32**.

1. Insira um nome para o projeto na caixa **Nome**. Para este exemplo, insira *Game*.

   Você pode aceitar a localização padrão na lista suspensa **Local**, inserir outro local ou escolher o botão **Procurar** para procurar um diretório em que deseja salvar o projeto.

   Quando você cria um projeto, o Visual Studio coloca o projeto em uma solução. Por padrão, a solução tem o mesmo nome do projeto. Você pode alterar o nome na caixa **Nome da solução**, mas, para este exemplo, mantenha o nome padrão.

1. Escolha o botão **OK** para criar o projeto.

   O Visual Studio cria a solução e os arquivos de projeto e abre o editor no arquivo de código-fonte Game.cpp que ele gerou.

::: moniker-end

## <a name="organize-projects-and-files"></a>Organizar projetos e arquivos

Use o **Gerenciador de Soluções** para organizar e gerenciar os projetos, os arquivos e outros recursos na solução.

Esta parte do passo a passo mostra como adicionar uma classe ao projeto. Quando você adiciona a classe, o Visual Studio adiciona os arquivos .h e .cpp correspondentes. Veja os resultados no **Gerenciador de Soluções**.

### <a name="to-add-a-class-to-a-project"></a>Para adicionar uma classe a um projeto

1. Se a janela do **Gerenciador de Soluções** não for exibida no Visual Studio, na barra de menus, escolha **Exibir** > **Gerenciador de Soluções**.

1. No **Gerenciador de Soluções**, selecione o projeto **Game**. Na barra de menus, escolha **Projeto** > **Adicionar classe**.

1. Na caixa de diálogo **Adicionar Classe**, insira *Cardgame* na caixa **Nome de classe**. Não altere os nomes de arquivo e as configurações padrão. Escolha o botão **OK**.

   O Visual Studio cria arquivos e adiciona-os ao projeto. Veja-os na janela **Gerenciador de Soluções**. Os arquivos Cardgame.h e Cardgame.cpp são abertos no editor.

1. Edite o arquivo Cardgame.h e faça estas alterações:

   - Adicione dois membros de dados particulares após a chave de abertura da definição de classe.
     <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - Modifique o construtor padrão que o Visual Studio gerou. Após o especificador de acesso `public:`, localize a linha com esta aparência:

      `Cardgame();`

      Modifique o construtor para que ele use um parâmetro do tipo `int`, chamado *players*.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - Após o destruidor padrão, adicione uma declaração embutida para uma função de membro `static int` chamada *GetParticipants* que não usa parâmetros e retorna o valor de `totalParticipants`.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   O arquivo Cardgame.h deve ter a aparência do código abaixo depois de alterado:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]-->

    ```cpp
    #pragma once
    class Cardgame
    {
        int players;
        static int totalParticipants;
    public:
        Cardgame(int players);
        ~Cardgame();
        static int GetParticipants() { return totalParticipants; }
    };
    ```

   A linha `#pragma once` instrui o compilador a incluir o arquivo de cabeçalho somente uma vez. Para obter mais informações, confira [once](../preprocessor/once.md). Para saber mais sobre outras palavras-chave do C++ no arquivo de cabeçalho acima, consulte [class](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [static](../cpp/storage-classes-cpp.md) e [public](../cpp/public-cpp.md).

1. Escolha a guia **Cardgame.cpp** na parte superior do painel de edição para abri-la para edição.

1. Exclua tudo no arquivo e substitua por este código:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]-->

    ```cpp
    #include "pch.h" // remove this line in Visual Studio 2019
    #include "Cardgame.h"
    #include <iostream>

    using namespace std;

    int Cardgame::totalParticipants = 0;

    Cardgame::Cardgame(int players)
        : players(players)
    {
        totalParticipants += players;
        cout << players << " players have started a new game.  There are now "
             << totalParticipants << " players in total." << endl;
    }

    Cardgame::~Cardgame()
    {
    }
    ```

   > [!NOTE]
   > É possível usar o preenchimento automático quando estiver inserindo o código. Por exemplo, se você inserir esse código no teclado, será possível inserir *pl* ou *tot* e, em seguida, pressionar **Ctrl**+**Barra de espaços**. O preenchimento automático insere `players` ou `totalParticipants` para você.

## <a name="add-test-code-to-your-main-function"></a>Adicionar um código de teste à função principal

Adicione um código ao aplicativo que testa as novas funções.

### <a name="to-add-test-code-to-the-project"></a>Para adicionar um código de teste ao projeto

1. Na janela do editor **Game.cpp**, substitua o código existente por:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]-->

    ```cpp
    // Game.cpp : Defines the entry point for the console application.
    //

    #include "pch.h" // remove this line in Visual Studio 2019
    #include "Cardgame.h"
    #include <iostream>

    using namespace std;

    void PlayGames()
    {
        Cardgame bridge(4);
        Cardgame blackjack(8);
        Cardgame solitaire(1);
        Cardgame poker(5);
    }

    int main()
    {
        PlayGames();
        return 0;
    }
    ```

   O código adiciona uma função de teste, `PlayGames`, ao código-fonte e a chama-a em `main`.

## <a name="build-and-run-your-app-project"></a>Compilar e executar o projeto de aplicativo

Em seguida, compile o projeto e execute o aplicativo.

### <a name="to-build-and-run-the-project"></a>Para compilar e executar o projeto

1. Na barra de menus, escolha **Compilar** > **Compilar Solução**.

   O resultado de um build é exibido na janela de **Saída**. Se o build for bem-sucedido, a saída deverá ter esta aparência:

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>pch.cpp
    1>Cardgame.cpp
    1>Game.cpp
    1>Generating Code...
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

   A janela de **Saída** pode mostrar etapas diferentes, dependendo da configuração de build, mas se o build do projeto tiver êxito, a última linha deverá ser semelhante ao resultado mostrado.

   Se o build não foi bem-sucedido, compare seu código com o código mostrado nas etapas anteriores.

1. Para executar o projeto, na barra de menus, escolha **Depurar** > **Iniciar sem Depuração**. Uma janela do console deverá ser exibida, e a saída deverá ser semelhante a esta:

    ```Output
    4 players have started a new game.  There are now 4 players in total.
    8 players have started a new game.  There are now 12 players in total.
    1 players have started a new game.  There are now 13 players in total.
    5 players have started a new game.  There are now 18 players in total.
    ```

   Pressione uma tecla para ignorar a janela do console.

Parabéns! Você compilou com êxito uma solução e um projeto de aplicativo. Continue o passo a passo para saber mais sobre como compilar projetos de código C++ no Visual Studio.

## <a name="next-steps"></a>Próximas etapas

**Anterior:** [Usando o IDE do Visual Studio para desenvolvimento de área de trabalho do C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)<br/>
**Avançar:** [Passo a passo: Compilação de um projeto (C++)](../ide/walkthrough-building-a-project-cpp.md)

## <a name="see-also"></a>Consulte também

[Referência da linguagem C++](../cpp/cpp-language-reference.md)<br/>
[Sistemas de Compilação e Projetos](../build/projects-and-build-systems-cpp.md)<br/>
