---
title: mbrlen
ms.date: 11/04/2016
api_name:
- mbrlen
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbrlen
helpviewer_keywords:
- mbrlen function
ms.assetid: dde8dee9-e091-4c4c-81b3-639808885ae1
ms.openlocfilehash: c9559731f39db35e03f640bb30b9af3fff00cf66
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952500"
---
# <a name="mbrlen"></a>mbrlen

Determine o número de bytes necessários para completar um caractere multibyte na localidade atual, com a capacidade de reiniciar no meio de um caractere multibyte.

## <a name="syntax"></a>Sintaxe

```C
size_t mbrlen(
   const char * str,
   size_t count,
   mbstate_t * mbstate
);
```

### <a name="parameters"></a>Parâmetros

*str*<br/>
O ponteiro para o próximo byte a ser inspecionado em uma cadeia de caracteres multibyte.

*count*<br/>
O número máximo de bytes a serem inspecionados.

*mbstate*<br/>
Aponta para o estado atual de deslocamento do byte inicial de *Str*.

## <a name="return-value"></a>Valor de retorno

Um dos seguintes valores:

|||
|-|-|
0|A próxima *contagem* ou menos bytes concluirá o caractere multibyte que representa o caractere nulo largo.
1 para *contagem*, inclusivo|A próxima *contagem* ou menos bytes concluirá um caractere multibyte válido. O valor retornado é o número de bytes que completa os caracteres multibyte.
(size_t)(-2)|Os bytes de *contagem* seguinte contribuem para um caractere multibyte incompleto, mas potencialmente válido, e todos os bytes de *contagem* foram processados.
(size_t)(-1)|Erro de codificação. A próxima *contagem* ou menos bytes não contribuirá para um caractere multibyte completo e válido. Nesse caso, **errno** é definido como EILSEQ e o estado de conversão em *mbstate* não é especificado.

## <a name="remarks"></a>Comentários

A função **mbrlen** inspeciona no máximo bytes de *contagem* começando com o byte apontado por *Str* para determinar o número de bytes necessários para concluir o próximo caractere multibyte, incluindo quaisquer sequências de deslocamento. É equivalente à chamada `mbrtowc(NULL, str, count, &mbstate)` , em que *mbstate* é um objeto **mbstate_t** fornecido pelo usuário ou um objeto interno estático fornecido pela biblioteca.

A função **mbrlen** salva e usa o estado de deslocamento de um caractere multibyte incompleto no parâmetro *mbstate* . Isso dá ao **mbrlen** a capacidade de reiniciar no meio de um caractere multibyte, se necessário, examinando no máximo os bytes de *contagem* . Se *mbstate* for um ponteiro nulo, **mbrlen** usará um objeto **mbstate_t** estático interno para armazenar o estado de deslocamento. Como o objeto **mbstate_t** interno não é thread-safe, é recomendável que você sempre aloque e transmita seu próprio parâmetro *mbstate* .

A função **mbrlen** difere de [_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md) por sua reinicialização. O estado de deslocamento é armazenado em *mbstate* para chamadas subsequentes para as mesmas ou outras funções reiniciáveis. Os resultados são indefinidos ao combinar o uso de funções reiniciáveis e não reiniciáveis.  Por exemplo, um aplicativo deve usar **wcsrlen** em vez de **wcslen** se uma chamada subsequente para **wcsrtombs** for usada em vez de **wcstombs**.

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina TCHAR.H|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|não aplicável|não aplicável|**mbrlen**|não aplicável|

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**mbrlen**|\<wchar.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

Este exemplo mostra como a interpretação de caracteres multibyte depende da página de código atual e demonstra a capacidade de retomada do **mbrlen**.

```C
// crt_mbrlen.c
// Compile by using: cl crt_mbrlen.c
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <locale.h>
#include <wchar.h>

size_t Example(const char * pStr)
{
    size_t      charLen = 0;
    size_t      charCount = 0;
    mbstate_t   mbState = {0};

    while ((charLen = mbrlen(pStr++, 1, &mbState)) != 0 &&
            charLen != (size_t)-1)
    {
        if (charLen != (size_t)-2) // if complete mbcs char,
        {
            charCount++;
        }
    }
    return (charCount);
}

int main( void )
{
    int         cp;
    size_t      charCount = 0;
    const char  *pSample =
        "\x82\xD0\x82\xE7\x82\xAA\x82\xC8: Shift-jis hiragana.";

    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);

    setlocale(LC_ALL, "ja-JP"); // Set Japanese locale
    _setmbcp(932); // and Japanese multibyte code page
    cp = _getmbcp();
    charCount = Example(pSample);
    printf("\nCode page: %d\n%s\nCharacter count: %d\n",
        cp, pSample, charCount);
}
```

```Output

Code page: 0
é╨éτé¬é╚: Shift-jis hiragana.
Character count: 29

Code page: 932
????: Shift-jis hiragana.
Character count: 25
```

## <a name="see-also"></a>Consulte também

[Manipulação de cadeias de caracteres](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Localidade](../../c-runtime-library/locale.md)<br/>
