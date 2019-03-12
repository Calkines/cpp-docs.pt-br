---
title: _daylight, _dstbias, _timezone e _tzname
ms.date: 11/04/2016
f1_keywords:
- tzname
- _timezone
- timezone
- _daylight
- _tzname
- daylight
helpviewer_keywords:
- time zones
- time adjustments
- timezone variables
- _tzname function
- _daylight function
- _timezone function
- daylight function
- local time adjustments
- timezone function
- tzname function
- time-zone variables
ms.assetid: d06c7292-6b99-4aba-b284-16a96570c856
ms.openlocfilehash: 3f9f78d0798140399960cade7ead408f958450ba
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748249"
---
# <a name="daylight-dstbias-timezone-and-tzname"></a>_daylight, _dstbias, _timezone e _tzname

`_daylight`, `_dstbias`, `_timezone` e `_tzname` são usados em algumas rotinas de data e hora para fazer ajustes de hora local. Essas variáveis globais foram preteridas em relação às versões funcionais mais seguras, que devem ser usadas no lugar das variáveis globais.

|Variável global|Equivalente funcional|
|---------------------|---------------------------|
|`_daylight`|[_get_daylight](../c-runtime-library/reference/get-daylight.md)|
|`_dstbias`|[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)|
|`_timezone`|[_get_timezone](../c-runtime-library/reference/get-timezone.md)|
|`_tzname`|[_get_tzname](../c-runtime-library/reference/get-tzname.md)|

Eles são declarados em Time.h, conforme mostrado a seguir.

## <a name="syntax"></a>Sintaxe

```
extern int _daylight;
extern int _dstbias;
extern long _timezone;
extern char *_tzname[2];
```

## <a name="remarks"></a>Comentários

Em uma chamada a `_ftime`, `localtime` ou `_tzset`, os valores de `_daylight`, `_dstbias`, `_timezone` e `_tzname` são determinados com base no valor da variável de ambiente `TZ`. Se você não definir explicitamente o valor de `TZ`, `_tzname[0]` e `_tzname[1]` conterão as configurações padrão de “PST” e “PDT”, respectivamente.  As funções de manipulação de hora ([_tzset](../c-runtime-library/reference/tzset.md), [_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md) e [localtime](../c-runtime-library/reference/localtime-localtime32-localtime64.md)) tentam definir os valores de `_daylight`, `_dstbias` e `_timezone` consultando o sistema operacional para obter o valor padrão de cada variável. Os valores das variáveis globais de fuso horário são mostrados na tabela a seguir.

|Variável|Valor|
|--------------|-----------|
|`_daylight`|Diferente de zero se o DST (fuso horário de verão) for especificado em `TZ` ou determinado por meio do sistema operacional; caso contrário, 0. O valor padrão é 1.|
|`_dstbias`|Deslocamento de horário de verão.|
|`_timezone`|Diferença em segundos entre o tempo universal coordenado e a hora local. O valor padrão é 28.800.|
|`_tzname[0]`|Nome do fuso horário derivado da variável de ambiente `TZ`. O valor padrão é “PST”.|
|`_tzname[1]`|Nome do DST (fuso horário de verão) derivado da variável de ambiente `TZ`. O valor padrão é “PDT” (horário de verão do Pacífico).|

## <a name="see-also"></a>Consulte também

[Variáveis globais](../c-runtime-library/global-variables.md)<br/>
[_get_daylight](../c-runtime-library/reference/get-daylight.md)<br/>
[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)<br/>
[_get_timezone](../c-runtime-library/reference/get-timezone.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)
