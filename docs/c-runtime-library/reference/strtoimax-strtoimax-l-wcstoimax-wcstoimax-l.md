---
title: strtoimax, _strtoimax_l, wcstoimax, _wcstoimax_l
ms.date: 11/04/2016
apiname:
- wcstoimax
- _wcstoimax_l
- _strtoimax_l
- strtoimax
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
- wcstoimax
- _tcstoimax
- strtoimax
- _wcstoimax_l
- _strtoimax_l
- _tcstoimax_l
helpviewer_keywords:
- strtoimax funciton
- conversion functions
- _strtoimax_l function
- _wcstoimax_l function
- wcstoimax function
ms.assetid: 4530d3dc-aaac-4a76-b7cf-29ae3c98d0ae
ms.openlocfilehash: e0a320f90b2c0f8653109a6ae0056c4c0cdd7455
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578146"
---
# <a name="strtoimax-strtoimaxl-wcstoimax-wcstoimaxl"></a>strtoimax, _strtoimax_l, wcstoimax, _wcstoimax_l

Converte uma cadeia de caracteres em um valor inteiro do maior tipo de inteiro com sinal.

## <a name="syntax"></a>Sintaxe

```C
intmax_t strtoimax(
   const char *strSource,
   char **endptr,
   int base
);
intmax_t wcstoimax(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
intmax_t _strtoimax_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
intmax_t _wcstoimax_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parâmetros

*strSource*<br/>
Cadeia de caracteres terminada em nulo a ser convertida.

*endptr*<br/>
Ponteiro para o caractere que interrompe o exame.

*base*<br/>
O número base a ser usado.

*locale*<br/>
A localidade a ser usada.

## <a name="return-value"></a>Valor de retorno

**strtoimax** retorna o valor que é representado na cadeia de caracteres *strSource*, exceto quando a representação causaria um estouro — nesse caso, ele retorna **INTMAX_MAX** ou **INTMAX_MIN**, e **errno** está definido como **ERANGE**. A função retorna 0, se nenhuma conversão pode ser realizada. **wcstoimax** retorna valores de maneira semelhante a **strtoimax**.

**INTMAX_MAX** e **INTMAX_MIN** são definidos em stdint. h.

Se *strSource* é **nulo** ou o *base* for diferente de zero e menos que 2 ou maior que 36, **errno** está definido como **EINVAL** .

Para obter mais informações sobre os códigos de retorno, consulte [errno, _doserrno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentários

O **strtoimax** função converte *strSource* para um **intmax_t**. A versão de caractere largo de **strtoimax** é **wcstoimax**; sua *strSource* argumento é uma cadeia de caracteres largos. Caso contrário, essas funções se comportam de forma idêntica. Ambas as funções param de ler a cadeia de caracteres *strSource* no primeiro caractere que não reconhecem como parte de um número. Isso pode ser o caractere nulo de terminação ou pode ser o primeiro caractere numérico que é maior que ou igual a *base*.

A localidade **LC_NUMERIC** configuração de categoria determina o reconhecimento do caractere fracionário em *strSource*; para obter mais informações, consulte [setlocale, wsetlocale](setlocale-wsetlocale.md). As funções que não têm o **l** sufixo usam a localidade atual; **strtoimax_l** e **wcstoimax_l** são idênticas às funções correspondentes que não têm o **l** sufixo, exceto que eles usam a localidade que passado. Para obter mais informações, consulte [Localidade](../../c-runtime-library/locale.md).

Se *endptr* não está **nulo**, um ponteiro para o caractere que parou a verificação é armazenado no local apontado pela *endptr*. Se nenhuma conversão puder ser executada (Nenhum dígito válido foi encontrado ou uma base inválida foi especificada), o valor de *strSource* é armazenado no local apontado por *endptr*.

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina TCHAR.H|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoimax**|**strtoimax**|**strtoimax**|**wcstoimax**|
|**_tcstoimax_l**|**strtoimax_l**|**_strtoimax_l**|**_wcstoimax_l**|

**strtoimax** espera *strSource* para apontar para uma cadeia de caracteres da seguinte forma:

> [*espaço em branco*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*dígitos* &#124; *letras*]  

Um *espaço em branco* pode consistir em caracteres de espaço ou tabulação, que são ignorados; *dígitos* são um ou mais dígitos decimais; *letras* são um ou mais das letras 'a' a 'z' (ou 'A' a 'Z'). O primeiro caractere que não é adequado a esse formato interrompe o exame. Se *base* está entre 2 e 36, ele será usado como a base do número. Se *base* for 0, os caracteres iniciais da cadeia de caracteres apontada por *strSource* são usados para determinar a base. Se o primeiro caractere for '0' e o segundo caractere não for 'x' nem 'X', a cadeia de caracteres será interpretada como um inteiro octal. Se o primeiro caractere for '0' e o segundo caractere for 'x' ou 'X', a cadeia de caracteres será interpretada como um inteiro hexadecimal. Se o primeiro caractere for de '1' até '9', a cadeia de caracteres será interpretada como um inteiro hexadecimal. As letras 'a' a 'z' (ou 'A' a 'Z') recebem os valores 10 a 35; somente são permitidas letras cujos valores atribuídos são menores que *base*. O primeiro caractere fora do intervalo da base interrompe o exame. Por exemplo, se *base* é 0 e o primeiro caractere verificado é '0', é considerado um inteiro octal e um caractere '8' ou '9' interromperia a verificação.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**strtoimax**, **strtoimax_l**, **wcstoimax**, **wcstoimax_l**|\<inttypes.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte também

[Conversão de Dados](../../c-runtime-library/data-conversion.md)<br/>
[Localidade](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funções de valor de cadeia de caracteres para numérico](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoumax, _strtoumax_l, wcstoumax, _wcstoumax_l](strtoumax-strtoumax-l-wcstoumax-wcstoumax-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
