---
title: Erro das Ferramentas de Vinculador LNK2011
ms.date: 11/04/2016
f1_keywords:
- LNK2011
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
ms.openlocfilehash: c8c62da6c1b4ea856f7a0854b998946893f2be63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299082"
---
# <a name="linker-tools-error-lnk2011"></a>Erro das Ferramentas de Vinculador LNK2011

objeto precompilado não vinculado; imagem não pode ser executada

Se você usar cabeçalhos pré-compilados, LINK requer que todos os arquivos de objeto criados com cabeçalhos pré-compilados devem ser vinculados em. Se você tiver um arquivo de origem que você usa para gerar um cabeçalho pré-compilado para uso com outros arquivos de origem, agora você deve incluir o arquivo de objeto criado juntamente com o cabeçalho pré-compilado.

Por exemplo, se você compilar um arquivo chamado STUB.cpp para criar um cabeçalho pré-compilado para uso com outros arquivos de origem, você deve vincular com STUB.obj ou você receberá esse erro. Nas linhas de comando a seguir, a linha um é usada para criar um cabeçalho pré-compilado, COMMON.pch, que é usado com PROG1.cpp e PROG2.cpp nas linhas dois e três. O arquivo STUB.cpp contém apenas `#include` linhas (o mesmo `#include` linhas como no PROG1.cpp e PROG2.cpp) e é usado apenas para gerar os cabeçalhos pré-compilados. Na última linha, STUB.obj devem ser vinculados em evitar LNK2011.

```
cl /c /Yccommon.h stub.cpp
cl /c /Yucommon.h prog1.cpp
cl /c /Yucommon.h prog2.cpp
link /out:prog.exe stub.obj prog1.obj prog2.obj
```