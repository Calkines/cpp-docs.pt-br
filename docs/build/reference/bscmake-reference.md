---
title: Referência de BSCMAKE
ms.date: 05/06/2019
helpviewer_keywords:
- BSCMAKE, reference
- Microsoft Browse Information Maintenance Utility
- browse windows
- browse information files (.bsc), building
- .bsc files, building
- bsc files, building
- BSCMAKE
ms.assetid: b97ad994-1355-4809-98db-6abc12c6fb13
ms.openlocfilehash: 72ad297ee5a24bc0c7ffd3ed25959031d0b8a309
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220562"
---
# <a name="bscmake-reference"></a>Referência de BSCMAKE

> [!WARNING]
> Embora BSCMAKE ainda está instalado com o Visual Studio, ele não é mais usado pelo IDE. Desde o Visual Studio 2008, as informações de símbolo e procura são armazenadas automaticamente em um arquivo. sdf de SQL Server na pasta da solução.

O utilitário de manutenção de informações de procura da Microsoft (BSCMAKE. EXE) cria um arquivo de informações de procura (. bsc) dos arquivos. SBR criados durante a compilação. Determinadas ferramentas de terceiros usam arquivos. BSC para análise de código.

Quando você compila seu programa, você pode criar um arquivo de informações de procura para o seu programa automaticamente, usando BSCMAKE para criar o arquivo. Você não precisa saber como executar BSCMAKE se você criar o arquivo de informações de procura no ambiente de desenvolvimento do Visual Studio. No entanto, você talvez queira ler este tópico para entender as opções disponíveis.

Se você compilar seu programa fora do ambiente de desenvolvimento, você ainda pode criar um. bsc personalizado que você pode examinar no ambiente. Execute BSCMAKE em arquivos. SBR que você criou durante a compilação.

> [!NOTE]
>  Você pode iniciar essa ferramenta apenas de prompt de comando do desenvolvedor do Visual Studio. Você não pode iniciá-lo em um prompt de comando do sistema ou no Explorador de arquivos.

Esta seção inclui os seguintes tópicos:

- [Compilando arquivos de informações de navegação: visão geral](building-browse-information-files-overview.md)

- [Criação de um arquivo. bsc](building-a-dot-bsc-file.md)

- [Linha de comando BSCMAKE](bscmake-command-line.md)

- [Arquivo de comando BSCMAKE](bscmake-command-file-response-file.md)

- [Opções de BSCMAKE](bscmake-options.md)

- [Códigos de saída BSCMAKE](bscmake-exit-codes.md)

## <a name="see-also"></a>Consulte também

[Ferramentas de Build do MSVC adicionais](c-cpp-build-tools.md)
