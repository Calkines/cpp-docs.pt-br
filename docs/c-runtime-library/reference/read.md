---
title: _read | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _read
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
- _read
dev_langs:
- C++
helpviewer_keywords:
- data [CRT]
- _read function
- read function
- data [C++], reading
- reading data [C++]
- files [C++], reading
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
caps.latest.revision: 15
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
ms.openlocfilehash: 0945829735b9996bca32780bb34385d3e19ffa57
ms.lasthandoff: 02/25/2017

---
# <a name="read"></a>_read
Lê dados de um arquivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      int _read(  
   int fd,  
   void *buffer,  
   unsigned int count   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fd`  
 Descritor de arquivo que se refere ao arquivo aberto.  
  
 *buffer*  
 Local de armazenamento de dados.  
  
 *count*  
 O número máximo de bytes.  
  
## <a name="return-value"></a>Valor de retorno  
 _**read** retorna o número de bytes lidos, que poderá ser menor que *count* se houver menos bytes de *count* restantes no arquivo ou se o arquivo foi aberto no modo de texto, quando então o par CR-LF (retorno de carro‑alimentação de linha) será substituído por um caractere único de avanço de linha. Apenas o caractere de avanço de linha único é contado no valor retornado. A substituição não afeta o ponteiro do arquivo.  
  
 Se a função tentar ler o final do arquivo, ela retornará 0. Se `fd` for inválido, arquivo não será aberto para leitura ou o arquivo será bloqueado, o manipulador de parâmetro inválido será invocado, conforme descrito em [Validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, a função retornará um valor -1 e definirá `errno` como `EBADF`.  
  
 Se *buffer* for **NULL**, o manipulador do parâmetro inválido será invocado. Se a execução tiver permissão para continuar, a função retornará -1 e `errno` será definido como `EINVAL`.  
  
 Para obter mais informações sobre este e outros códigos retornados, consulte [_doserrno, errno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentários  
 A função `_read` lê um máximo de *count * bytes no *buffer* do arquivo associado a `fd`. A operação de leitura começa na posição atual do ponteiro de arquivo associado ao arquivo em questão. Após a operação de leitura, o ponteiro do arquivo aponta para o próximo caractere não lido.  
  
 Se o arquivo foi aberto no modo de texto, a leitura termina quando `_read` encontrar um caractere CTRL+Z, que é tratado como um indicador de fim de arquivo. Use [_lseek](../../c-runtime-library/reference/lseek-lseeki64.md) para limpar o indicador de fim do arquivo.  
  
## <a name="requirements"></a>Requisitos  
  
|Rotina|Cabeçalho necessário|  
|-------------|---------------------|  
|`_read`|\<io.h>|  
  
 Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md) na Introdução.  
  
## <a name="libraries"></a>Libraries  
 Todas as versões das [bibliotecas em tempo de execução C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Exemplo  
  
```  
// crt_read.c  
/* This program opens a file named crt_read.txt  
 * and tries to read 60,000 bytes from  
 * that file using _read. It then displays the  
 * actual number of bytes read.  
 */  
  
#include <fcntl.h>      /* Needed only for _O_RDWR definition */  
#include <io.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <share.h>  
  
char buffer[60000];  
  
int main( void )  
{  
   int fh;  
   unsigned int nbytes = 60000, bytesread;  
  
   /* Open file for input: */  
   if( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ) )  
   {  
      perror( "open failed on input file" );  
      exit( 1 );  
   }  
  
   /* Read in input: */  
   if( ( bytesread = _read( fh, buffer, nbytes ) ) <= 0 )  
      perror( "Problem reading file" );  
   else  
      printf( "Read %u bytes from file\n", bytesread );  
  
   _close( fh );  
}  
```  
  
## <a name="input-crtreadtxt"></a>Entrada: crt_read.txt  
  
```  
Line one.  
Line two.  
```  
  
## <a name="output"></a>Saída  
  
```  
Read 19 bytes from file  
```  
  
## <a name="see-also"></a>Consulte também  
 [E/S de nível inferior](../../c-runtime-library/low-level-i-o.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fread](../../c-runtime-library/reference/fread.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_write](../../c-runtime-library/reference/write.md)