---
title: _chmod, _wchmod
ms.date: 11/04/2016
apiname:
- _chmod
- _wchmod
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
- _chmod
- _wchmod
- wchmod
helpviewer_keywords:
- _chmod function
- wchmod function
- file permissions [C++]
- chmod function
- files [C++], changing permissions
- _wchmod function
ms.assetid: 92f7cb86-b3b0-4232-a599-b8c04a2f2c19
ms.openlocfilehash: 278ee1e6dda9e153b55676ce5c0ca389f383efd1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348465"
---
# <a name="chmod-wchmod"></a>_chmod, _wchmod

Altera as configurações de permissão de arquivo.

## <a name="syntax"></a>Sintaxe

```C
int _chmod( const char *filename, int pmode );
int _wchmod( const wchar_t *filename, int pmode );
```

### <a name="parameters"></a>Parâmetros

*filename*<br/>
Nome do arquivo existente.

*pmode*<br/>
Configuração de permissão para o arquivo.

## <a name="return-value"></a>Valor de retorno

Essas funções retornarão 0 se a configuração de permissão for alterada com êxito. Um valor de retorno de -1 indica falha. Se o arquivo especificado não pôde ser encontrado, **errno** é definido como **ENOENT**; se um parâmetro for inválido, **errno** é definido como **EINVAL**.

## <a name="remarks"></a>Comentários

O **chmod** função altera a configuração de permissão do arquivo especificado por *filename*. A configuração de permissão controla o acesso de leitura e gravação para o arquivo. A expressão de inteiro *pmode* contém uma ou ambas das seguintes constantes de manifesto, definidas em sys\stat.h.

| *pmode* | Significado |
|-|-|
| **\_S\_IREAD** | Somente a leitura é permitida. |
| **\_S\_IWRITE** | Gravação permitida. (Na verdade, permite leitura e gravação.) |
| **\_S\_IREAD** &#124; **\_S\_IWRITE** | Leitura e gravação permitidas. |

Quando as duas constantes são informadas, elas são unidas com o bit a bit ou operador (**\|**). Se a permissão de gravação não for fornecida, o arquivo será somente leitura. Observe que todos os arquivos são sempre legíveis; não é possível dar permissão somente gravação. Portanto, os modos **s_iwrite** e **s_iread** \| **s_iwrite** são equivalentes.

**wchmod** é uma versão de caractere largo de **chmod**; o *filename* argumento **wchmod** é uma cadeia de caracteres largos. **wchmod** e **chmod** se comportam de forma idêntica caso contrário.

Essa função valida seus parâmetros. Se *pmode* não é uma combinação de uma das constantes de manifesto nem incorporar um conjunto alternativo de constantes, a função simplesmente as ignorará. Se *filename* é **nulo**, o manipulador de parâmetro inválido será invocado, conforme descrito na [validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, **errno** é definido como **EINVAL** e a função retornará -1.

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina Tchar.h|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchmod**|**_chmod**|**_chmod**|**_wchmod**|

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|Cabeçalho opcional|
|-------------|---------------------|---------------------|
|**_chmod**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wchmod**|\<io.h> ou \<wchar.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_chmod.c
// This program uses _chmod to
// change the mode of a file to read-only.
// It then attempts to modify the file.
//

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

// Change the mode and report error or success
void set_mode_and_report(char * filename, int mask)
{
   // Check for failure
   if( _chmod( filename, mask ) == -1 )
   {
      // Determine cause of failure and report.
      switch (errno)
      {
         case EINVAL:
            fprintf( stderr, "Invalid parameter to chmod.\n");
            break;
         case ENOENT:
            fprintf( stderr, "File %s not found\n", filename );
            break;
         default:
            // Should never be reached
            fprintf( stderr, "Unexpected error in chmod.\n" );
       }
   }
   else
   {
      if (mask == _S_IREAD)
        printf( "Mode set to read-only\n" );
      else if (mask & _S_IWRITE)
        printf( "Mode set to read/write\n" );
   }
   fflush(stderr);
}

int main( void )
{

   // Create or append to a file.
   system( "echo /* End of file */ >> crt_chmod.c_input" );

   // Set file mode to read-only:
   set_mode_and_report("crt_chmod.c_input ", _S_IREAD );

   system( "echo /* End of file */ >> crt_chmod.c_input " );

   // Change back to read/write:
   set_mode_and_report("crt_chmod.c_input ", _S_IWRITE );

   system( "echo /* End of file */ >> crt_chmod.c_input " );
}
```

```Output

A line of text.
```

```Output

      A line of text.Mode set to read-only
Access is denied.
Mode set to read/write
```

## <a name="see-also"></a>Consulte também

[Manipulação de Arquivos](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[Funções _stat, _wstat](stat-functions.md)<br/>
