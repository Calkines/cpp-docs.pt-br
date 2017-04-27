---
title: _open_osfhandle | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _open_osfhandle
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _open_osfhandle
- open_osfhandle
dev_langs:
- C++
helpviewer_keywords:
- open_osfhandle function
- file handles [C++], associating
- _open_osfhandle function
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 9b6081c6e9c5cb6f21ac3fd7e51446bb45b00283
ms.lasthandoff: 02/25/2017

---
# <a name="openosfhandle"></a>_open_osfhandle
Associa um descritor de arquivo de tempo de execução C a um identificador de arquivo do sistema operacional existente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      int _open_osfhandle (  
   intptr_t osfhandle,  
   int flags   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `osfhandle`  
 Identificador de arquivo do sistema operacional.  
  
 `flags`  
 Tipos de operações permitidas.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, `_open_osfhandle` retornará um descritor de arquivo de tempo de execução C. Caso contrário, retornará –1.  
  
## <a name="remarks"></a>Comentários  
 A função `_open_osfhandle` aloca um descritor de arquivo de tempo de execução C e o associa ao identificador de arquivo do sistema operacional especificado pelo `osfhandle`. O argumento `flags` é uma expressão inteira formada por uma ou mais constantes de manifesto definidas em Fcntl.h. Quando duas ou mais constantes de manifesto são usadas para formar o argumento `flags`, as constantes são combinadas ao operador OR bit a bit ( **&#124;** ).  
  
 Fcntl.h define as seguintes constantes de manifesto.  
  
 **_O_APPEND**  
 Posiciona um ponteiro de arquivo no final do arquivo, antes de cada operação de gravação.  
  
 **_O_RDONLY**  
 Abre o arquivo para somente leitura.  
  
 **_O_TEXT**  
 Abre o arquivo no modo de texto (convertido).  
  
 **_O_WTEXT**  
 Abre o arquivo no modo Unicode (convertido em UTF-16).  
  
 Para fechar um arquivo aberto com `_open_osfhandle`, chame `_close`. O identificador subjacente também é fechado por uma chamada para `_close`, portanto, não é necessário chamar a função `CloseHandle` do Win32 no identificador original.  
  
## <a name="requirements"></a>Requisitos  
  
|Rotina|Cabeçalho necessário|  
|-------------|---------------------|  
|`_open_osfhandle`|\<io.h>|  
  
 Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md) na Introdução.  
  
## <a name="libraries"></a>Libraries  
 Todas as versões das [bibliotecas em tempo de execução C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="net-framework-equivalent"></a>Equivalente ao .NET Framework  
 [System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)  
  
## <a name="see-also"></a>Consulte também  
 [Manipulação de Arquivos](../../c-runtime-library/file-handling.md)