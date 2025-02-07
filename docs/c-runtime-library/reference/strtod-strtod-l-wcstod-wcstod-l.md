---
title: strtod, _strtod_l, wcstod, _wcstod_l
ms.date: 10/20/2017
api_name:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
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
- _tcstod
- strtod
- wcstod
- _strtod_l
- _wcstod_l
- stdlib/strtod
- corecrt_wstdlib/wcstod
- stdlib/_strtod_l
- corecrt_wstdlib/_wcstod_l
helpviewer_keywords:
- wcstod_l function
- tcstod_l function
- _tcstod_l function
- strtod function
- _wcstod_l function
- wcstod function
- strtod_l function
- tcstod function
- _tcstod function
- _strtod_l function
- string conversion, to floating point values
ms.assetid: 0444f74a-ba2a-4973-b7f0-1d77ba88c6ed
ms.openlocfilehash: 5372525eb99dc9d39e31b10def0377c9aad5296c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946501"
---
# <a name="strtod-_strtod_l-wcstod-_wcstod_l"></a>strtod, _strtod_l, wcstod, _wcstod_l

Converte cadeias de caracteres em um valor de precisão dupla.

## <a name="syntax"></a>Sintaxe

```C
double strtod(
   const char *strSource,
   char **endptr
);
double _strtod_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
double wcstod(
   const wchar_t *strSource,
   wchar_t **endptr
);
double wcstod_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>Parâmetros

*strSource*<br/>
Cadeia de caracteres terminada em nulo a ser convertida.

*endptr*<br/>
Ponteiro para o caractere que interrompe a verificação.

*locale*<br/>
A localidade a ser usada.

## <a name="return-value"></a>Valor de retorno

**strtod** retorna o valor do número de ponto flutuante, exceto quando a representação causar um estouro, caso em que a função retorna +/-**HUGE_VAL**. O sinal de **HUGE_VAL** corresponde ao sinal do valor que não pode ser representado. **strtod** retornará 0 se nenhuma conversão puder ser executada ou se ocorrer um estouro negativo.

**wcstod** retorna valores de forma análoga ao **strtod**. Para ambas as funções, **errno** é definido como **ERANGE** se o estouro ou Subfluxo ocorre e o manipulador de parâmetro inválido é invocado, conforme descrito em [validação de parâmetro](../../c-runtime-library/parameter-validation.md). Consulte [_doserrno, errno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obter mais informações sobre esses e outros códigos de retorno.

## <a name="remarks"></a>Comentários

Cada função converte a cadeia de caracteres de entrada *strSource* em um **Double**. A função **strtod** converte *strSource* em um valor de precisão dupla. **strtod** interrompe a leitura da cadeia de caracteres *strSource* no primeiro caractere que ela não pode reconhecer como parte de um número. Este pode ser o caractere nulo de terminação. **wcstod** é uma versão de caractere largo do **strtod**; seu argumento *strSource* é uma cadeia de caracteres largos. Caso contrário, essas funções se comportam de forma idêntica.

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina TCHAR.H|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

A configuração de categoria **LC_NUMERIC** da localidade atual determina o reconhecimento do caractere de ponto de base em *strSource*. Para obter mais informações sobre, consulte [setlocale](setlocale-wsetlocale.md). As funções sem o sufixo **_L** usam a localidade atual; **_strtod_l** é idêntico ao **_strtod_l** , exceto pelo fato de que eles usam a *localidade* transmitida em seu lugar. Para obter mais informações, consulte [Localidade](../../c-runtime-library/locale.md).

Se *endptr* não for **NULL**, um ponteiro para o caractere que parou a verificação será armazenado no local apontado por *endptr*. Se nenhuma conversão puder ser executada (nenhum dígito válido foi encontrado ou uma base inválida foi especificada), o valor de *strSource* será armazenado no local apontado por *endptr*.

**strtod** espera que *strSource* aponte para uma cadeia de caracteres de uma das seguintes formas:

[*espaço em branco*] [*assinar*] { digits [ *dígitos*de &#124; *base* ] *dígitos*de *base* } [{**e** &#124; **e**} [*assinar*] *dígitos*] [*espaço em branco*] [*sinal*] {**0x** &#124; **0x**} {*hexdigits* [*Radix* *hexdigits*] &#124;  *Radix* *hexdigits*} [{**p** &#124; **p**} [*Sign*] *hexdigits*] [*espaço em branco*] [*Sign*] {**inf** &#124; **Infinity**} [*Whitespace*] [ *Sign*] **Nan** [*Sequence*]

O espaço em *branco* à esquerda opcional pode consistir em caracteres de espaço e tabulação, ignorados; o *sinal* é mais (+) ou menos (-); os *dígitos* são um ou mais dígitos decimais; *hexdigits* são um ou mais dígitos hexadecimais; *Radix* é o caractere de ponto fracionário, um ponto (.) na localidade padrão "C" ou o valor específico de localidade se a localidade atual for diferente ou quando a *localidade* for especificada; uma *sequência* é uma sequência de caracteres alfanuméricos ou de sublinhado. Nos formatos de número decimal e hexadecimal, se nenhum dígito aparecer antes do caractere de ponto de base, pelo menos um deve aparecer após o caractere de ponto de base. Na forma decimal, os dígitos decimais podem ser seguidos por um expoente, que consiste em uma letra introdutória (**e** ou **e**) e um inteiro assinado opcionalmente. Na forma hexadecimal, os dígitos hexadecimais podem ser seguidos por um expoente, que consiste em uma letra introdutória (**p** ou **p**) e um inteiro hexadecimal, opcionalmente assinado, que representa o expoente como uma potência de 2. Em qualquer forma, se nem uma parte de expoente nem um caractere de ponto de base aparecer, um caractere de ponto de base será considerado para seguir o último dígito na cadeia de caracteres. O caso é ignorado nos formulários **inf** e **Nan** . O primeiro caractere que não se ajusta a um desses formulários interrompe a verificação.

As versões UCRT dessas funções não dão suporte à conversão de letras de expoente de estilo Fortran (**d** ou **d**). Essa extensão não padrão tinha suporte em versões anteriores do CRT e pode ser uma alteração significativa para seu código. As versões do UCRT dão suporte a cadeias de caracteres hexadecimais e a ida e volta de valores INF e NAN, que não têm suporte em versões anteriores. Isso também pode causar alterações significativas em seu código. Por exemplo, a cadeia de caracteres "0x1A" seria interpretada por **strtod** como 0,0 em versões anteriores, mas como 26,0 na versão UCRT.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**strtod**, **_strtod_l**|C: &lt;stdlib.h> C++: &lt;cstdlib> ou &lt;stdlib.h> |
|**wcstod**, **_wcstod_l**|C: &lt;stdlib.h> ou &lt;wchar.h> C++: &lt;cstdlib>, &lt;stdlib.h> ou &lt;wchar.h> |

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_strtod.c
// This program uses strtod to convert a
// string to a double-precision value; strtol to
// convert a string to long integer values; and strtoul
// to convert a string to unsigned long-integer values.
//

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char   *string, *stopstring;
   double x;
   long   l;
   int    base;
   unsigned long ul;

   string = "3.1415926This stopped it";
   x = strtod( string, &stopstring );
   printf( "string = %s\n", string );
   printf("   strtod = %f\n", x );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "-10110134932This stopped it";
   l = strtol( string, &stopstring, 10 );
   printf( "string = %s\n", string );
   printf("   strtol = %ld\n", l );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "10110134932";
   printf( "string = %s\n", string );

   // Convert string using base 2, 4, and 8:
   for( base = 2; base <= 8; base *= 2 )
   {
      // Convert the string:
      ul = strtoul( string, &stopstring, base );
      printf( "   strtol = %ld (base %d)\n", ul, base );
      printf( "   Stopped scan at: %s\n", stopstring );
   }
}
```

```Output
string = 3.1415926This stopped it
   strtod = 3.141593
   Stopped scan at: This stopped it

string = -10110134932This stopped it
   strtol = -2147483648
   Stopped scan at: This stopped it

string = 10110134932
   strtol = 45 (base 2)
   Stopped scan at: 34932
   strtol = 4423 (base 4)
   Stopped scan at: 4932
   strtol = 2134108 (base 8)
   Stopped scan at: 932
```

## <a name="see-also"></a>Consulte também

[Conversão de Dados](../../c-runtime-library/data-conversion.md)<br/>
[Suporte a ponto flutuante](../../c-runtime-library/floating-point-support.md)<br/>
[Interpretação de sequências de caracteres multibyte](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Localidade](../../c-runtime-library/locale.md)<br/>
[Funções de valor de cadeia de caracteres para numérico](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
