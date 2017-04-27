---
title: rename, _wrename | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- rename
- _wrename
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wrename
- _trename
- Rename
dev_langs:
- C++
helpviewer_keywords:
- trename function
- directories [C++], renaming
- renaming directories
- names [C++], changing file
- _trename function
- rename function
- wrename function
- files [C++], renaming
- _wrename function
- names [C++], changing directory
- renaming files
ms.assetid: 9f0a6103-26a2-4dda-b14b-79a48946266a
caps.latest.revision: 9
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: da665c7e4829cd8bde8bc749e1dc8c1bf28b4e33
ms.lasthandoff: 02/25/2017

---
# <a name="rename-wrename"></a>rename, _wrename
Renomeie um arquivo ou diretório.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      int rename(  
   const char *oldname,  
   const char *newname   
);  
int _wrename(  
   const wchar_t *oldname,  
   const wchar_t *newname   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *oldname*  
 Ponteiro para o nome antigo.  
  
 *newname*  
 Ponteiro para o novo nome.  
  
## <a name="return-value"></a>Valor de retorno  
 Cada uma dessas funções retornará 0 em caso de êxito. Em caso de erro, a função retorna um valor diferente de zero e define `errno` para um dos seguintes valores:  
  
 `EACCES`  
 O arquivo ou diretório especificado por *newname* já existe ou pode não ser criado (caminho inválido) ou *oldname* é um diretório e *newname* especifica um caminho diferente.  
  
 `ENOENT`  
 O arquivo ou caminho especificado por *oldname* não foi encontrado.  
  
 `EINVAL`  
 Nome contém caracteres inválidos.  
  
 Para ver outros valores retornados possíveis, consulte [_doserrno, _errno, syserrlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentários  
 A função **rename** renomeia o arquivo ou o diretório especificado por *oldname* para o nome fornecido por *newname*. O nome antigo deve ser o caminho de um arquivo ou diretório existente. O novo nome não pode ser o nome de um arquivo ou diretório existente. Você pode usar **rename** para mover um arquivo de um diretório ou dispositivo para outro fornecendo um caminho diferente no argumento *newname*. No entanto, não é possível usar **rename** para mover um diretório. Diretórios podem ser renomeados, mas não movidos.  
  
 `_wrename` é uma versão de caractere largo de **_rename**; os argumentos para `_wrename` são cadeias de caracteres largas. Caso contrário, `_wrename` e **_rename** se comportam de forma idêntica.  
  
### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico  
  
|Rotina TCHAR.H|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_trename`|**rename**|**rename**|`_wrename`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rotina|Cabeçalho necessário|  
|-------------|---------------------|  
|**rename**|\<io.h> ou \<stdio.h>|  
|`_wrename`|\<stdio.h> ou \<wchar.h>|  
  
 Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md) na Introdução.  
  
## <a name="libraries"></a>Libraries  
 Todas as versões das [bibliotecas em tempo de execução C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Exemplo  
  
```  
// crt_renamer.c  
/* This program attempts to rename a file named  
 * CRT_RENAMER.OBJ to CRT_RENAMER.JBO. For this operation  
 * to succeed, a file named CRT_RENAMER.OBJ must exist and  
 * a file named CRT_RENAMER.JBO must not exist.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   int  result;  
   char old[] = "CRT_RENAMER.OBJ", new[] = "CRT_RENAMER.JBO";  
  
   /* Attempt to rename file: */  
   result = rename( old, new );  
   if( result != 0 )  
      printf( "Could not rename '%s'\n", old );  
   else  
      printf( "File '%s' renamed to '%s'\n", old, new );  
}  
```  
  
## <a name="output"></a>Saída  
  
```  
File 'CRT_RENAMER.OBJ' renamed to 'CRT_RENAMER.JBO'  
```  
  
## <a name="net-framework-equivalent"></a>Equivalente ao .NET Framework  
 [System::IO::File::Move](https://msdn.microsoft.com/en-us/library/system.io.file.move.aspx)  
  
## <a name="see-also"></a>Consulte também  
 [Manipulação de Arquivos](../../c-runtime-library/file-handling.md)