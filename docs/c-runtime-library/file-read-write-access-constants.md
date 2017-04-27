---
title: "Constantes de acesso de leitura/gravação de arquivo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.constants.file
dev_langs:
- C++
helpviewer_keywords:
- read/write access constants
- write access constants
- access constants for file read/write
- constants [C++], file attributes
- file read/write access constants
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
caps.latest.revision: 6
author: corob-msft
ms.author: corob
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 93279d1399ebc2395c29f7aac674cb83ddad0048
ms.lasthandoff: 02/25/2017

---
# <a name="file-readwrite-access-constants"></a>Constantes de acesso de leitura/gravação de arquivo
## <a name="syntax"></a>Sintaxe  
  
```  
  
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Comentários  
 Essas constantes especificam o tipo de acesso ("a", "r" ou "w") solicitado para o arquivo. O [modo de translação](../c-runtime-library/file-translation-constants.md) ("b" ou "t") e o [modo commit-to-disk](../c-runtime-library/commit-to-disk-constants.md) ("c" ou "n") podem ser especificados com o tipo de acesso.  
  
 Os tipos de acesso são descritos abaixo.  
  
 **"a"**  
 Abre para gravação no final do arquivo (acréscimo); cria o arquivo primeiro se ele não existir. Todas as operações de gravação ocorrem no final do arquivo. Embora o ponteiro do arquivo possa ser reposicionado usando `fseek` ou **rewind**, ele é sempre movido de volta para o final do arquivo antes que qualquer operação de gravação seja realizada.  
  
 **"a+"**  
 Idem acima, mas também permite a leitura.  
  
 **"r"**  
 Abre para leitura. Se o arquivo não existir ou não puder ser encontrado, ocorrerá uma falha na chamada para abrir o arquivo.  
  
 **"r+"**  
 Abre para leitura e gravação. Se o arquivo não existir ou não puder ser encontrado, ocorrerá uma falha na chamada para abrir o arquivo.  
  
 **"w"**  
 Abre um arquivo vazio para gravação. Se o arquivo determinado existir, seus conteúdos são destruídos.  
  
 **"w+"**  
 Abre um arquivo vazio para leitura e gravação. Se o arquivo determinado existir, seus conteúdos são destruídos.  
  
 Quando o tipo "r+", "w+" ou "a+" é especificado, são permitidas leitura e gravação (diz-se que o arquivo está aberto para "atualização"). No entanto, quando você muda entre leitura e gravação, deve haver uma operação `fflush`, `fsetpos`, `fseek` ou **rewind** intermediária. A posição atual pode ser especificada para a operação `fsetpos` ou `fseek`.  
  
## <a name="see-also"></a>Consulte também  
 [_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)   
 [_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)   
 [Constantes globais](../c-runtime-library/global-constants.md)