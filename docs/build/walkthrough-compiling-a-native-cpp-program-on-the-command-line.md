---
title: 'Passo a passo: Compilando um programa C++ nativo na linha de comando'
description: Usar o Microsoft C++ compilador de um prompt de comando.
ms.custom: conceptual
ms.date: 04/23/2019
helpviewer_keywords:
- native code [C++]
- Visual C++, native code
- compiling programs [C++]
- command-line applications [C++], native
ms.assetid: b200cfd1-0440-498f-90ee-7ecf92492dc0
ms.openlocfilehash: 64300c8683dd5d1c40638ba7d50acfca6abc40c0
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65217705"
---
# <a name="walkthrough-compiling-a-native-c-program-on-the-command-line"></a>Passo a passo: Compilando um programa C++ nativo na linha de comando

O Visual Studio inclui uma linha de comando C++ compilador que você pode usar para criar tudo, desde aplicativos de console básicos para aplicativos da plataforma Universal do Windows, aplicativos da área de trabalho, drivers de dispositivo e componentes do .NET.

Este passo a passo, você criará um básico "Hello, World"-estilo programa C++ usando um texto de editor e, em seguida, compilá-lo na linha de comando. Se você gostaria de experimentar o IDE do Visual Studio em vez de usar a linha de comando, consulte [passo a passo: Trabalhando com projetos e soluções (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) ou [usando o IDE do Visual Studio para desenvolvimento de área de trabalho do C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

Neste passo a passo, é possível usar o próprio programa do Visual C++ em vez de digitar o programa mostrado, ou usar uma amostra de código do Visual C++ de outro artigo de ajuda.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este passo a passo, você deve ter instalado o Visual Studio e opcional **desenvolvimento para Desktop com C++** carga de trabalho ou as ferramentas de linha de comando de Build para o Visual Studio.

Visual Studio é um ambiente de desenvolvimento integrado (IDE) que dá suporte a um editor completo e compiladores, depuradores e gerenciadores de recursos para várias linguagens e plataformas. Para obter informações sobre como baixar e instalar o Visual Studio, incluindo o Visual Studio Community edition gratuito e incluem suporte para o desenvolvimento do C/C++, consulte [suporte de instalar o C++ no Visual Studio](vscpp-step-0-installation.md).

As ferramentas de Build para o Visual Studio instala somente os compiladores de linha de comando, ferramentas e bibliotecas que necessárias para compilar programas em C e C++. Ele é perfeito para a criação de laboratórios ou sala de aula exercícios e instala relativamente rápido. Para instalar apenas as ferramentas de linha de comando, procure as ferramentas de Build para o Visual Studio na [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/) página.

Antes de compilar um programa C ou C++ na linha de comando, você deve verificar se as ferramentas são instaladas e que você pode acessá-los na linha de comando. Visual C++ tem requisitos complexos para o ambiente de linha de comando encontrar as ferramentas, cabeçalhos e bibliotecas que ele usa. **Não é possível usar o Visual C++ em uma janela de prompt de comando simples** sem fazer algumas preparações. Felizmente, o Visual C++ instala atalhos para que você inicie um prompt de comando do desenvolvedor que tenha a configuração de ambiente para compilações de linha de comando. Infelizmente, os nomes dos atalhos de prompt de comando do desenvolvedor e onde elas estão localizadas são diferentes em quase todas as versões do Visual C++ e em versões diferentes do Windows. A primeira tarefa do passo a passo é encontrar um certo para usar.

> [!NOTE]
> Um atalho de prompt de comando do desenvolvedor define automaticamente os caminhos corretos para o compilador e ferramentas e para quaisquer cabeçalhos necessários e bibliotecas. Você deve definir esses valores de ambiente se você usar uma expressão **Prompt de comando** janela. Para obter mais informações, consulte [definir o caminho e variáveis de ambiente para Builds de linha de comando](setting-the-path-and-environment-variables-for-command-line-builds.md). É recomendável que você use um atalho de prompt de comando do desenvolvedor em vez de criar seus próprios.

### <a name="open-a-developer-command-prompt"></a>Abra um prompt de comando do desenvolvedor

1. Se você tiver instalado o Visual Studio 2017 ou posterior no Windows 10, abra o menu Iniciar e escolha **todos os aplicativos**. Role para baixo e abra o **Visual Studio** pasta (não o aplicativo do Visual Studio). Escolher **Prompt de comando do desenvolvedor para VS** para abrir a janela de prompt de comando.

   Se você tiver instalado o Microsoft Visual C++ Build Tools 2015 no Windows 10, abra o **inicie** menu e escolha **todos os aplicativos**. Role para baixo e abra o **ferramentas de Build do Visual C++** pasta. Escolher **Prompt de comando de ferramentas nativas do Visual C++ 2015 x86** para abrir a janela de prompt de comando.

   Você também pode usar a função de pesquisa do Windows para procurar por "prompt de comando do desenvolvedor" e escolha aquela que corresponde à sua versão instalada do Visual Studio. Use o atalho para abrir a janela de prompt de comando.

1. Em seguida, verifique se o prompt de comando do desenvolvedor de Visual C++ está definido corretamente. Na janela do prompt de comando, digite `cl` e verifique se que a saída é semelhante a:

   ```Output
   C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise>cl
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   usage: cl [ option... ] filename... [ /link linkoption... ]
   ```

   Pode haver diferenças no diretório atual ou os números de versão, dependendo da versão do Visual C++ e qualquer atualização instalada. Se a saída acima é semelhante ao que você vê, em seguida, você estará pronto para compilar programas C ou C++ na linha de comando.

   > [!NOTE]
   > Se você receber um erro, como "'cl' não é reconhecido como um comando interno ou externo, programa operável ou arquivo em lotes," Erro C1034 ou erro LNK1104 quando você executa o **cl** de comando, em seguida, ou você não estiver usando um prompt de comando do desenvolvedor, ou algo está errado com sua instalação do Visual C++. Você deve corrigir esse problema antes de continuar.

   Se você não encontrar o desenvolvedor de atalho do prompt de comando, ou se você receber uma mensagem de erro quando você insere `cl`, em seguida, a instalação do Visual C++ pode ter um problema. Tente reinstalar o componente do Visual C++ no Visual Studio ou reinstale o Microsoft Visual C++ ferramentas de Build. Não vá para a próxima seção até que isso funciona. Para obter mais informações sobre como instalar e solucionar problemas do Visual C++, consulte [instalar o Visual Studio](/visualstudio/install/install-visual-studio).

   > [!NOTE]
   > Dependendo da versão do Windows no computador e a configuração de segurança do sistema, talvez seja necessário com o botão direito para abrir o menu de atalho para o atalho de prompt de comando do desenvolvedor e, em seguida, escolha **executar como administrador** para compilar e executar o programa que você criar seguindo este passo a passo com êxito.

### <a name="create-a-visual-c-source-file-and-compile-it-on-the-command-line"></a>Criar um arquivo de origem do Visual C++ e compilá-lo na linha de comando

1. Na janela de prompt de comando do desenvolvedor, digite `md c:\hello` para criar um diretório e, em seguida, insira `cd c:\hello` para alterar para aquele diretório. Esse diretório é onde o arquivo de origem e o programa compilado são criados no.

1. Insira `notepad hello.cpp` na janela do prompt de comando.

   Escolher **Sim** quando o bloco de notas solicitará que você crie um arquivo. Essa etapa abre uma janela do bloco de notas em branco, pronta para que você insira seu código em um arquivo chamado hello.cpp.

1. No bloco de notas, insira as seguintes linhas de código:

   ```cpp
   #include <iostream>
   using namespace std;
   void main()
   {
       cout << "Hello, world, from Visual C++!" << endl;
   }
   ```

   Esse código é um programa simples que irá escrever uma linha de texto na tela e, em seguida, sair. Para minimizar os erros, copie esse código e cole-a no bloco de notas.

1. Salve seu trabalho! No bloco de notas, sobre o **arquivo** menu, escolha **salvar**.

   Parabéns, você criou um C++ arquivo de origem, hello.cpp, que está pronto para compilar.

1. Alterne para a janela de prompt de comando do desenvolvedor. Insira `dir` no prompt de comando para listar o conteúdo do diretório c:\hello. Você deve ver o hello.cpp do arquivo de origem na listagem de diretório, que é semelhante:

   ```Output
   c:\hello>dir
    Volume in drive C has no label.
    Volume Serial Number is CC62-6545

    Directory of c:\hello

   05/24/2016  05:36 PM    <DIR>          .
   05/24/2016  05:36 PM    <DIR>          ..
   05/24/2016  05:37 PM               115 hello.cpp
                  1 File(s)            115 bytes
                  2 Dir(s)  571,343,446,016 bytes free

   ```

   As datas e outros detalhes serão diferentes em seu computador. Se você não vir seu arquivo de código fonte, hello.cpp, verifique se você tiver alterado para o diretório c:\hello que você criou e no bloco de notas, certifique-se de que você salvou o arquivo de origem nesse diretório. Além disso, certifique-se de que você salvou o código-fonte com uma extensão de nome de arquivo. cpp, não é uma extensão. txt.

1. No prompt de comando do desenvolvedor, digite `cl /EHsc hello.cpp` para compilar seu programa.

   O compilador cl.exe gera um arquivo. obj que contém o código compilado e, em seguida, executa o vinculador para criar um programa executável chamado hello.exe. Esse nome é exibido nas linhas das informações de saída exibidas pelo compilador. A saída do compilador deve ser algo como:

   ```Output
   c:\hello>cl /EHsc hello.cpp
   Microsoft (R) C/C++ Optimizing Compiler Version 19.10.25017 for x86
   Copyright (C) Microsoft Corporation.  All rights reserved.

   hello.cpp
   Microsoft (R) Incremental Linker Version 14.10.25017.0
   Copyright (C) Microsoft Corporation.  All rights reserved.

   /out:hello.exe
   hello.obj
   ```

   > [!NOTE]
   > Se você receber um erro, como "'cl' não é reconhecido como um comando interno ou externo, programa operável ou arquivo em lotes," Erro C1034 ou erro LNK1104, seu prompt de comando do desenvolvedor não está configurado corretamente. Para obter informações sobre como corrigir esse problema, volte para o **abra um prompt de comando do desenvolvedor** seção.

   > [!NOTE]
   > Se você receber um diferente do compilador ou aviso ou erro de vinculador, revise seu código-fonte para corrigir os erros, em seguida, salvá-lo e executar o compilador novamente. Para obter informações sobre erros específicos, use a caixa de pesquisa nesta página do MSDN para procurar o número do erro.

1. Para executar o programa hello.exe, no prompt de comando, digite `hello`.

   O programa exibe este texto e é fechado:

   ```Output
   Hello, world, from Visual C++!
   ```

   Parabéns, você acabou de compilado e executar um programa C++ usando as ferramentas de linha de comando.

## <a name="next-steps"></a>Próximas etapas

Este exemplo "Hello, World" é mais simple como um programa C++ pode obter. Programas do mundo real têm arquivos de cabeçalho e mais arquivos de código-fonte, vincular nas bibliotecas e fazer trabalho útil.

Você pode usar as etapas neste passo a passo para criar seu próprio código C++ em vez de digitar o código de exemplo mostrado. Você também pode criar muitos programas de exemplo de código de C++ que você encontre em outro lugar. Você pode colocar seu código-fonte e compilar seus aplicativos em qualquer diretório gravável. Por padrão, o IDE do Visual Studio cria projetos na sua pasta de documentos, em uma subpasta de projetos de uma pasta do Visual Studio chamada para a sua versão do Visual Studio.

Para compilar um programa que tem os arquivos de código de origem adicionais, inseri-las all na linha de comando, como:

`cl /EHsc file1.cpp file2.cpp file3.cpp`

O `/EHsc` opção de linha de comando instrui o compilador para habilitar o tratamento de exceções C++. Para obter mais informações, consulte [/EH (modelo de tratamento de exceção)](reference/eh-exception-handling-model.md).

Quando você fornecer arquivos de origem adicionais, o compilador usa o primeiro arquivo de entrada para criar o nome do programa. Nesse caso, ele produz um programa chamado file1.exe. Para alterar o nome para program1.exe, adicione uma [/out](reference/out-output-file-name.md) a opção de vinculador:

`cl /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

E para capturar erros de programação mais automaticamente, é recomendável que você compilar usando o [/w3](reference/compiler-option-warning-level.md) ou [/W4](reference/compiler-option-warning-level.md) opção de nível de aviso:

`cl /W4 /EHsc file1.cpp file2.cpp file3.cpp /link /out:program1.exe`

O compilador, cl.exe, tem muito mais opções se aplicam para compilar, otimizar, depurar e analisar seu código. Para obter uma lista rápida, insira `cl /?` no prompt de comando do desenvolvedor. Também pode compilar e vincular separadamente e aplicar opções de vinculador em cenários mais complexos de compilação. Para obter mais informações sobre o compilador e as opções do vinculador e uso, consulte [referência de build do C/C++](reference/c-cpp-building-reference.md).

Você pode usar o MSBuild e arquivos de projeto e makefiles ou NMAKE para configurar e criar projetos mais complexos na linha de comando. Para obter mais informações sobre como usar essas ferramentas, consulte [referência de NMAKE](reference/nmake-reference.md) e [MSBuild](msbuild-visual-cpp.md).

As linguagens C e C++ são semelhantes, mas não o mesmo. O compilador MSVC usa uma regra simples para determinar qual idioma usar quando ele compila seu código. Por padrão, o compilador MSVC trata todos os arquivos que terminam em. c como código-fonte C e todos os arquivos que terminam em. cpp como código-fonte C++. Para forçar o compilador trate todos os arquivos dependentes na extensão de nome de arquivo do c++, use o [/Tp](reference/tc-tp-tc-tp-specify-source-file-type.md) opção de compilador.

O compilador MSVC inclui uma biblioteca de tempo de execução de C (CRT) que é compatível com o padrão ISO C99, mas não estritamente em conformidade. Na maioria dos casos, o código portátil compilará e executados conforme o esperado. Visual C++ não oferece suporte algumas das alterações do CRT no ISO C11. Determinadas funções de biblioteca e nomes de função POSIX foram preteridos pelo compilador MSVC. As funções têm suporte, mas os nomes preferenciais foram alterados. Para obter mais informações, consulte [recursos de segurança no CRT](../c-runtime-library/security-features-in-the-crt.md) e [aviso do compilador (nível 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md).

## <a name="see-also"></a>Consulte também

[Referência da linguagem C++](../cpp/cpp-language-reference.md)<br/>
[Sistemas de Compilação e Projetos](projects-and-build-systems-cpp.md)<br/>
[Opções do compilador MSVC](reference/compiler-options.md)
