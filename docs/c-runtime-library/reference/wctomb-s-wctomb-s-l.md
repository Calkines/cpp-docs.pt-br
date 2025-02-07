---
title: wctomb_s, _wctomb_s_l
ms.date: 11/04/2016
api_name:
- _wctomb_s_l
- wctomb_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wctomb_s
- _wctomb_s_l
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
ms.openlocfilehash: 329724ca0196e07397d4f0337a2bf0aa2db05c84
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957902"
---
# <a name="wctomb_s-_wctomb_s_l"></a>wctomb_s, _wctomb_s_l

Converte um caractere largo no caractere multibyte correspondente. Uma versão de [wctomb, _wctomb_l](wctomb-wctomb-l.md) com melhorias de segurança, conforme descrito em [Recursos de segurança no CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxe

```C
errno_t wctomb_s(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar
);
errno_t _wctomb_s_l(
   int *pRetValue,
   char *mbchar,
   size_t sizeInBytes,
   wchar_t wchar,
   _locale_t locale
);
```

### <a name="parameters"></a>Parâmetros

*pRetValue*<br/>
O número de bytes ou um código que indica o resultado.

*mbchar*<br/>
O endereço de um caractere multibyte.

*sizeInBytes*<br/>
Tamanho do buffer *mbchar*.

*wchar*<br/>
Um caractere largo.

*locale*<br/>
A localidade a ser usada.

## <a name="return-value"></a>Valor de retorno

Zero se for bem-sucedido ou um código de erro em caso de falha.

Condições de Erro

|*mbchar*|*sizeInBytes*|Valor retornado|*pRetValue*|
|--------------|-------------------|------------------|-----------------|
|**NULL**|>0|**EINVAL**|não modificado|
|qualquer|>**INT_MAX**|**EINVAL**|não modificado|
|qualquer|muito pequeno|**EINVAL**|não modificado|

Se qualquer uma das condições de erro acima ocorrer, o manipulador de parâmetro inválido será invocado, conforme descrito em [Validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, **wctomb** retornará **EINVAL** e definirá **errno** como **EINVAL**.

## <a name="remarks"></a>Comentários

A função **wctomb_s** converte seu argumento *WCHAR* para o caractere multibyte correspondente e armazena o resultado em *mbchar*. Você pode chamar a função de qualquer ponto, em qualquer programa.

Se **wctomb_s** converter o caractere largo em um caractere multibyte, ele colocará o número de bytes (que nunca é maior que **MB_CUR_MAX**) no caractere largo no número inteiro apontado por *pRetValue*. Se *WCHAR* for o caractere nulo de caractere largo (L ' \ 0 '), **wctomb_s** preencherá *pRetValue* com 1. Se o ponteiro de destino *mbchar* for **nulo**, **wctomb_s** colocará 0 em *pRetValue*. Se a conversão não for possível na localidade atual, **wctomb_s** colocará-1 em *pRetValue*.

**wctomb_s** usa a localidade atual para obter informações dependentes de localidade; **_wctomb_s_l** é idêntico, exceto pelo fato de que ele usa a localidade transmitida em seu lugar. Para obter mais informações, consulte [Localidade](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**wctomb_s**|\<stdlib.h>|
|**_wctomb_s_l**|\<stdlib.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

Este programa ilustra o comportamento da função **wctomb** .

```cpp
// crt_wctomb_s.cpp
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    int i;
    wchar_t wc = L'a';
    char *pmb = (char *)malloc( MB_CUR_MAX );

    printf_s( "Convert a wide character:\n" );
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );
    printf_s( "   Characters converted: %u\n", i );
    printf_s( "   Multibyte character: %.1s\n\n", pmb );
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
