---
title: 'Como: Modificar o Framework de destino e o conjunto de ferramentas de plataforma'
ms.custom: conceptual
ms.date: 07/24/2019
helpviewer_keywords:
- 'msbuild (c++), howto: modify target framework and platform toolset'
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
ms.openlocfilehash: 6af7a4eb47c1d3f8b9c52eec39795c9307ca9d8e
ms.sourcegitcommit: ce3393846c86e7905ff0c86e4cd6610476809585
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68492226"
---
# <a name="how-to-modify-the-target-framework-and-platform-toolset"></a>Como: Modificar o Framework de destino e o conjunto de ferramentas de plataforma

Você pode editar um arquivo de C++ projeto do Visual Studio para direcionar versões C++ diferentes do conjunto de ferramentas de plataforma, oC++SDK do Windows e o .NET Framework (apenas projetos/CLI). Por padrão, o sistema do projeto usa a versão do .NET Framework e do conjunto de ferramentas que corresponde à versão do Visual Studio usada para criar o projeto. Você pode modificar todos esses valores no arquivo. vcxproj para que você possa usar a mesma base de código para cada destino de compilação.

## <a name="platform-toolset"></a>Conjunto de ferramentas de plataforma

O conjunto de ferramentas de plataforma C++ consiste no compilador (CL. exe) e no vinculador (link. exe), juntamente comC++ as bibliotecas C/Standard. Desde o Visual Studio 2015, a versão principal do conjunto de ferramentas permaneceu em 14, o que significa que os projetos compilados com o Visual Studio 2019 ou o Visual Studio 2017 são ABI-versões compatíveis com projetos compilados com o Visual Studio 2015. A versão secundária foi atualizada em 1 para cada versão desde o Visual Studio 2015:

- Visual Studio 2015: v140
- Visual Studio 2017: v141
- Visual Studio 2019: v142

Esses conjuntos de ferramentas dão suporte ao .NET Framework 4,5 e posterior.

O Visual Studio também dá suporte a multidirecionamento para C++ projetos. Você pode usar o IDE do Visual Studio para editar e compilar projetos que foram criados com versões anteriores do Visual Studio, sem atualizá-los para usar uma nova versão do conjunto de ferramentas. Você precisa ter os conjuntos de ferramentas mais antigos instalados no seu computador. Para obter mais informações, consulte [como usar vários destinos nativos no Visual Studio](../porting/use-native-multi-targeting.md). Por exemplo, no Visual Studio 2015, você pode *direcionar* .NET Framework 2,0, mas deve usar um conjunto de ferramentas anterior que ofereça suporte a ele.

## <a name="target-framework-ccli-project-only"></a>Estrutura de destinoC++(somente projeto/CLI)

Ao alterar a Estrutura de destino, altere também o conjunto de ferramentas da plataforma para uma versão que suporte essa Estrutura. Por exemplo, para direcionar o .NET Framework 4,5, você deve usar um conjunto de ferramentas de plataforma compatível, como o Visual Studio 2015 (V140), Visual Studio 2013 (V120) ou o Visual Studio 2012 (V110). Você pode usar o conjunto de ferramentas do [SDK do Windows 7,1](https://www.microsoft.com/en-us/download/details.aspx?id=8279) para direcionar o .NET Framework 2,0, 3,0, 3,5 e 4 e as plataformas x86/x64.

É possível estender a plataforma de destino ainda mais criando um conjunto de ferramentas personalizado da plataforma. Para obter mais informações, consulte [ C++ multi-Targeting nativo](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) no C++ blog do Visual.

### <a name="to-change-the-target-framework"></a>Para alterar a Estrutura de destino

1. No Visual Studio, em **Gerenciador de soluções**, selecione seu projeto. Na barra de menus, abra o menu **projeto** e escolha **descarregar projeto**. Isso descarrega o arquivo do projeto (.vcxproj) para seu projeto.

   > [!NOTE]
   >  Um projeto C++ não pode ser carregado enquanto o arquivo do projeto estiver sendo modificado no Visual Studio. No entanto, é possível usar outro editor como o Bloco de Notas para modificar o arquivo do projeto enquanto o projeto é carregado no Visual Studio. O Visual Studio detectará que o arquivo do projeto foi modificado e solicitará que o projeto seja recarregado.

1. Na barra de menus, selecione **arquivo**, **abrir**, **arquivo**. Na caixa de diálogo **Abrir arquivo** , navegue até a pasta do projeto e abra o arquivo do projeto (. vcxproj).

1. No arquivo do projeto, localize a entrada para a versão da Estrutura de destino. Por exemplo, se o projeto estiver designado para o .NET Framework 4.5, localize `<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>` no elemento `<PropertyGroup Label="Globals">` do elemento `<Project>`. Se o elemento `<TargetFrameworkVersion>` não estiver presente, seu projeto não usa o .NET Framework e nenhuma modificação é necessária.

1. Altere o valor para a versão de estrutura desejada, como v 3.5 ou v 4.6.

1. Salve as alterações e feche o editor.

1. No **Gerenciador de soluções**, abra o menu de atalho para seu projeto e, em seguida, escolha **recarregar projeto**.

1. Para verificar a alteração, em **Gerenciador de soluções**, clique com o botão direito do mouse para abrir o menu de atalho do seu projeto (não para sua solução) e escolha **Propriedades** para abrir a caixa de diálogo **páginas de propriedades** do projeto. No painel esquerdo da caixa de diálogo, expanda **Propriedades de configuração** e, em seguida, selecione **geral**. Verifique se a **versão da estrutura de destino do .net** mostra a nova versão da estrutura.

### <a name="to-change-the-platform-toolset"></a>Para alterar o conjunto de ferramentas de plataforma

1. No Visual Studio, no **Gerenciador de soluções**, abra o menu de atalho do seu projeto (não para sua solução) e escolha **Propriedades** para abrir a caixa de diálogo **páginas de propriedades** do projeto.

1. Na caixa de diálogo **páginas de propriedades** , abra a lista suspensa **configuração** e, em seguida, selecione **todas as configurações**.

1. No painel esquerdo da caixa de diálogo, expanda **Propriedades de configuração** e, em seguida, selecione **geral**.

1. No painel direito, selecione **conjunto de ferramentas de plataforma** e, em seguida, selecione o conjunto de ferramentas desejado na lista suspensa. Por exemplo, se você tiver instalado o conjunto de ferramentas do Visual Studio 2010, selecione **visual studio 2010 (V100)** para usá-lo para seu projeto.

1. Escolha o botão **OK**.

## <a name="see-also"></a>Consulte também

[MSBuild na linha de comando – C++](msbuild-visual-cpp.md)
