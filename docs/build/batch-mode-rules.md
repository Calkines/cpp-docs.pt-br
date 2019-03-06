---
title: Regras de modo do lote
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
ms.openlocfilehash: 106db69327bbad112be7efea6970845956e52431
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416664"
---
# <a name="batch-mode-rules"></a>Regras de modo do lote

```
{frompath}.fromext{topath}.toext::
   commands
```

Regras de inferência de modo de lote fornecem apenas uma invocação da regra de inferência de tipos quando comandos de N passar por essa regra de inferência de tipos. Sem regras de inferência de modo de lote, ele exigiria comandos de N a ser invocado. N é o número de dependentes que disparam a regra de inferência de tipos.

Makefiles que contêm regras de inferência de modo de lote deve usar NMAKE versão 1.62 ou superior. Para verificar a versão NMAKE, execute a macro _NMAKE_VER disponível com a versão NMAKE 1,62 ou superior. Essa macro retorna uma cadeia de caracteres que representa a versão do produto Visual C++.

A diferença sintática apenas da regra de inferência padrão é que a regra de inferência de tipos de modo de lote é encerrada com dois-pontos duplos (:).

> [!NOTE]
>  A ferramenta que está sendo invocada deve ser capaz de lidar com vários arquivos. A regra de inferência de tipos de modo de lote deve usar `$<` como a macro para acessar os arquivos dependentes.

As regras de inferência de modo de lote podem acelerar o processo de compilação. Ele é mais rápido fornecer arquivos para o compilador em lote, porque o driver do compilador é invocado apenas uma vez. Por exemplo, o compilador C e C++ executa melhor ao lidar com um conjunto de arquivos, porque ele pode permanecer memória residente durante o processo.

O exemplo a seguir mostra como usar regras de inferência de modo de lote:

```
#
# sample makefile to illustrate batch-mode inference rules
#
O = .
S = .
Objs = $O/foo1.obj $O/foo2.obj $O/foo2.obj $O/foo3.obj $O/foo4.obj
CFLAGS = -nologo

all : $(Objs)

!ifdef NOBatch
{$S}.cpp{$O}.obj:
!else
{$S}.cpp{$O}.obj::
!endif
   $(CC) $(CFLAGS) -Fd$O\ -c $<

$(Objs) :

#end of makefile
```

NMAKE produz a seguinte saída sem regras de inferência de modo de lote:

```
E:\tmp> nmake -f test.mak -a NOBatch=1

Microsoft (R) Program Maintenance Utility   Version 7.00.0000
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.
        cl -nologo -Fd.\ -c .\foo1.cpp
foo1.cpp
        cl -nologo -Fd.\ -c .\foo2.cpp
foo2.cpp
        cl -nologo -Fd.\ -c .\foo3.cpp
foo3.cpp
        cl -nologo -Fd.\ -c .\foo4.cpp
foo4.cpp
```

NMAKE produz o resultado a seguir com as regras de inferência de modo de lote:

```
E:\tmp> nmake -f test.mak -a

Microsoft (R) Program Maintenance Utility   Version 7.00.0000
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.

        cl -nologo -Fd.\ -c .\foo1.cpp .\foo2.cpp .\foo3.cpp .\foo4.cpp
foo1.cpp
foo2.cpp
foo3.cpp
foo4.cpp
Generating Code...
```

## <a name="see-also"></a>Consulte também

[Regras de inferência](../build/inference-rules.md)
