---
title: wctob
ms.date: 11/04/2016
apiname:
- wctob
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wctob
helpviewer_keywords:
- wide characters, converting
- wctob function
- characters, converting
ms.assetid: 46aec98b-c2f2-4e9d-9d89-7db99ba8a9a6
ms.openlocfilehash: 1d9dca16ca905afbc94d912a8083017ba9cc84e6
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522513"
---
# <a name="wctob"></a>wctob

Determina se um caractere largo corresponde a um caractere multibyte e retorna sua representação de caracteres multibyte.

## <a name="syntax"></a>Sintaxe

```C
int wctob(
   wint_t wchar
);
```

### <a name="parameters"></a>Parâmetros

*wchar*<br/>
A valor a ser movido.

## <a name="return-value"></a>Valor de retorno

Se **wctob** converte com êxito um caractere largo, ele retornará sua representação de caracteres multibyte somente se o caractere multibyte for exatamente um byte. Se **wctob** encontra um caractere largo que não é possível converter um caractere multibyte ou os caracteres multibyte não é exatamente um byte, ele retornará -1.

## <a name="remarks"></a>Comentários

O **wctob** função converte um caractere largo contido no *wchar* no caractere multibyte correspondente passado pelo retorno **int** valor, se o multibyte caractere é exatamente um byte.

Se **wctob** não foi bem-sucedida e nenhum caractere multibyte correspondente foi encontrado, a função define **errno** para **EILSEQ** e retornará -1.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**wctob**|\<wchar.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

Este programa ilustra o comportamento do **wcstombs** função.

```C
// crt_wctob.c
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    int     bChar = 0;
    wint_t  wChar = 0;

    // Set the corresponding wide character to exactly one byte.
    wChar = (wint_t)'A';

    bChar = wctob( wChar );
    if (bChar == WEOF)
    {
        printf( "No corresponding multibyte character was found.\n");
    }
    else
    {
        printf( "Determined the corresponding multibyte character to"
                " be \"%c\".\n", bChar);
    }
}
```

```Output
Determined the corresponding multibyte character to be "A".
```

## <a name="see-also"></a>Consulte também

[Conversão de Dados](../../c-runtime-library/data-conversion.md)<br/>
[Localidade](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
[WideCharToMultiByte](/windows/desktop/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
