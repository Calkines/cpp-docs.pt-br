---
title: Variáveis de ambiente LINK
ms.date: 11/04/2016
f1_keywords:
- link
helpviewer_keywords:
- variables, environment
- LINK tool [C++], environment variables
- LIB environment variable
- environment variables [C++], LINK
ms.assetid: 9a3d3291-0cc4-4a7d-9d50-80e351b90708
ms.openlocfilehash: 3a398787530794f5a08d6cd122e55c305e265062
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434405"
---
# <a name="link-environment-variables"></a>Variáveis de ambiente LINK

A ferramenta LINK usa as seguintes variáveis de ambiente:

- LINK e \_LINK\_, se definido. A ferramenta LINK precede as opções e argumentos definidos na variável de ambiente LINK e acrescenta as opções e argumentos definidos na \_LINK\_ variável de ambiente para os argumentos de linha de comando antes do processamento.

- LIB, se definido. As ferramentas LINK usa o caminho do LIB ao pesquisar por um objeto, biblioteca ou outro arquivo especificado na linha de comando ou pelo [/base](../../build/reference/base-base-address.md) opção. Ele também usa o caminho do LIB para localizar um arquivo. PDB chamado em um objeto. A variável LIB pode conter uma ou mais especificações de caminho, separadas por ponto e vírgula. Um caminho deve apontar para o subdiretório \lib de sua instalação do Visual C++.

- CAMINHO, se a ferramenta precisa ser executado CVTRES e não é possível localizar o arquivo no mesmo diretório que o próprio LINK. (O LINK exige CVTRES vincular um arquivo. res). CAMINHO deve apontar para o subdiretório \bin de sua instalação do Visual C++.

- TMP, especifique um diretório ao vincular arquivos OMF ou. res.

## <a name="see-also"></a>Consulte também

[Definindo opções de vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opções do vinculador](../../build/reference/linker-options.md)<br/>
[Compilar código C/C++ na linha de comando](../../build/building-on-the-command-line.md)<br/>
[Definir o caminho e variáveis de ambiente para builds de linha de comando](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)
