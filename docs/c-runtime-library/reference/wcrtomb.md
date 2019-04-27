---
title: wcrtomb
ms.date: 11/04/2016
apiname:
- wcrtomb
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
- wcrtomb
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
ms.openlocfilehash: a5fad3f41c7ed459a1af3fae7c6a5a85c867d5ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188647"
---
# <a name="wcrtomb"></a>wcrtomb

Converta um caractere largo em sua representação de caracteres multibyte. Uma versão mais segura dessa função está disponível; consulte [wcrtomb_s](wcrtomb-s.md).

## <a name="syntax"></a>Sintaxe

```C
size_t wcrtomb(
   char *mbchar,
   wchar_t wchar,
   mbstate_t *mbstate
);
template <size_t size>
size_t wcrtomb(
   char (&mbchar)[size],
   wchar_t wchar,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parâmetros

*mbchar*<br/>
O caractere multibyte convertido resultante.

*wchar*<br/>
Um caractere largo a ser convertido.

*mbstate*<br/>
Um ponteiro para um **mbstate_t** objeto.

## <a name="return-value"></a>Valor de retorno

Retorna o número de bytes necessários para representar o caractere multibyte convertido, caso contrário, retorna –1 em caso de erro.

## <a name="remarks"></a>Comentários

O **wcrtomb** função converte um caractere largo, a partir do estado da conversão especificado contido na *mbstate*, do valor contido no *wchar*, para o endereço representado por *mbchar*. O valor de retorno é o número de bytes necessários para representar o caractere multibyte correspondente, mas não retornará mais de **MB_CUR_MAX** bytes.

Se *mbstate* for nulo, a interna **mbstate_t** objeto contendo o estado de conversão de *mbchar* é usado. Se a sequência de caracteres *wchar* multibyte correspondente não tem representação de caractere, -1 será retornado e o **errno** está definido como **EILSEQ**.

O **wcrtomb** função difere [wctomb, wctomb_l](wctomb-wctomb-l.md) por sua capacidade de reinicialização. O estado de conversão é armazenado em *mbstate* para chamadas posteriores às mesmas funções ou outras funções reiniciáveis. Os resultados são indefinidos ao combinar o uso de funções reiniciáveis e não reiniciáveis. Por exemplo, um aplicativo usaria **wcsrlen** vez **wcsnlen**, se uma chamada subsequente para **wcsrtombs** foram usadas em vez de **wcstombs**.

Em C++, essa função tem uma sobrecarga de modelo que invoca os equivalentes mais recentes e seguros dessa função. Para obter mais informações, consulte [Sobrecargas de modelo seguro](../../c-runtime-library/secure-template-overloads.md).

## <a name="exceptions"></a>Exceções

O **wcrtomb** função será multithread-safe contanto que nenhuma função no thread atual chame **setlocale** enquanto essa função está em execução e enquanto o *mbstate* é nulo.

## <a name="example"></a>Exemplo

```C
// crt_wcrtomb.c
// compile with: /W3
// This program converts a wide character
// to its corresponding multibyte character.

#include <string.h>
#include <stdio.h>
#include <wchar.h>

int main( void )
{
    size_t      sizeOfCovertion = 0;
    mbstate_t   mbstate;
    char        mbStr = 0;
    wchar_t*    wcStr = L"Q";

    // Reset to initial conversion state
    memset(&mbstate, 0, sizeof(mbstate));

    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead
    if (sizeOfCovertion > 0)
    {
        printf("The corresponding wide character \"");
        wprintf(L"%s\"", wcStr);
        printf(" was converted to the \"%c\" ", mbStr);
        printf("multibyte character.\n");
    }
    else
    {
        printf("No corresponding multibyte character "
               "was found.\n");
    }
}
```

```Output
The corresponding wide character "Q" was converted to the "Q" multibyte character.
```

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**wcrtomb**|\<wchar.h>|

## <a name="see-also"></a>Consulte também

[Conversão de Dados](../../c-runtime-library/data-conversion.md)<br/>
[Localidade](../../c-runtime-library/locale.md)<br/>
[Interpretação de sequências de caracteres multibyte](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbsinit](mbsinit.md)<br/>
