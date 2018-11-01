---
title: strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l
ms.date: 11/04/2016
apiname:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- strxfrm
- _tcsxfrm
- wcsxfrm
helpviewer_keywords:
- strxfrm_l function
- _tcsxfrm function
- _strxfrm_l function
- strxfrm function
- wcsxfrm_l function
- wcsxfrm function
- string comparison [C++], transforming strings
- tcsxfrm function
- strings [C++], comparing locale
- _wcsxfrm_l function
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
ms.openlocfilehash: 4e4f5bb6639cbeee0f004f94f09177c08394d43e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590977"
---
# <a name="strxfrm-wcsxfrm-strxfrml-wcsxfrml"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l

Transforme uma cadeia de caracteres com base nas informações específicas à localidade.

## <a name="syntax"></a>Sintaxe

```C
size_t strxfrm(
   char *strDest,
   const char *strSource,
   size_t count
);
size_t wcsxfrm(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
size_t _strxfrm_l(
   char *strDest,
   const char *strSource,
   size_t count,
   _locale_t locale
);
size_t wcsxfrm_l(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parâmetros

*strDest*<br/>
Cadeia de caracteres de destino.

*strSource*<br/>
Cadeia de caracteres de origem.

*count*<br/>
Número máximo de caracteres a serem colocados na *strDest*.

*locale*<br/>
A localidade a ser usada.

## <a name="return-value"></a>Valor de retorno

Retorna o tamanho da cadeia de caracteres transformada, sem contar o caractere nulo de terminação. Se o valor de retorno é maior que ou igual a *contagem*, o conteúdo dos *strDest* é imprevisível. Em um erro, cada função define **errno** e retorna **INT_MAX**. Para um caractere inválido **errno** é definido como **EILSEQ**.

## <a name="remarks"></a>Comentários

O **strxfrm** função transforma a cadeia de caracteres apontada por *strSource* em um novo formato agrupado que é armazenado no *strDest*. Não mais do que *contagem* caracteres, incluindo o caractere nulo, são transformados e colocados na cadeia de caracteres resultante. A transformação é feita usando a localidade **LC_COLLATE** configuração de categoria. Para obter mais informações sobre **LC_COLLATE**, consulte [setlocale](setlocale-wsetlocale.md). **strxfrm** usa a localidade atual de seu comportamento dependente da localidade; **strxfrm_l** é idêntico, exceto que ele usa a localidade passada em vez da localidade atual. Para obter mais informações, consulte [Localidade](../../c-runtime-library/locale.md).

Após a transformação, uma chamada para **strcmp** com as duas cadeias de caracteres transformadas produz resultados idênticos aos de uma chamada para **strcoll** aplicado para as duas cadeias de caracteres originais. Assim como acontece com **strcoll** e **stricoll**, **strxfrm** manipula automaticamente as cadeias de caracteres multibyte conforme apropriado.

**wcsxfrm** é uma versão de caractere largo de **strxfrm**; os argumentos de cadeia de caracteres de **wcsxfrm** são ponteiros de caractere largo. Para **wcsxfrm**após a transformação de cadeia de caracteres, uma chamada para **wcscmp** com as duas cadeias de caracteres transformadas produz resultados idênticos aos de uma chamada para **wcscoll** aplicada para o cadeias de caracteres de dois originais. **wcsxfrm** e **strxfrm** se comportam de forma idêntica caso contrário. **wcsxfrm** usa a localidade atual de seu comportamento dependente da localidade; **wcsxfrm_l** usa a localidade passada em vez da localidade atual.

Essas funções validam seus parâmetros. Se *strSource* for um ponteiro nulo, ou *strDest* é um **nulo** ponteiro (a menos que contagem seja zero), ou se *contagem* é maior que **INT_MAX**, o manipulador de parâmetro inválido será invocado, conforme descrito em [validação de parâmetro](../../c-runtime-library/parameter-validation.md) . Se a execução puder continuar, essas funções definirão **errno** à **EINVAL** e retornar **INT_MAX**.

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina TCHAR.H|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

Na localidade “C”, a ordem dos caracteres no conjunto de caracteres (conjunto de caracteres ASCII) é a mesma que a ordem lexicográfica dos caracteres. No entanto, em outras localidades, a ordem de caracteres no conjunto de caracteres pode ser diferente da ordem lexicográfica de caracteres. Por exemplo, em algumas localidades europeias, o caractere “a” (valor 0x61) precede o caractere “&\#x00E4;” (valor 0xE4) no conjunto de caracteres, mas o caractere “ä” precede a caractere “a” lexicograficamente.

Em localidades para as quais o conjunto de caracteres e a ordem lexicográfica de caracteres diferem, use **strxfrm** nas cadeias de caracteres originais e, em seguida **strcmp** em cadeias de caracteres resultantes para produzir uma cadeia de caracteres lexicográfica comparação de acordo com a localidade atual **LC_COLLATE** configuração de categoria. Portanto, para comparar duas cadeias de caracteres lexicograficamente na localidade acima, use **strxfrm** em cadeias de caracteres originais, então **strcmp** nas cadeias de caracteres resultantes. Como alternativa, você pode usar **strcoll** vez **strcmp** nas cadeias de caracteres originais.

**strxfrm** é basicamente um wrapper em torno [LCMapString](/windows/desktop/api/winnls/nf-winnls-lcmapstringa) com **LCMAP_SORTKEY**.

O valor da expressão a seguir é o tamanho da matriz necessário para manter o **strxfrm** transformação da cadeia de caracteres de origem:

`1 + strxfrm( NULL, string, 0 )`

Na localidade "C", **strxfrm** é equivalente à seguinte:

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**strxfrm**|\<string.h>|
|**wcsxfrm**|\<string.h> ou \<wchar.h>|
|**_strxfrm_l**|\<string.h>|
|**_wcsxfrm_l**|\<string.h> ou \<wchar.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte também

[Conversão de Dados](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Localidade](../../c-runtime-library/locale.md)<br/>
[Manipulação de cadeias de caracteres](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Funções strcoll](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
