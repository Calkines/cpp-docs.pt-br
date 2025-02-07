---
title: _popen, _wpopen
ms.date: 11/04/2016
api_name:
- _popen
- _wpopen
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tpopen
- popen
- wpopen
- _popen
- _wpopen
- _tpopen
helpviewer_keywords:
- tpopen function
- pipes, creating
- _popen function
- _tpopen function
- popen function
- wpopen function
- _wpopen function
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
ms.openlocfilehash: 0e58ffd523c6919d70c68454f3547736afdef565
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950993"
---
# <a name="_popen-_wpopen"></a>_popen, _wpopen

Cria um pipe e executa um comando.

> [!IMPORTANT]
> Esta API não pode ser usada em aplicativos executados no Tempo de Execução do Windows. Para obter mais informações, confira [Funções do CRT sem suporte em aplicativos da Plataforma Universal do Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxe

```C
FILE *_popen(
    const char *command,
    const char *mode
);
FILE *_wpopen(
    const wchar_t *command,
    const wchar_t *mode
);
```

### <a name="parameters"></a>Parâmetros

*command*<br/>
O comando a ser executado.

*modo*<br/>
Modo do fluxo retornado.

## <a name="return-value"></a>Valor de retorno

Retorna um fluxo associado a uma extremidade do pipe criado. A outra extremidade do pipe está associada à entrada ou saída padrão do comando gerado. As funções retornam **Nulo** em caso de erro. Se o erro for um parâmetro inválido, como se o *comando* ou o *modo* for um ponteiro nulo, ou o *modo* não for um modo válido, **errno** será definido como **EINVAL**. Consulte a seção Comentários para ver os modos válidos.

Para obter informações sobre esses e outros códigos de erro, consulte [_doserrno, errno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentários

A função **_popen** cria um pipe e executa de forma assíncrona uma cópia gerada do processador de comando com o *comando*de cadeia de caracteres especificado. A cadeia de caracteres *mode* especifica o tipo de acesso solicitado da seguinte maneira.

|Modo de Acesso|Descrição|
|-|-|
|**"r"**|O processo de chamada pode ler a saída padrão do comando gerado usando o fluxo retornado.|
|**"w"**|O processo de chamada pode gravar na entrada padrão do comando gerado usando o fluxo retornado.|
|**"b"**|Abrir no modo binário.|
|**"t"**|Abrir no modo de texto.|

> [!NOTE]
> Se usado em um programa do Windows, a função **_popen** retorna um ponteiro de arquivo inválido que faz com que o programa pare de responder indefinidamente. **_popen** funciona corretamente em um aplicativo de console. Para criar um aplicativo do Windows que redireciona entrada e saída, consulte [criando um processo filho com entrada e saída redirecionadas](/windows/win32/ProcThread/creating-a-child-process-with-redirected-input-and-output) no SDK do Windows.

**_wpopen** é uma versão de caractere largo do **_popen**; o argumento *path* para **_wpopen** é uma cadeia de caracteres largos. **_wpopen** e **_popen** se comportam de outra forma.

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina Tchar.h|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen**|**_popen**|**_popen**|**_wpopen**|

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**_popen**|\<stdio.h>|
|**_wpopen**|\<stdio.h> ou \<wchar.h>|

Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Libraries

Todas as versões das [bibliotecas em tempo de execução C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemplo

```C
// crt_popen.c
/* This program uses _popen and _pclose to receive a
* stream of text from a system process.
*/

#include <stdio.h>
#include <stdlib.h>

int main( void )
{

   char   psBuffer[128];
   FILE   *pPipe;

        /* Run DIR so that it writes its output to a pipe. Open this
         * pipe with read text attribute so that we can read it
         * like a text file.
         */

   if( (pPipe = _popen( "dir *.c /on /p", "rt" )) == NULL )
      exit( 1 );

   /* Read pipe until end of file, or an error occurs. */

   while(fgets(psBuffer, 128, pPipe))
   {
      printf(psBuffer);
   }

   /* Close pipe and print return value of pPipe. */
   if (feof( pPipe))
   {
     printf( "\nProcess returned %d\n", _pclose( pPipe ) );
   }
   else
   {
     printf( "Error: Failed to read the pipe to the end.\n");
   }
}
```

### <a name="sample-output"></a>Saída de Exemplo

Essa saída supõe que haja apenas um arquivo no diretório atual com uma extensão de nome de arquivo .c.

```Output
Volume in drive C is CDRIVE
Volume Serial Number is 0E17-1702

Directory of D:\proj\console\test1

07/17/98  07:26p                   780 popen.c
               1 File(s)            780 bytes
                             86,597,632 bytes free

Process returned 0
```

## <a name="see-also"></a>Consulte também

[Controle de processo e de ambiente](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pclose](pclose.md)<br/>
[_pipe](pipe.md)<br/>
