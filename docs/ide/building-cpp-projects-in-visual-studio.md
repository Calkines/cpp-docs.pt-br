---
title: Compilando projetos do 	C++ no Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visual C++ projects, building
- projects [C++], building
- builds [C++], about building in Visual Studio
ms.assetid: 9e8bc1a2-bb17-4951-937a-c757ed88d2d1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0da2464684a06b62c6e22ea04bb68a01dc36f42b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382336"
---
# <a name="building-c-projects-in-visual-studio"></a>Compilando projetos do C++ no Visual Studio

No IDE (ambiente de desenvolvimento integrado) do Visual Studio há diversas formas de compilar uma solução completa ou apenas um projeto em uma solução. Você também pode modificar as definições de compilação e especificar etapas de compilação especificadas para aumentar a eficiência do seu processo de desenvolvimento.

Para compilar uma solução que está aberta no Visual Studio e selecionada no **Gerenciador de Soluções**, execute uma destas ações:

- Na barra de menus, escolha **Compilar**, **Compilar Solução**.

- Ou, no **Gerenciador de Soluções**, abra o menu de atalho da solução e, em seguida, escolha **Compilar Solução**.

- Ou pressione F7. (esse é o atalho padrão do teclado para as definições de desenvolvimento em C/C++).

- Ou, na [Janela Comando](/visualstudio/ide/reference/command-window) (na barra de menus, escolha **Exibir**, **Outras Janelas**, **Janela Comando**), insira `Build.BuildSolution`.

- Ou, na caixa [Início Rápido](/visualstudio/ide/reference/quick-launch-environment-options-dialog-box), insira `build build solution`.

Para compilar um projeto selecionado no **Gerenciador de Soluções**, execute uma destas ações:

- Na barra de menus, escolha **Compilar**, **Compilar \<Nome do Projeto>**.

- Ou, no **Gerenciador de Soluções**, abra o menu de atalho do projeto e, em seguida, escolha **Compilar**.

- Ou, na Janela Comando (na barra de menus, escolha **Exibir**, **Outras Janelas**, **Janela Comando**), insira `Build.BuildOnlyProject`.

- Ou, na caixa Início Rápido, insira `build project only build only <project name>`.

Ao compilar um aplicativo em Visual C++ no Visual Studio, você pode modificar diversas definições da compilação na caixa de diálogo Páginas de Propriedades do projeto. Para obter informações sobre como definir as propriedades do projeto, confira [Trabalhando com propriedades do projeto](../ide/working-with-project-properties.md).

Para obter um exemplo de como usar o IDE para criar, compilar e depurar um projeto do C++, confira [Passo a passo: Explorar o IDE do Visual Studio com o C++](/visualstudio/ide/getting-started-with-cpp-in-visual-studio). Para obter um exemplo de como usar o IDE para compilar um projeto do C++/CLR, confira [Passo a passo: Compilando um programa do C++ direcionado ao CLR no Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md). Para obter um exemplo de como usar o IDE para criar um aplicativo do Windows Runtime, confira [Criar seu primeiro aplicativo do Windows Runtime usando o C++](https://msdn.microsoft.com/library/windows/apps/hh974580.aspx).

Para saber mais sobre como compilar, modificar definições de compilação e especificar etapas de compilação personalizadas, consulte os artigos mencionados a seguir.

## <a name="in-this-section"></a>Nesta seção

[Noções básicas sobre etapas e eventos compilação personalizada](../ide/understanding-custom-build-steps-and-build-events.md)<br>
Descreve como personalizar o processo de compilação no ambiente de desenvolvimento integrado.

[Macros comuns para compilar comandos e propriedades](../ide/common-macros-for-build-commands-and-properties.md)<br>
Lista as macros que você pode usar onde as sequências de caracteres são aceitas.

[Compilando projetos externos](../ide/building-external-projects.md)<br>
Fala sobre projetos de compilação que usam instalações externas ao ambiente de desenvolvimento integrado.

[Arquivos de projeto](../ide/project-files.md)<br>
Apresenta a estrutura XML de um arquivo .vcxproj.

## <a name="related-sections"></a>Seções relacionadas

[Caixa de diálogo Diretórios do VC++, Projetos, Opções](vcpp-directories-property-page.md)<br>
(Somente para projetos do MSBuild) Explica como modificar o caminho de pesquisa de arquivos executáveis, arquivos de inclusão, arquivos de biblioteca e arquivos de código-fonte durante um build.

[Compilando e criando](/visualstudio/ide/compiling-and-building-in-visual-studio)<br>
Fornece informações sobre como compilar no Visual Studio.

[Compilando programas do C/C++](../build/building-c-cpp-programs.md)<br>
Fornece links para tópicos que descrevem como compilar seu programa pela linha de comando ou pelo ambiente de desenvolvimento integrado do Visual Studio.

[Referência de build C/C++](../build/reference/c-cpp-building-reference.md)<br>
Fornece links para uma visão geral sobre os programas de compilação em C++, opções de compilador e vinculador, e outras ferramentas de compilação.

[Atualizando projetos de versões anteriores do Visual C++](../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br>
Fornece links para tópicos que abrangem problemas de atualização do projeto do C++ para versões mais recentes do conjunto de ferramentas do compilador.

[Guia de atualização e portabilidade do Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md) Informações detalhadas sobre como atualizar aplicativos do C++ criados em versões anteriores do Visual Studio e também como migrar aplicativos criados com ferramentas que não sejam o Visual Studio.

## <a name="see-also"></a>Consulte também

[Aplicativos universais do Windows (C++)](../windows/universal-windows-apps-cpp.md)