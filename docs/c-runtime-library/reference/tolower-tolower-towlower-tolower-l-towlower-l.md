---
title: tolower, _tolower, towlower, _tolower_l, _towlower_l
ms.date: 11/04/2016
api_name:
- _tolower_l
- towlower
- tolower
- _tolower
- _towlower_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _totlower
- tolower
- _tolower
- towlower
helpviewer_keywords:
- tolower_l function
- _tolower_l function
- totlower function
- string conversion, to different characters
- lowercase, converting to
- tolower function
- string conversion, case
- towlower function
- _tolower function
- _totlower function
- towlower_l function
- case, converting
- characters, converting
- _towlower_l function
ms.assetid: 86e0fc02-94ae-4472-9631-bf8e96f67b92
ms.openlocfilehash: 5d182fca50befac3393012572e68e65a8c81fa72
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957448"
---
# <a name="tolower-_tolower-towlower-_tolower_l-_towlower_l"></a>tolower, _tolower, towlower, _tolower_l, _towlower_l

Converte um caractere em minúsculo.

## <a name="syntax"></a>Sintaxe

```C
int tolower(
   int c
);
int _tolower(
   int c
);
int towlower(
   wint_t c
);
int _tolower_l(
   int c,
   _locale_t locale
);
int _towlower_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parâmetros

*c*<br/>
Caractere a ser convertido.

*locale*<br/>
Localidade a ser usada para conversão específica de localidade.

## <a name="return-value"></a>Valor de retorno

Cada uma dessas rotinas converte uma cópia de *c* em minúsculas se a conversão é possível e retorna o resultado. Não há valor retornado reservado para indicar um erro.

## <a name="remarks"></a>Comentários

Cada uma dessas rotinas converte determinada letra maiúscula em minúscula, se for possível e relevante. A conversão de casos de **towlower** é específica da localidade. Somente caracteres relevantes à localidade atual são alterados quanto a maiúsculas e minúsculas. As funções sem o sufixo **_L** usam a localidade definida atualmente. As versões dessas funções que têm o sufixo **_L** pegam a localidade como um parâmetro e usam isso em vez da localidade definida no momento. Para obter mais informações, consulte [Localidade](../../c-runtime-library/locale.md).

Para que o **_tolower** forneça os resultados esperados, [__isascii](isascii-isascii-iswascii.md) e [IsUpper](isupper-isupper-l-iswupper-iswupper-l.md) devem retornar diferentes de zero.

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina TCHAR.H|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_totlower**|**tolower**|**_mbctolower**|**towlower**|
|**_totlower_l**|**_tolower_l**|**_mbctolower_l**|**_towlower_l**|

> [!NOTE]
> **_tolower_l** e **_towlower_l** não têm nenhuma dependência de localidade e não devem ser chamados diretamente. Eles são fornecidos para uso interno pelo **_totlower_l**.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**tolower**|\<ctype.h>|
|**_tolower**|\<ctype.h>|
|**towlower**|\<ctype.h> ou \<wchar.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

Consulte o exemplo em [Funções to](../../c-runtime-library/to-functions.md).

## <a name="see-also"></a>Consulte também

[Conversão de Dados](../../c-runtime-library/data-conversion.md)<br/>
[Rotinas is, isw](../../c-runtime-library/is-isw-routines.md)<br/>
[Funções to](../../c-runtime-library/to-functions.md)<br/>
[Localidade](../../c-runtime-library/locale.md)<br/>
[Interpretação de sequências de caracteres multibyte](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
