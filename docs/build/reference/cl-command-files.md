---
title: Arquivos de comando CL
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- cl.exe compiler, command files
- command files
- command files, CL compiler
ms.assetid: ec3cea06-2af0-4fe9-a94c-119c9d31b3a9
ms.openlocfilehash: dae3238f24fc1ac4898aee0b23c3f1899f2e25fc
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420070"
---
# <a name="cl-command-files"></a>Arquivos de comando CL

Um arquivo de comando é um arquivo de texto que contém opções e nomes de arquivo que você utilizaria em caso contrário, o [linha de comando](../../build/reference/compiler-command-line-syntax.md) ou especificada usando o [variável de ambiente CL](../../build/reference/cl-environment-variables.md). CL aceita um arquivo de comando do compilador como um argumento na variável de ambiente CL ou na linha de comando. Em vez da linha de comando ou da variável de ambiente CL, um arquivo de comando permite que você use várias linhas de opções e nomes de arquivo.

Opções e nomes de arquivo em um arquivo de comando são processados de acordo com o local de um nome de arquivo de comando na variável de ambiente CL ou na linha de comando. No entanto, se a opção /link aparece no arquivo de comando, todas as opções no restante da linha são passadas para o vinculador. Opções nas linhas posteriores no arquivo de comando e opções na linha de comando após a chamada do arquivo de comando ainda são aceitos como opções do compilador. Para obter mais informações sobre como a ordem das opções afeta sua interpretação, consulte [ordem de opções CL](../../build/reference/order-of-cl-options.md).

Um arquivo de comando não deve conter o comando CL. Cada opção deve começar e terminar na mesma linha; não é possível usar a barra invertida (**\\**) para combinar uma opção em duas linhas.

Um arquivo de comando é especificado por um sinal de arroba (**\@**) seguido por um nome de arquivo; o nome do arquivo pode especificar um caminho absoluto ou relativo.

Por exemplo, se o comando a seguir está em um arquivo chamado RESP:

```
/Og /link LIBC.LIB
```

e você especificar o seguinte comando CL:

```
CL /Ob2 @RESP MYAPP.C
```

o comando para CL é da seguinte maneira:

```
CL /Ob2 /Og MYAPP.C /link LIBC.LIB
```

Observe que a linha de comando e os comandos do arquivo de comando são combinados com eficiência.

## <a name="see-also"></a>Consulte também

[Definindo opções do compilador](../../build/reference/setting-compiler-options.md)<br/>
[Opções do Compilador](../../build/reference/compiler-options.md)
