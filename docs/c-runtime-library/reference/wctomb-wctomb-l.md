---
title: wctomb, _wctomb_l
ms.date: 11/04/2016
api_name:
- _wctomb_l
- wctomb
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
- api-ms-win-crt-convert-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctomb
helpviewer_keywords:
- string conversion, wide characters
- wide characters, converting
- _wctomb_l function
- wctomb function
- wctomb_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 4a543f0e-5516-4d81-8ff2-3c5206f02ed5
ms.openlocfilehash: 195105618c75bd2a3a493f169fca4c2d3d4ebd62
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944996"
---
# <a name="wctomb-_wctomb_l"></a>wctomb, _wctomb_l

Converta um caractere largo para o caractere multibyte correspondente. Estão disponíveis versões mais seguras dessas funções; consulte [wctomb_s, _wctomb_s_l](wctomb-s-wctomb-s-l.md).

## <a name="syntax"></a>Sintaxe

```C
int wctomb(
   char *mbchar,
   wchar_t wchar
);
int _wctomb_l(
   char *mbchar,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>Parâmetros

*mbchar*<br/>
O endereço de um caractere multibyte.

*wchar*<br/>
Um caractere largo.

## <a name="return-value"></a>Valor de retorno

Se **wctomb** converter o caractere largo em um caractere multibyte, ele retornará o número de bytes (que nunca é maior que **MB_CUR_MAX**) no caractere largo. Se *WCHAR* for o caractere nulo de caractere largo (L ' \ 0 '), **wctomb** retornará 1. Se o ponteiro de destino *mbchar* for **nulo**, **wctomb** retornará 0. Se a conversão não for possível na localidade atual, **wctomb** retornará-1 e **errno** será definido como **EILSEQ**.

## <a name="remarks"></a>Comentários

A função **wctomb** converte seu argumento *WCHAR* para o caractere multibyte correspondente e armazena o resultado em *mbchar*. Você pode chamar a função de qualquer ponto, em qualquer programa. **wctomb** usa a localidade atual para qualquer comportamento dependente de localidade; **_wctomb_l** é idêntico ao **wctomb** , exceto pelo fato de que ele usa a localidade transmitida em seu lugar. Para obter mais informações, consulte [Localidade](../../c-runtime-library/locale.md).

**wctomb** valida seus parâmetros. Se *mbchar* for **NULL**, o manipulador de parâmetro inválido será invocado, conforme descrito em [validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, **errno** será definido como **EINVAL** e a função retornará-1.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**wctomb**|\<stdlib.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

Este programa ilustra o comportamento da função wctomb.

```cpp
// crt_wctomb.cpp
// compile with: /W3
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int i;
   wchar_t wc = L'a';
   char *pmb = (char *)malloc( MB_CUR_MAX );

   printf( "Convert a wide character:\n" );
   i = wctomb( pmb, wc ); // C4996
   // Note: wctomb is deprecated; consider using wctomb_s
   printf( "   Characters converted: %u\n", i );
   printf( "   Multibyte character: %.1s\n\n", pmb );
}
```

```Output
Convert a wide character:
   Characters converted: 1
   Multibyte character: a
```

## <a name="see-also"></a>Consulte também

[Conversão de Dados](../../c-runtime-library/data-conversion.md)<br/>
[Localidade](../../c-runtime-library/locale.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[WideCharToMultiByte](/windows/win32/api/stringapiset/nf-stringapiset-widechartomultibyte)<br/>
