---
title: Limites de campo do demarcador
ms.date: 11/04/2016
f1_keywords:
- _MAX_EXT
- _MAX_DIR
- _MAX_PATH
- _MAX_FNAME
- _MAX_DRIVE
helpviewer_keywords:
- path field constants
- MAX_FNAME constant
- _MAX_DIR constant
- _MAX_DRIVE constant
- paths, maximum limit
- _MAX_PATH constant
- MAX_DRIVE constant
- _MAX_FNAME constant
- _MAX_EXT constant
- MAX_DIR constant
- MAX_EXT constant
ms.assetid: 2b5d0e43-1347-45b4-8397-24a8a45c444e
ms.openlocfilehash: 89609de3fc5584a960480bff83566f5e38c8be1f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477526"
---
# <a name="path-field-limits"></a>Limites de campo do demarcador

## <a name="syntax"></a>Sintaxe

```cpp
#include <stdlib.h>
```

## <a name="remarks"></a>Comentários

Essas constantes definem o comprimento máximo para o caminho e para os campos individuais dentro do caminho.

|Constante|Significado|
|--------------|-------------|
|`_MAX_DIR`|Comprimento máximo do componente de diretório|
|`_MAX_DRIVE`|Comprimento máximo do componente de unidade|
|`_MAX_EXT`|Comprimento máximo do componente de extensão|
|`_MAX_FNAME`|Comprimento máximo do componente de nome do arquivo|
|`_MAX_PATH`|Comprimento máximo do caminho completo|

> [!NOTE]
> O tempo de execução C dá suporte a comprimentos de caminho com até 32.768 caracteres; porém, o suporte a esses caminhos mais longos depende do sistema operacional, especificamente do sistema de arquivos. A soma dos campos não deve exceder `_MAX_PATH` para compatibilidade completa com versões anteriores em relação a sistemas de arquivos FAT32. O sistema de arquivos NTFS do Windows é compatível com caminhos com até 32768 caracteres de comprimento, mas somente quando as APIs Unicode são usadas. Ao usar nomes de caminho longos, faça um prefixo para o caminho com os caracteres \\ \\? \ e use as versões Unicode das funções de tempo de execução C.

## <a name="see-also"></a>Consulte também

[Constantes globais](../c-runtime-library/global-constants.md)