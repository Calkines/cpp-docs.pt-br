---
title: _getc_nolock, _getwc_nolock
ms.date: 11/04/2016
api_name:
- _getc_nolock
- _getwc_nolock
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
- getc_nolock
- _gettc_nolock
- _getc_nolock
- getwc_nolock
- gettc_nolock
- _getwc_nolock
helpviewer_keywords:
- characters, reading
- _getc_nolock function
- _getwc_nolock function
- getwc_nolock function
- streams, reading characters from
- reading characters from streams
- getc_nolock function
- gettc_nolock function
- _gettc_nolock function
ms.assetid: eb37b272-e177-41c9-b077-12ce7ffd3b88
ms.openlocfilehash: f6c2da5297e07d82fdea96452c3282c19329f24f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955503"
---
# <a name="_getc_nolock-_getwc_nolock"></a>_getc_nolock, _getwc_nolock

Lê um caractere de um fluxo.

## <a name="syntax"></a>Sintaxe

```C
int _getc_nolock(
   FILE *stream
);
wint_t _getwc_nolock(
   FILE *stream
);
```

### <a name="parameters"></a>Parâmetros

*stream*<br/>
Fluxo de entrada.

## <a name="return-value"></a>Valor de retorno

Consulte [getc, getwc](getc-getwc.md).

## <a name="remarks"></a>Comentários

Essas funções são idênticas a **getc** e **getwc** , exceto que não bloqueiam o thread de chamada. Elas podem ser mais rápidas, porque não incorrem na sobrecarga de bloquear outros threads. Use estas funções apenas em contextos thread-safe, como aplicativos de thread único ou em que o escopo de chamada já trata do isolamento de threads.

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina Tchar.h|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_gettc_nolock**|**getc_nolock**|**getc_nolock**|**getwc_nolock**|

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**getc_nolock**|\<stdio.h>|
|**getwc_nolock**|\<stdio.h> ou \<wchar.h>|

Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_getc_nolock.c
// Use getc to read a line from a file.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;
    FILE* fp;

    // Read a single line from the file "crt_getc_nolock.txt".
    fopen_s(&fp, "crt_getc_nolock.txt", "r");
    if (!fp)
    {
       printf("Failed to open file crt_getc_nolock.txt.\n");
       exit(1);
    }

    for (i = 0; (i < 80) && ((ch = getc(fp)) != EOF)
                         && (ch != '\n'); i++)
    {
        buffer[i] = (char) ch;
    }

    // Terminate string with a null character
    buffer[i] = '\0';
    printf( "Input was: %s\n", buffer);

    fclose(fp);
}
```

### <a name="input-crt_getc_nolocktxt"></a>Entrada: crt_getc_nolock.txt

```Input
Line the first.
Line the second.
```

### <a name="output"></a>Saída

```Output
Input was: Line the first.
```

## <a name="see-also"></a>Consulte também

[E/S de fluxo](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
