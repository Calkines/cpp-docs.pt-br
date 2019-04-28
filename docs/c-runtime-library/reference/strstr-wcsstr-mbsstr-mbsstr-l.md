---
title: strstr, wcsstr, _mbsstr, _mbsstr_l
ms.date: 11/04/2016
apiname:
- _mbsstr
- wcsstr
- _mbsstr_l
- strstr
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- _fstrstr
- _ftcsstr
- strstr
- wcsstr
- _mbsstr
- _tcsstr
helpviewer_keywords:
- strings [C++], searching
- mbsstr function
- _ftcsstr function
- ftcsstr function
- fstrstr function
- _tcsstr function
- substrings, finding
- mbsstr_l function
- tcsstr function
- _mbsstr function
- wcsstr function
- _fstrstr function
- _mbsstr_l function
- strstr function
ms.assetid: 03d70c3f-2473-45cb-a5f8-b35beeb2748a
ms.openlocfilehash: 42e02473e062c3af9524ed432aa163b7574342de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223073"
---
# <a name="strstr-wcsstr-mbsstr-mbsstrl"></a>strstr, wcsstr, _mbsstr, _mbsstr_l

Retorna um ponteiro para a primeira ocorrência de uma cadeia de caracteres de pesquisa em uma cadeia de caracteres.

> [!IMPORTANT]
> `_mbsstr` e `_mbsstr_l` não podem ser usados em aplicativos executados no Windows Runtime. Para obter mais informações, confira [Funções do CRT sem suporte em aplicativos da Plataforma Universal do Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxe

```C
char *strstr(
   const char *str,
   const char *strSearch
); // C only
char *strstr(
   char *str,
   const char *strSearch
); // C++ only
const char *strstr(
   const char *str,
   const char *strSearch
); // C++ only
wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C only
wchar_t *wcsstr(
   wchar_t *str,
   const wchar_t *strSearch
); // C++ only
const wchar_t *wcsstr(
   const wchar_t *str,
   const wchar_t *strSearch
); // C++ only
unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C only
unsigned char *_mbsstr(
   unsigned char *str,
   const unsigned char *strSearch
); // C++ only
const unsigned char *_mbsstr(
   const unsigned char *str,
   const unsigned char *strSearch
); // C++ only
unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C only
unsigned char *_mbsstr_l(
   unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
const unsigned char *_mbsstr_l(
   const unsigned char *str,
   const unsigned char *strSearch,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parâmetros

*str*<br/>
Cadeia de caracteres terminada em nulo para pesquisa.

*strSearch*<br/>
Cadeia de caracteres terminada em nulo para pesquisar.

*locale*<br/>
Localidade a usar.

## <a name="return-value"></a>Valor de retorno

Retorna um ponteiro para a primeira ocorrência de *strSearch* na *str*, ou nulo se *strSearch* não aparecer na *str*. Se *strSearch* aponta para uma cadeia de caracteres de comprimento zero, a função retorna *str*.

## <a name="remarks"></a>Comentários

O `strstr` função retorna um ponteiro para a primeira ocorrência do *strSearch* na *str*. A pesquisa não inclui os caracteres nulo de terminação. `wcsstr` é a versão de caractere largo de `strstr` e `_mbsstr` é a versão de caracteres multibyte. Os argumentos e o valor retornado de `wcsstr` são cadeias de caracteres largos; aqueles de `_mbsstr` são cadeias de caracteres multibyte. `_mbsstr` valida seus parâmetros. Se *str* ou *strSearch* for NULL, o manipulador de parâmetro inválido será invocado, conforme descrito na [validação de parâmetro](../../c-runtime-library/parameter-validation.md) . Se a execução puder continuar, `_mbsstr` define `errno` EINVAL e retornará 0. `strstr` e `wcsstr` não validam seus parâmetros. Caso contrário, essas três funções se comportam de forma idêntica.

> [!IMPORTANT]
> Essas funções podem incorrer uma ameaça de um problema de estouro de buffer. Problemas de estouro de buffer podem ser usados para atacar um sistema pois eles podem permitir a execução de código arbitrário, que pode causar uma injustificada elevação de privilégio. Para obter mais informações, consulte [Avoiding Buffer Overruns](/windows/desktop/SecBP/avoiding-buffer-overruns) (Evitando estouros de buffer).

Em C, essas funções usam um **const** ponteiro para o primeiro argumento. No C++, duas sobrecargas estão disponíveis. A sobrecarga que usa um ponteiro para **const** retorna um ponteiro para **const**; a versão que usa um ponteiro para não**const** retorna um ponteiro para não - **Const**. _CRT_CONST_CORRECT_OVERLOADS a macro é definida se ambos os **const** e não-**const** versões dessas funções estão disponíveis. Se você precisar de não**const** comportamento para ambos C++ sobrecargas, defina o símbolo const_return.

O valor de saída é afetado pela configuração de categoria da localidade do LC_CTYPE; Para obter mais informações, consulte [setlocale, wsetlocale](setlocale-wsetlocale.md). As versões dessas funções que não têm o **l** sufixo usam a localidade atual desse comportamento dependente da localidade; as versões que têm o **l** sufixo são idênticas, exceto pelo fato de que usam o parâmetro de localidade informado. Para obter mais informações, consulte [Localidade](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina TCHAR.H|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcsstr`|`strstr`|`_mbsstr`|`wcsstr`|
|**n/d**|**n/d**|`_mbsstr_l`|**n/d**|

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|`strstr`|\<string.h>|
|`wcsstr`|\<string.h> ou \<wchar.h>|
|`_mbsstr`, `_mbsstr_l`|\<mbstring.h>|

Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_strstr.c

#include <string.h>
#include <stdio.h>

char str[] =    "lazy";
char string[] = "The quick brown dog jumps over the lazy fox";
char fmt1[] =   "         1         2         3         4         5";
char fmt2[] =   "12345678901234567890123456789012345678901234567890";

int main( void )
{
   char *pdest;
   int  result;
   printf( "String to be searched:\n   %s\n", string );
   printf( "   %s\n   %s\n\n", fmt1, fmt2 );
   pdest = strstr( string, str );
   result = (int)(pdest - string + 1);
   if ( pdest != NULL )
      printf( "%s found at position %d\n", str, result );
   else
      printf( "%s not found\n", str );
}
```

```Output
String to be searched:
   The quick brown dog jumps over the lazy fox
            1         2         3         4         5
   12345678901234567890123456789012345678901234567890

lazy found at position 36
```

## <a name="see-also"></a>Consulte também

[Manipulação de cadeias de caracteres](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Localidade](../../c-runtime-library/locale.md)<br/>
[Interpretação de sequências de caracteres multibyte](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l](strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
[basic_string::find](../../standard-library/basic-string-class.md#find)<br/>
