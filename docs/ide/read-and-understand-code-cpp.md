---
title: Ler e entender o código C++ no Visual Studio
description: Use o editor de código C++ no Visual Studio para formatar e entender o código.
ms.date: 05/28/2019
ms.openlocfilehash: c5e4d7f3e53ef37649e3635d11cf99b10cb8a7ee
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66742022"
---
# <a name="read-and-understand-c-code-in-visual-studio"></a>Ler e entender o código C++ no Visual Studio

O editor de códigos e o IDE do Visual Studio fornecem muitos recursos de codificação. Alguns são exclusivos ao C++ e outros são essencialmente os mesmos para todas as linguagens Visual Studio. Para obter mais informações sobre as funcionalidades compartilhadas, confira [Escrevendo um código no Editor de Códigos e de Texto](/visualstudio/ide/writing-code-in-the-code-and-text-editor).  

## <a name="colorization"></a>Colorização

O Visual Studio colore elementos de sintaxe para diferenciar entre tipos de símbolos, como palavras-chave de linguagem, nomes de tipos, nomes de variáveis, parâmetros de função, literais de cadeia de caracteres e assim por diante.

![Colorização de código](../ide/media/code-outline-colorization.png "Colorização do C++")

 O código não utilizado (como o código em um #if 0) tem uma cor mais esmaecida.

 ![Código inativo](../ide/media/inactive-code-cpp.png "Código inativo do C++")

Personalize as cores digitando "Fontes" em **Início Rápido** e, em seguida, escolhendo **Fontes e Cores**. Na caixa de diálogo **Fontes e Cores**, role a página para baixo até as opções do C/C++ e, em seguida, escolha uma fonte e/ou uma cor personalizada.

## <a name="outlining"></a>Estrutura de tópicos

Clique com o botão direito do mouse em qualquer lugar em um arquivo de código-fonte e escolha **Estrutura de Tópicos** para recolher ou expandir blocos de código e/ou regiões personalizadas, a fim de facilitar a navegação apenas pelo código de seu interesse. Para obter mais informações, consulte [Estrutura de tópicos](/visualstudio/ide/outlining).

![Estrutura de tópicos no C&#43;&#43;](../ide/media/vs2015_cpp_outlining.png "Estrutura de tópicos")

Quando você coloca o cursor na frente de uma chave, '{' ou '}', o editor realça seu equivalente correspondente.

Outras opções de estrutura de tópicos estão localizadas em **Editar** > **Estrutura de Tópicos** no menu principal.

## <a name="line-numbers"></a>Os números de linha

Adicione números de linha ao projeto acessando **Ferramentas** > **Opções** > **Editor de Texto** > **Todas as Linguagens** > **Geral** ou pesquisando “número de linha” com **Início Rápido (Ctrl+Q)** . Os números de linha podem ser definidos para todas as linguagens ou para linguagens específicas, incluindo C++.

## <a name="scroll-and-zoom"></a>Rolar e aplicar zoom

Você pode ampliar ou reduzir a página no editor pressionando a tecla **Ctrl** e rolando a página com o botão de rolagem do mouse. Também é possível aplicar zoom usando a configuração de zoom no canto inferior esquerdo.

![Controle de Zoom no C&#43;&#43;](../ide/media/zoom-control.png "Controle de Zoom")

O **Modo de Mapa** da barra de rolagem permite que você role a página e navegue por um arquivo de código rapidamente sem sair da localização atual. Clique em qualquer lugar no mapa de códigos para ir diretamente para essa localização.

![Mapa de códigos no C&#43;&#43;](../ide/media/vs2015-cpp-code-map.png "Mapa de códigos")

Para ativar o **Modo de Mapa**, digite “mapa” na caixa de pesquisa **Início Rápido** na barra de ferramentas principal e escolha **Usar modo de mapa de rolagem**. Para obter mais informações, confira [Como: Acompanhar o código personalizando a barra de rolagem](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

Quando o **Modo de Mapa** estiver desativado, a barra de rolagem ainda realçará as alterações feitas no arquivo. A cor verde indica as alterações salvas e a cor amarela indica as alterações não salvas.

## <a name="quick-info-and-parameter-info"></a>Informações Rápidas e Informações de Parâmetro

Passe o mouse sobre qualquer variável, função ou outro símbolo para obter informações sobre ele, incluindo a declaração e os comentários localizados logo antes dela.

::: moniker range="vs-2019"

![Informações Rápidas no C&#43;&#43;](../ide/media/quick-info-vs2019.png "Informações Rápidas")

A dica de ferramenta **Informações Rápidas** tem um link **Pesquisar Online**. Acesse **Ferramentas** > **Opções** > **Editor de Texto** > **C++**  > **Exibir** para especificar o provedor de pesquisa. 

Se houver um erro no código, passe o mouse sobre ele, e as **Informações Rápidas** exibirão a mensagem de erro. Encontre também a mensagem de erro na janela Lista de Erros.

![Informações Rápidas sobre o erro](../ide/media/quickinfo-on-error.png "Informações Rápidas sobre o erro")

::: moniker-end

::: moniker range="<=vs-2017"

![Informações Rápidas no C&#43;&#43;](../ide/media/quick-info.png "Informações Rápidas")

Se houver um erro no código, passe o mouse sobre ele, e as **Informações Rápidas** exibirão a mensagem de erro. Encontre também a mensagem de erro na janela **Lista de Erros**.

![Informações Rápidas sobre o erro](../ide/media/quickinfo-on-error.png "Informações Rápidas sobre o erro")

::: moniker-end

Quando você chama uma função, a opção **Informações de Parâmetro** mostra os tipos de parâmetros e a ordem na qual eles são esperados.

![Informações de Parâmetro no C&#43;&#43;](../ide/media/parameter-info.png "Informações de Parâmetro")

## <a name="peek-definition"></a>Inspecionar Definição

Passe o mouse sobre uma variável ou uma declaração da função, clique com o botão direito do mouse e, em seguida, escolha **Inspecionar Definição** para ver uma exibição embutida de sua definição sem sair da localização atual. Para obter mais informações, confira [Inspecionar Definição (Alt+F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![Inspecionar Definição no C&#43;&#43;](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

##  <a name="f1-help"></a>F1 Ajuda

Posicione o cursor sobre qualquer tipo, palavra-chave ou função ou imediatamente após eles e pressione **F1** para ir diretamente para o tópico de referência relevante em docs.microsoft.com. **F1** também funciona em itens da Lista de Erros e em muitas caixas de diálogo.

## <a name="class-view"></a>Exibição de Classe

O **Modo de Exibição de Classe** exibe um conjunto pesquisável de árvores de todos os símbolos de códigos e suas hierarquias de pai/filho e escopo, organizadas por projeto. Configure o que o **Modo de Exibição de Classe** exibe em **Configurações do Modo de Exibição de Classe** (clique no ícone da caixa de engrenagem na parte superior da janela).

![Modo de Exibição de Classe no C&#43;&#43;](../ide/media/class-view.png "Modo de Exibição de Classe")

## <a name="generate-graph-of-include-files"></a>Gerar grafo de arquivos de inclusão

Clique com o botão direito do mouse em um arquivo de código no projeto e escolha **Gerar grafo de arquivos de inclusão** para ver um grafo de quais arquivos são incluídos por outros arquivos.

![Grafo de arquivos de inclusão no C&#43;&#43;](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="view-call-hierarchy"></a>Exibir Hierarquia de Chamada

Clique com o botão direito do mouse em qualquer chamada de função e exiba uma lista recursiva de todas as funções chamadas por ela e de todas as funções que a chamam. Cada função na lista pode ser expandida da mesma maneira. Para obter mais informações, confira [Hierarquia de chamada](/visualstudio/ide/reference/call-hierarchy).

![Hierarquia de Chamadas no C&#43;&#43;](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="see-also"></a>Consulte também

[Editar e refatorar o código (C++)](writing-and-refactoring-code-cpp.md)</br>
[Navegar pela base de código C++ no Visual Studio](navigate-code-cpp.md)</br>
[Colaborar com o Live Share para C++](live-share-cpp.md)
