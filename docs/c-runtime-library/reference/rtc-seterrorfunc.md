---
title: _RTC_SetErrorFunc
ms.date: 11/04/2016
apiname:
- _RTC_SetErrorFunc
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
apitype: DLLExport
f1_keywords:
- RTC_SetErrorFunc
- _RTC_SetErrorFunc
helpviewer_keywords:
- RTC_SetErrorFunc function
- _RTC_SetErrorFunc function
ms.assetid: b2292722-0d83-4092-83df-3d5b19880666
ms.openlocfilehash: 6b292d685eea8eccb9e9b2a3c3e6cd903d501005
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514732"
---
# <a name="rtcseterrorfunc"></a>_RTC_SetErrorFunc

Designa uma função como o manipulador para RTCs (verificações de erro em tempo de execução). Essa função foi preterida; Use **RTC_SetErrorFuncW** em vez disso.

## <a name="syntax"></a>Sintaxe

```C
_RTC_error_fn _RTC_SetErrorFunc(
   _RTC_error_fn function
);
```

### <a name="parameters"></a>Parâmetros

*function*<br/>
O endereço da função que manipulará verificações de erro em tempo de execução.

## <a name="return-value"></a>Valor de retorno

A função de erro definida anteriormente. Se não houver nenhuma função definida anteriormente, retorna **nulo**.

## <a name="remarks"></a>Comentários

Não use essa função; em vez disso, use **RTC_SetErrorFuncW**. Ela é mantida apenas para fins de compatibilidade com versões anteriores.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**_RTC_SetErrorFunc**|\<rtcapi.h>|

Para obter mais informações, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Libraries

Todas as versões das [bibliotecas em tempo de execução C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Consulte também

[_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)<br/>
[Verificação de erros em tempo de execução](../../c-runtime-library/run-time-error-checking.md)<br/>
