---
title: isleadbyte, _isleadbyte_l
ms.date: 11/04/2016
api_name:
- _isleadbyte_l
- isleadbyte
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
- _istleadbyte
- _isleadbyte_l
- isleadbyte
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
ms.openlocfilehash: 6b853dcea82c2afea91b2e0545d253786c88ae5e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954307"
---
# <a name="isleadbyte-_isleadbyte_l"></a>isleadbyte, _isleadbyte_l

Determina se um caractere é o byte inicial de um caractere multibyte.

> [!IMPORTANT]
> Esta API não pode ser usada em aplicativos executados no Tempo de Execução do Windows. Para obter mais informações, confira [Funções do CRT sem suporte em aplicativos da Plataforma Universal do Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxe

```C
int isleadbyte( int c );
int _isleadbyte_l( int c );
```

### <a name="parameters"></a>Parâmetros

*c*<br/>
Inteiro a ser testado.

## <a name="return-value"></a>Valor de retorno

**isleadbyte** retornará um valor diferente de zero se o argumento satisfizer a condição de teste ou 0 se não tiver. Na localidade "C" e em localidades SBCS (conjunto de caracteres de byte único), **isleadbyte** sempre retorna 0.

## <a name="remarks"></a>Comentários

A macro **isleadbyte** retornará um valor diferente de zero se o argumento for o primeiro byte de um caractere multibyte. **isleadbyte** produz um resultado significativo para qualquer argumento inteiro de-1 (**EOF**) a **UCHAR_MAX** (0xFF), inclusive.

O tipo de argumento esperado de **isleadbyte** é **int**; se um caractere assinado for passado, o compilador poderá convertê-lo em um inteiro por extensão de assinatura, gerando resultados imprevisíveis.

A versão dessa função com o sufixo **_L** é idêntica, exceto pelo fato de que ele usa a localidade passada em vez da localidade atual para seu comportamento dependente de localidade.

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina TCHAR.H|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istleadbyte**|Sempre retorna falso|**_isleadbyte**|Sempre retorna falso|

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**isleadbyte**|\<ctype.h>|
|**_isleadbyte_l**|\<ctype.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte também

[Classificação de byte](../../c-runtime-library/byte-classification.md)<br/>
[Localidade](../../c-runtime-library/locale.md)<br/>
[Rotinas _ismbb](../../c-runtime-library/ismbb-routines.md)<br/>
