---
title: /PDBALTPATH (usar demarcador de PDB alternativo)
ms.date: 11/04/2016
f1_keywords:
- /pdbaltpath
helpviewer_keywords:
- .pdb files, path
- PDBALTPATH dumpbin option
- -PDBALTPATH dumpbin option
- /PDBALTPATH dumpbin option
- PDB files, path
ms.assetid: 72e200aa-e2c3-4ad8-b687-25528da1aaaf
ms.openlocfilehash: 660e39a97b9fed0c5a9228fe011e7c0fa2566e68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320026"
---
# <a name="pdbaltpath-use-alternate-pdb-path"></a>/PDBALTPATH (usar demarcador de PDB alternativo)

```
/PDBALTPATH:pdb_file_name
```

## <a name="arguments"></a>Arguments

*pdb_file_name*<br/>
O caminho e o nome de arquivo para o arquivo .pdb.

## <a name="remarks"></a>Comentários

Use essa opção para oferecer um local alternativo para o arquivo Program Database (.pdb) em um arquivo binário compilado. Normalmente, o vinculador registra o local do arquivo .pdb nos binários que o reproduzem. Você pode usar essa opção para oferecer um caminho e o nome de arquivo diferentes para o arquivo .pdb. As informações fornecidas com /PDBALTPATH não alteram o local ou o nome do arquivo .pdb real; o que muda são as informações que o vinculador grava no arquivo binário. Isso faz com que seja possível fornecer um caminho independente da estrutura do arquivo do computador da compilação. Dois usos comuns dessa opção são: oferecer um caminho de rede ou um arquivo sem informações de caminho.

O valor de *pdb_file_name* pode ser uma cadeia de caracteres arbitrária, uma variável de ambiente, ou **_PDB %**. O vinculador expandirá uma variável de ambiente, como **% SystemRoot %**, para seu valor. O vinculador define as variáveis de ambiente **% _PDB** e **_EXT %**. **% _PDB** expande para o nome de arquivo do arquivo. PDB real sem nenhuma informação de caminho e **_EXT %** é a extensão do executável gerado.

## <a name="see-also"></a>Consulte também

[Opções de DUMPBIN](dumpbin-options.md)<br/>
[/PDBPATH](pdbpath.md)
