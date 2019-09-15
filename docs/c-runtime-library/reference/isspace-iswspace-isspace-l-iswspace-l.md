---
title: isspace, iswspace, _isspace_l, _iswspace_l
ms.date: 11/04/2016
api_name:
- iswspace
- _isspace_l
- _iswspace_l
- isspace
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswspace
- _istspace
- isspace
helpviewer_keywords:
- iswspace function
- isspace function
- _iswspace_l function
- _isspace_l function
- iswspace_l function
- isspace_l function
- _istspace function
- istspace function
ms.assetid: b851e0c0-36bb-4dac-a1a3-533540939035
ms.openlocfilehash: b01aaf29ff0cd3994c45433db9ff0b9f4ca7481c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953639"
---
# <a name="isspace-iswspace-_isspace_l-_iswspace_l"></a>isspace, iswspace, _isspace_l, _iswspace_l

Determina se um inteiro representa um caractere de espaço.

## <a name="syntax"></a>Sintaxe

```C
int isspace(
   int c
);
int iswspace(
   wint_t c
);
int _isspace_l(
   int c,
   _locale_t locale
);
int _iswspace_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parâmetros

*c*<br/>
Inteiro a ser testado.

*locale*<br/>
Localidade a usar.

## <a name="return-value"></a>Valor de retorno

Cada uma dessas rotinas retornará zero se *c* for uma representação específica de um caractere de espaço. **isspace** retornará um valor diferente de zero se *c* for um caractere de espaço em branco (0x09-0x0D ou 0x20). O resultado da condição de teste para a função **isspace** depende da configuração de categoria **LC_CTYPE** da localidade; consulte [setlocale, _wsetlocale](setlocale-wsetlocale.md) para obter mais informações. As versões dessas funções que não têm o sufixo **_L** usam a localidade atual para qualquer comportamento dependente de localidade; as versões que têm o sufixo **_L** são idênticas, exceto que usam a localidade que é passada em vez disso. Para obter mais informações, consulte [Localidade](../../c-runtime-library/locale.md).

**iswspace** retornará um valor diferente de zero se *c* for um caractere largo que corresponde a um caractere de espaço em branco padrão.

O comportamento de **isspace** e **_isspace_l** será indefinido se *c* não for EOF ou no intervalo de 0 a 0xFF, inclusive. Quando uma biblioteca CRT de depuração é usada e *c* não é um desses valores, as funções geram uma asserção.

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina TCHAR.H|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_** **istspace**|**isspace**|[_ismbcspace](ismbcgraph-functions.md)|**iswspace**|

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**isspace**|\<ctype.h>|
|**iswspace**|\<ctype.h> ou \<wchar.h>|
|**_isspace_l**|\<ctype.h>|
|**_iswspace_l**|\<ctype.h> ou \<wchar.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte também

[Classificação de caracteres](../../c-runtime-library/character-classification.md)<br/>
[Localidade](../../c-runtime-library/locale.md)<br/>
[Rotinas is, isw](../../c-runtime-library/is-isw-routines.md)<br/>
