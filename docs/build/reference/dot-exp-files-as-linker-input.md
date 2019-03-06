---
title: Arquivos .Exp como entrada de vinculador
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions
- import libraries, linker files
- linking [C++], exports
- exporting functions, information about exported functions
- exporting data, export (.exp) files
- functions [C++], exporting
- .exp files [C++]
- EXP files
ms.assetid: 399f5636-0a4d-462e-b500-5f5b9ae5ad22
ms.openlocfilehash: 170adfe54b34d14f84b54c717bc9f75fe0b7ab37
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418471"
---
# <a name="exp-files-as-linker-input"></a>Arquivos .Exp como entrada de vinculador

Arquivos de exportação (. Exp) contêm informações sobre itens de funções e os dados exportados. Quando o LIB cria uma biblioteca de importação, ele também cria um arquivo. Exp. Use o arquivo. EXP quando você vincula um programa que exporta para o e importa de outro programa, direta ou indiretamente. Se você vincular um arquivo. EXP, o LINK não produz uma biblioteca de importação, pois ele supõe que LIB já criou um. Para obter detalhes sobre arquivos. EXP e bibliotecas de importação, consulte [trabalhando com bibliotecas de importar e exportar arquivos](../../build/reference/working-with-import-libraries-and-export-files.md).

## <a name="see-also"></a>Consulte também

[Arquivos de entrada de LINK](../../build/reference/link-input-files.md)<br/>
[Opções do vinculador](../../build/reference/linker-options.md)
