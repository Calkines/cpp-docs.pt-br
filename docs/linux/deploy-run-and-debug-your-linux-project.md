---
title: Implantar, executar e depurar o projeto do Linux | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7084cdb-17b1-4960-b522-f84981bea879
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: dff1e9e03911f65dfcffcd078e0739224f73f4aa
ms.openlocfilehash: db868094a8f10ad05ed6f95bf8a4c8a29a2c941e

---

# <a name="deploy-run-and-debug-your-project"></a>Implantar, executar e depurar o projeto

Agora que o projeto foi criado, você precisará se conectar ao computador Linux, que é o local em que o código será compilado, executado e depurado.

1. Defina a arquitetura de destino remota usando o menu suspenso padrão no Visual Studio mostrado: ![Arquitetura Remota](media/architecture.png)

Há várias maneiras de interagir com o projeto do Linux e depurá-lo.

* Os recursos tradicionais do Visual Studio, como pontos de interrupção, janelas Inspeção e focalizar uma variável, tudo funcionará como esperado, para que você possa realizar a depuração como faria normalmente.
* Uma janela especial do Console do Linux pode ser aberta com o item de menu **Depurar > Console do Linux**.

  ![Menu do Console do Linux](media/consolemenu.png)

  Esse console exibirá qualquer saída do console do computador de destino, bem como usará a entrada e a enviará ao computador de destino.

  ![Janela do Console do Linux](media/consolewindow.png)

* Argumentos de linha de comando podem ser passados para o executável usando o item **Argumentos do Programa** na página de propriedades **Depuração** do projeto.
  
  ![Argumentos do Programa](media/settings_programarguments.png)

* O GDB é usado para depurar aplicativos em execução no Linux.  No entanto, isso pode ser executado em dois modos diferentes, que podem ser selecionados na opção **Modo de Depuração**, na página de propriedades **Depuração** do projeto:

  ![Opções do GDB](media/settings_debugger.png)

  | Seleção | Descrição
  | --------- | ---
  | gdbserver | O GDB é executado localmente, que se conecta ao gdbserver em execução no sistema remoto.  Observe que esse é o único modo que dá suporte à janela do Console do Linux. 
  | gdb       | O depurador do Visual Studio executa o GDB no sistema remoto, que é mais compatível se a versão local do GDB não é compatível com a versão instalada no computador de destino

* Opções específicas do depurador podem ser passadas para o GDB usando a entrada **Comandos adicionais do depurador**.  Por exemplo, talvez você deseje ignorar os sinais SIGILL (instrução inválida).  Você poderá usar o comando **handle** para fazer isso.  adicionando o seguinte à entrada **Comandos adicionais do depurador**, conforme mostrado acima:

  ```handle SIGILL nostop noprint```



<!--HONumber=Feb17_HO4-->

