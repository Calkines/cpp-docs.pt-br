---
title: _setmode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _setmode
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
- _setmode
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
caps.latest.revision: 23
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
ms.openlocfilehash: e1037e5dcdf75ffae6197a32d4be0c2d17c57d78
ms.lasthandoff: 02/25/2017

---
# <a name="setmode"></a>_setmode
Define o modo de tradução do arquivo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
int _setmode (  
   int fd,  
   int mode   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `fd`  
 Descritor de arquivo.  
  
 `mode`  
 Novo modo de conversão.  
  
## <a name="return-value"></a>Valor de retorno  
 Se bem-sucedido, retorna para o modo de conversão anterior.  
  
 Se parâmetros inválidos forem passados para essa função, o manipulador de parâmetro inválido será invocado, conforme descrito em [Validação de Parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, essa função retorna –1 e define `errno` para `EBADF`, que indica um descritor de arquivo inválido ou `EINVAL`, que indica um argumento `mode` inválido.  
  
 Para obter mais informações sobre esses e outros códigos de retorno, consulte [_doserrno, errno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentários  
 A função `_setmode` define para `mode` o modo de conversão do arquivo fornecido por `fd`. Passar `_O_TEXT` como `mode` define o modo de texto (ou seja, convertido). Combinações CR-LF (Retorno de carro–alimentação de linha) são convertidas para um único caractere de alimentação de linha na entrada. Os caracteres de alimentação de linha são convertidos para combinações CR-LF na saída. Passar `_O_BINARY` define o modo binário (não traduzido), em que essas conversões são suprimidas.  
  
 Você também pode passar `_O_U16TEXT`, `_O_U8TEXT` ou _`O_WTEXT` para habilitar o modo Unicode, como demonstrado no segundo exemplo mais adiante neste documento. `_setmode` normalmente é usado para modificar o modo de conversão padrão de `stdin` e `stdout`, mas você pode usá-lo em qualquer arquivo. Se você aplicar `_setmode` ao descritor de arquivo para um fluxo, chame `_setmode` antes de realizar alguma operação de entrada ou saída no fluxo.  
  
> [!CAUTION]
>  Se você gravar dados em um fluxo de arquivo, limpe explicitamente o código usando [fflush](../../c-runtime-library/reference/fflush.md) antes de usar `_setmode` para alterar o modo. Se você não limpar o código, pode ocorrer comportamento inesperado. Se você não tiver dados gravados no fluxo, não será preciso limpar o código.  
  
## <a name="requirements"></a>Requisitos  
  
|Rotina|Cabeçalho necessário|Cabeçalhos opcionais|  
|-------------|---------------------|----------------------|  
|`_setmode`|\<io.h>|\<fcntl.h>|  
  
 Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Exemplo  
  
```  
// crt_setmode.c  
// This program uses _setmode to change  
// stdin from text mode to binary mode.  
  
#include <stdio.h>  
#include <fcntl.h>  
#include <io.h>  
  
int main( void )  
{  
   int result;  
  
   // Set "stdin" to have binary mode:  
   result = _setmode( _fileno( stdin ), _O_BINARY );  
   if( result == -1 )  
      perror( "Cannot set mode" );  
   else  
      printf( "'stdin' successfully changed to binary mode\n" );  
}  
```  
  
```Output  
'stdin' successfully changed to binary mode  
```  
  
## <a name="example"></a>Exemplo  
  
```  
// crt_setmodeunicode.c  
// This program uses _setmode to change  
// stdout to Unicode. Cyrillic and Ideographic  
// characters will appear on the console (if  
// your console font supports those character sets).  
  
#include <fcntl.h>  
#include <io.h>  
#include <stdio.h>  
  
int main(void) {  
    _setmode(_fileno(stdout), _O_U16TEXT);  
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");  
    return 0;  
}  
```  
  
## <a name="net-framework-equivalent"></a>Equivalente ao .NET Framework  
  
-   [Classe System::IO::BinaryReader](https://msdn.microsoft.com/en-us/library/system.io.binaryreader.aspx)  
  
-   [Classe System::IO::TextReader](https://msdn.microsoft.com/en-us/library/system.io.textreader.aspx)  
  
## <a name="see-also"></a>Consulte também  
 [Manipulação de Arquivos](../../c-runtime-library/file-handling.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_open, _wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_set_fmode](../../c-runtime-library/reference/set-fmode.md)