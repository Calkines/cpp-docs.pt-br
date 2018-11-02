---
title: Compilando e vinculando programas multithread
ms.date: 11/04/2016
helpviewer_keywords:
- compiling multithreaded programs
- multithreading [C++], linking programs
- threading [C++], linking programs
- multithreading [C++], compiled programs
- threading [C++], compiled programs
- compiling source code [C++], multithread programs
- linking [C++], multithread programs
ms.assetid: 27589afc-daf2-4f26-b868-a99de5c9dfec
ms.openlocfilehash: 3d98f5341de1374c9119e2a4303c94fcfb005e29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558880"
---
# <a name="compiling-and-linking-multithread-programs"></a>Compilando e vinculando programas multithread

O programa de Bounce é introduzido no [programa de C Multithread de exemplo](sample-multithread-c-program.md).

Programas são compilados com multithread por padrão.

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-within-the-development-environment"></a>Para compilar e vincular o programa multithread Bounce de dentro do ambiente de desenvolvimento

1. No menu **Arquivo**, clique em **Novo** e clique em **Projeto**.

1. No **tipos de projeto** painel, clique em **Win32**.

1. No **modelos** painel, clique em **aplicativo de Console Win32**e, em seguida, nomeie o projeto.

1. Adicione o arquivo que contém o código-fonte C para o projeto.

1. No **compilar** menu, compile o projeto clicando o **Build** comando.

### <a name="to-compile-and-link-the-multithread-program-bouncec-from-the-command-line"></a>Para compilar e vincular o programa multithread Bounce da linha de comando

1. Compilar e vincular o programa:

    ```
    CL BOUNCE.C
    ```

## <a name="see-also"></a>Consulte também

[Multithreading com C e Win32](multithreading-with-c-and-win32.md)