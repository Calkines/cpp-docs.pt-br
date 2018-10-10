---
title: Compilando um programa do C++ direcionado ao CLR | Microsoft Docs
ms.custom: ''
ms.date: 09/17/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a375f93eaa164657964be7ad1ea2554ebc1986b8
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235393"
---
# <a name="walkthrough-compiling-a-c-program-that-targets-the-clr-in-visual-studio"></a>Instruções passo a passo: compilando um programa C++ que se destina ao CLR no Visual Studio

Crie programas do Visual C++ que usam classes .NET e compile-os usando o Ambiente de Desenvolvimento do Visual Studio.  
  
Para este procedimento, é possível digitar seu próprio programa do Visual C++ ou usar um dos programas de exemplo. O programa de exemplo que usamos neste procedimento cria um arquivo de texto chamado textfile.txt e salva-o no diretório do projeto.  
  
## <a name="prerequisites"></a>Pré-requisitos  

Este tópico pressupõe que você conheça os princípios básicos da linguagem C++.  
  
### <a name="to-create-a-new-project-in-visual-studio-and-add-a-new-source-file"></a>Para criar um projeto no Visual Studio e adicionar um novo arquivo de origem  
  
1. Crie um novo projeto. No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
1. Entre os tipos de projeto do Visual C++, clique em **CLR** e, em seguida, **Projeto CLR Vazio**.  

   > [!NOTE]
   > Se o tipo **Projeto CLR Vazio** estiver ausente (Visual Studio 2017 apenas), selecione **Abrir Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo Projeto**. Instale a opção localizada embaixo de **Desenvolvimento para desktop com C++** na seção de componentes **Opcional**, denominada **Suporte ao C++/CLI**.<br/>
  
1. Digite um nome de projeto.  
  
    Por padrão, a solução que contém o projeto tem o mesmo nome do novo projeto, mas você pode inserir outro nome. Insira outro local para o projeto se desejar.  
  
    Clique em **OK** para criar o projeto.  
  
1. Se o **Gerenciador de Soluções** não estiver visível, clique no **Gerenciador de Soluções** no menu **Exibir**.  
  
1. Adicione um novo arquivo de origem ao projeto:  
  
    - Clique com o botão direito do mouse na pasta **Arquivos de origem** no **Gerenciador de Soluções**, aponte para **Adicionar** e clique em **Novo Item**.  
  
    - Clique em **Arquivo C++ (.cpp)**, digite um nome de arquivo e, em seguida, clique em **Adicionar**.  
  
    O arquivo **.cpp** é exibido na pasta **Arquivos de Origem** do **Gerenciador de Soluções** e uma janela com guias é exibida no campo no qual você digita o código que deseja inserir nesse arquivo.  
  
1. Clique na guia recém-criada no Visual Studio e digite um programa válido do Visual C++ ou copie e cole um dos programas de exemplo.  
  
    Por exemplo, use o programa de exemplo [Como escrever um arquivo de texto (C++/CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md) (no nó **Manipulação de Arquivos e E/S** do Guia de Programação).  
  
    Se você usar o programa de exemplo, observe que você usará a palavra-chave `gcnew` em vez de `new` durante a criação de um objeto .NET e que `gcnew` retorna um identificador (`^`) em vez de um ponteiro (`*`):  
  
    `StreamWriter^ sw = gcnew StreamWriter(fileName);`  
  
    Para obter mais informações sobre a nova sintaxe Visual C++, confira [Extensões de componentes para plataformas de tempo de execução](../windows/component-extensions-for-runtime-platforms.md).  
  
1. No menu **Compilar**, clique em **Compilar Solução**.  
  
    A janela de **Saída** exibe informações sobre o progresso da compilação, como o local do log de build e uma mensagem que indica o status do build.  
  
    Se você fizer alterações e executar o programa sem fazer um build, uma caixa de diálogo poderá indicar que o projeto está desatualizado. Marque a caixa de seleção nessa caixa de diálogo antes de clicar em **OK** se desejar que o Visual Studio sempre use as versões atuais dos arquivos, em vez de exibir uma solicitação sempre que compilar o aplicativo.  
  
1. No menu **Depuração**, clique em **Iniciar sem Depurar**.  
  
1. Se você usou o programa de exemplo, quando executar o programa, será exibida uma janela Comando que indica que o arquivo de texto foi criado.  
  
    O arquivo de texto **textfile.txt** agora está localizado no diretório do projeto. Abra esse arquivo usando o Bloco de notas.  
  
    > [!NOTE]
    > A escolha do modelo de projeto CLR vazio define automaticamente a opção do compilador `/clr`. Para verificar isso, clique com o botão direito do mouse no projeto no **Gerenciador de Soluções**, clique em **Propriedades** e, em seguida, marque a opção **Suporte a Common Language Runtime** no nó **Geral** de **Propriedades de Configuração**.  
  
## <a name="whats-next"></a>Novidades 

**Anterior:** [Passo a passo: compilando um programa do C++ nativo na linha de comando](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
**Próximo:** [Passo a passo: compilar um programa do C na linha de comando](../build/walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
  
## <a name="see-also"></a>Consulte também  

[Referência da linguagem C++](../cpp/cpp-language-reference.md)<br/>
[Compilando programas do C/C++](../build/building-c-cpp-programs.md)<br/>
