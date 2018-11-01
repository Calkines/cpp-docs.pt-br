---
title: _create_locale, _wcreate_locale
ms.date: 11/04/2016
apiname:
- _create_locale
- __create_locale
- _wcreate_locale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- create_locale
- _create_locale
- __create_locale
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
ms.openlocfilehash: 0ede14d56dc093b83078bf28eb01f5b5c55d8949
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545919"
---
# <a name="createlocale-wcreatelocale"></a>_create_locale, _wcreate_locale

Cria um objeto de localidade.

## <a name="syntax"></a>Sintaxe

```C
_locale_t _create_locale(
   int category,
   const char *locale
);
_locale_t _wcreate_locale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>Parâmetros

*category*<br/>
Categoria.

*locale*<br/>
Especificador de localidade.

## <a name="return-value"></a>Valor de retorno

Se for um válida *localidade* e *categoria* forem fornecidos, retornará as configurações de localidade especificada como um **locale_t** objeto. As configurações de localidade atual do programa não são alteradas.

## <a name="remarks"></a>Comentários

O **create_locale** função permite que você crie um objeto que representa certas configurações específicas de região, para uso em versões específicas de localidade de muitas funções CRT (funciona com o **l** sufixo ). O comportamento é semelhante à **setlocale**, exceto que em vez de aplicar as configurações de localidade especificadas ao ambiente atual, as configurações são salvas em um **locale_t** estrutura que é retornada. O **locale_t** estrutura deve ser liberada usando [free_locale](free-locale.md) quando ele não for mais necessário.

**wcreate_locale** é uma versão de caractere largo de **create_locale**; o *localidade* argumento **wcreate_locale** é uma cadeia de caracteres largos. **wcreate_locale** e **create_locale** se comportam de forma idêntica caso contrário.

O *categoria* argumento especifica as partes do comportamento específico de localidade que são afetadas. Os sinalizadores usados para *categoria* e as partes do programa que afetam são mostrados na tabela a seguir.

|*categoria* sinalizador|Afeta|
|-|-|
**LC_ALL**|Todas as categorias, conforme listado abaixo.
**LC_COLLATE**|O **strcoll**, **stricoll**, **wcscoll**, **wcsicoll**, **strxfrm**, **_ strncoll**, **strnicoll**, **wcsncoll**, **wcsnicoll**, e **wcsxfrm** funções.
**LC_CTYPE**|As funções de manipulação de caracteres (exceto **isdigit**, **isxdigit**, **mbstowcs**, e **mbtowc**, que não são afetadas).
**LC_MONETARY**|Informações de formatação monetária retornadas pela **localeconv** função.
**LC_NUMERIC**|Caractere decimal para rotinas de saída formatadas (como **printf**), para as rotinas de conversão de dados e para as informações de formatação não-monetária retornadas pela **localeconv**. Além do caractere de vírgula decimal **LC_NUMERIC** separador de milhares de conjuntos e o agrupamento de controle de cadeia de caracteres retornada pela [localeconv](localeconv.md).
**LC_TIME**|O **strftime** e **wcsftime** funções.

Essa função valida o *categoria* e *localidade* parâmetros. Se o parâmetro category não for um dos valores fornecidos na tabela anterior ou se *localidade* é **nulo**, a função retornará **nulo**.

O *localidade* argumento é um ponteiro para uma cadeia de caracteres que especifica a localidade. Para obter informações sobre o formato do *localidade* argumento, consulte [nomes de localidades, idiomas e cadeias de caracteres de país/região](../../c-runtime-library/locale-names-languages-and-country-region-strings.md).

O *localidade* argumento pode assumir um nome de localidade, uma cadeia de caracteres de idioma, uma cadeia de caracteres de idioma e código de país/região, uma página de código, ou uma cadeia de caracteres de idioma, o código de país/região e página de código. O conjunto de nomes de localidade, idiomas, códigos de país/região e páginas de código disponíveis inclui tudo o que tem suporte na API NLS do Windows, com exceção das páginas de código que exigem mais de dois bytes por caractere – por exemplo, UTF-7 e UTF-8. Se você fornecer uma página de código como UTF-7 ou UTF-8 **create_locale** falhará e retornará **nulo**. O conjunto de nomes de localidades com suporte pelo **create_locale** descritos nos [nomes de localidades, idiomas e cadeias de caracteres de país/região](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). O conjunto de cadeias de caracteres de idioma e país/região com suporte pelo **create_locale** são listadas na [cadeias de caracteres de idioma](../../c-runtime-library/language-strings.md) e [cadeias de caracteres de país/região](../../c-runtime-library/country-region-strings.md).

Para obter mais informações sobre as configurações de localidade, consulte [setlocale, _wsetlocale](setlocale-wsetlocale.md).

O nome anterior dessa função, **__create_locale** (com dois sublinhados à esquerda), foi preterido.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**_create_locale**|\<locale.h>|
|**_wcreate_locale**|\<locale.h> ou \<wchar.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_create_locale.c
// Sets the current locale to "de-CH" using the
// setlocale function and demonstrates its effect on the strftime
// function.

#include <stdio.h>
#include <locale.h>
#include <time.h>

int main(void)
{
    time_t ltime;
    struct tm thetime;
    unsigned char str[100];
    _locale_t locale;

    // Create a locale object representing the German (Switzerland) locale
    locale = _create_locale(LC_ALL, "de-CH");
    time (&ltime);
    _gmtime64_s(&thetime, &ltime);

    // %#x is the long date representation, appropriate to
    // the current locale
    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In de-CH locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);

    // Create a locale object representing the default C locale
    locale = _create_locale(LC_ALL, "C");
    time(&ltime);
    _gmtime64_s(&thetime, &ltime);

    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In 'C' locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);
}
```

```Output
In de-CH locale, _strftime_l returns 'Samstag, 9. Februar 2002'
In 'C' locale, _strftime_l returns 'Saturday, February 09, 2002'
```

## <a name="see-also"></a>Consulte também

[Nomes de localidades, idiomas e cadeias de caracteres de país/região](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Cadeias de caracteres de idioma](../../c-runtime-library/language-strings.md)<br/>
[Cadeias de caracteres de país/região](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[Localidade](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funções strcoll](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
