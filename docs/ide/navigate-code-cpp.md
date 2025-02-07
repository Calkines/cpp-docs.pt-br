---
title: Navegar pelo código C++ no Visual Studio
description: Use várias ferramentas no Visual Studio para navegar pela base de código C++.
ms.date: 05/28/2019
ms.openlocfilehash: c2d3a1aa4a26cb820ff4a1e87d6eae88b1b8e739
ms.sourcegitcommit: 96f48079cdc402e4c2c1578d1f1eed4846a484dc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67576522"
---
# <a name="navigate-c-code-in-visual-studio"></a>Navegar pelo código C++ no Visual Studio

O Visual Studio fornece um conjunto de ferramentas que você pode usar para navegar pela base de código de forma rápida e eficiente.

## <a name="open-an-included-file"></a>Abrir um arquivo incluído

Clique com o botão direito do mouse em uma diretiva `#include` e selecione **Ir para o Documento**. Ou selecione **F12** com o cursor sobre essa linha para abrir o arquivo.

![Opção de menu Ir para o Documento do C&#43;&#43](../ide/media/go-to-document.png "Ir para o Documento")

## <a name="toggle-headercode-file"></a>Ativar/Desativar Arquivo de Cabeçalho/Código

Você pode alternar entre um arquivo de cabeçalho e seu arquivo de origem correspondente. Clique com o botão direito do mouse em qualquer lugar do seu arquivo e selecione **Ativar/Desativar Arquivo de Cabeçalho/Código**. Ou selecione **Ctrl+K**, **Ctrl+O**.

## <a name="go-to-definitiondeclaration"></a>Ir para definição/declaração

Navegue até a definição de um símbolo de código, clicando com o botão direito do mouse no editor e selecionando **Ir para definição** ou pressionando **F12**. Navegue até uma declaração da mesma forma, clicando com o botão direito do mouse para abrir o menu de contexto ou selecionando **Ctrl+F12**.

![Ir para definição no C&#43;&#43;](../ide/media/go-to-def.png "Ir para definição")

## <a name="go-to"></a>Ir para

**Ir para** refere-se a um conjunto de recursos de navegação, com cada um fornecendo um tipo específico de resultado com base nos filtros especificados. 

Abra **Ir para** com **Ctrl+,** . Esta ação criará uma caixa de pesquisa sobre o documento que você está editando.

![Ir para no C&#43;&#43;](../ide/media/go-to-cpp.png "Ir para")

**Ir para** inclui estes filtros de pesquisa:

- **Ir para Linha** (**Ctrl+G**): ir rapidamente para outra linha do documento atual.
- **Ir para Todos** (**Ctrl+,** ) ou (**Ctrl+T**): os resultados da pesquisa incluem tudo o que segue.
- **Ir para Arquivo** (**Ctrl 1, F**): pesquise arquivos na solução.
- **Ir para Tipo** (**Ctrl 1, T**): os resultados da pesquisa incluem:
  - Classes, structs e enumerações.
  - Interfaces e representantes (somente código gerenciado).
- **Ir para Membro** (**Ctrl 1, M**): os resultados da pesquisa incluem:
  - Variáveis globais e funções globais.
  - Variáveis de membro de classe e funções de membro.
  - Constantes.
  - Itens de enumeração.
  - Propriedades e eventos.
- **Ir para Símbolo** (**Ctrl 1, S**): os resultados da pesquisa incluem:
  - Resultados de Ir para Tipos e Ir para Membros.
  - Todos os demais constructos da linguagem C++, o que inclui macros.

Quando você invoca **Ir para** pela primeira vez com **Ctrl+** , **Ir para Todos** é ativado (sem filtro nos resultados da pesquisa). Em seguida, você pode selecionar o filtro desejado, usando os botões ao lado da caixa de pesquisa. Invoque um filtro específico usando o atalho de teclado correspondente. Esta ação abre a caixa de pesquisa **Ir para** com esse filtro pré-selecionado. Todos os atalhos de teclado são configuráveis.

Para aplicar um filtro de texto, inicie a consulta de pesquisa com o caractere correspondente do filtro, seguido por um espaço. (**Ir para Linha** pode, opcionalmente, omitir o espaço.) Estes são os filtros de texto disponíveis:

- Ir para Todos: (sem filtro de texto)
- Ir para Número de Linha: :
- Ir para Arquivo: f
- Ir para Tipo: t
- Ir para Membro: m
- Ir para Símbolo: #

O seguinte exemplo mostra os resultados de uma operação *Ir para Arquivos* usando o filtro “f”:

![Menu de Ir para no C&#43;&#43;](../ide/media/vs2017-go-to-results.png "Menu de Ir para")

Para ver a lista de filtros de texto, digite um ? seguido por um espaço. Também é possível acessar os comandos **Ir para** com o menu **Editar**. Essa é outra maneira de se lembrar dos principais atalhos de teclado de **Ir para**.

![Menu de Ir para no C&#43;&#43;](../ide/media/go-to-menu-cpp.png "Menu de Ir para")

## <a name="find-or-find-in-files"></a>Localizar ou Localizar nos Arquivos

Execute uma pesquisa de texto de qualquer item na solução com **Localizar** (**Ctrl+F**) ou **Localizar nos Arquivos** (**Ctrl+Shift+F**).

A opção **Localizar** pode ter o escopo definido para uma seleção, o documento atual, todos os documentos abertos, o projeto atual ou a solução inteira. Você pode usar expressões regulares e texto sem formatação. Ela também realça todas as correspondências automaticamente no IDE.

![Localizar no C&#43;&#43;](../ide/media/find-cpp.png "Localizar")

A opção **Localizar nos Arquivos** é uma versão mais eficiente de **Localizar** que exibe os resultados na janela **Localizar Resultados**. Você pode pesquisar dependências de código externas, filtrar por tipos de arquivos e muito mais. 

![Localizar nos Arquivos no C&#43;&#43;](../ide/media/find-in-files-cpp.png "Localizar nos Arquivos")

Organize os resultados de **Localizar nos Arquivos** em duas janelas. Acrescente os resultados de várias pesquisas juntos. Selecione um resultado para ir até essa localização no arquivo.

![Localizar nos Arquivos no C&#43;&#43;](../ide/media/vs2017-find-in-files-results.png "Localizar nos Arquivos")

Para obter mais informações, confira [Localizar nos Arquivos](/visualstudio/ide/find-in-files) na documentação do Visual Studio.

## <a name="find-all-references"></a>Localizar Todas as Referências

Para localizar todos os usos de um símbolo na base de código, coloque o cursor no símbolo ou logo após ele, clique com o botão direito do mouse e, em seguida, selecione **Localizar Todas as Referências**. Você pode filtrar, classificar ou agrupar os resultados de várias maneiras diferentes. Os resultados são populados de maneira incremental. Eles são classificados como Leituras ou Gravações para ajudar você a ver o que existe na solução, em vez de cabeçalhos do sistema ou outras bibliotecas.

![Localizar todas as referências no C&#43;&#43;](../ide/media/find-all-references-results-cpp.png "Localizar todas as referências")

Agrupe os resultados pelas seguintes categorias:

- Projeto, então Definição
- Somente Definição
- Definição, então Projeto
- Definição, então Caminho
- Definição, Projeto e, então, Caminho

 #### <a name="filter-results"></a>Filtrar os resultados

Para filtrar os resultados, passe o mouse sobre uma coluna e selecione o ícone de filtragem exibido. Filtre os resultados da primeira coluna para ocultar itens como referências de cadeias de caracteres e comentários que talvez você não deseje ver.

![Localizar todos os filtros de referências no C&#43;&#43;](../ide/media/find-all-references-filters-cpp.png "Localizar todos os filtros de referências")

- **Resultados confirmados**: Referências de código real para o símbolo que está sendo pesquisado. Por exemplo, a pesquisa de uma função de membro chamada `Size` retorna todas as referências a `Size` que correspondem ao escopo da classe que define `Size`.

- **Resultados desconfirmados**: Esse filtro está desativado por padrão porque mostra os símbolos cujos nomes correspondem aos símbolos pesquisados, mas que não são referências reais a eles. Por exemplo, se você tiver duas classes, com cada uma definindo uma função de membro chamada `Size`, e executar uma pesquisa por `Size` em uma referência de um objeto de `Class1`, todas as referências a `Size` de `Class2` serão exibidas como desconfirmadas.

- **Resultados não processados**: As operações **Localizar Todas as Referências** podem levar tempo para serem concluídas em bases de código maiores, portanto, a lista de resultados mostra os resultados "não processados" aqui. Os resultados não processados correspondem ao nome do símbolo que está sendo pesquisado, mas que ainda não foi confirmado como uma referência de código real. Ative esse filtro para obter resultados mais rápidos. Apenas lembre-se de que alguns resultados podem não ser referências reais.

 #### <a name="sort-results"></a>Classificar os resultados

Classifique os resultados por qualquer coluna, selecionando essa coluna. Alterne entre ordem ascendente ou decrescente selecionando a coluna novamente.

## <a name="navigation-bar"></a>Barra de navegação

Navegue até a definição de um tipo em um arquivo ou até membros de tipo, usando a **barra de navegação** acima da janela do editor.

![Barra de navegação no C&#43;&#43;](../ide/media/navbar-cpp.png "Barra de navegação")

## <a name="see-also"></a>Consulte também

- [Ler e entender o código C++](read-and-understand-code-cpp.md)</br>
- [Editar e refatorar o código C++](read-and-understand-code-cpp.md)</br>
- [Colaborar com o Live Share para C++](live-share-cpp.md)
