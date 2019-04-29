---
title: _strtime, _wstrtime
ms.date: 11/04/2016
apiname:
- _wstrtime
- _strtime
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
- api-ms-win-crt-time-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wstrtime
- _strtime
- wstrtime
- strtime
- _tstrtime
helpviewer_keywords:
- strtime function
- _strtime function
- _wstrtime function
- copying time to buffers
- wstrtime function
- tstrtime function
- _tstrtime function
- time, copying
ms.assetid: 9e538161-cf49-44ec-bca5-c0ab0b9e4ca3
ms.openlocfilehash: 9d874321418854a703886eb80ee23ac1cba57fa4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223076"
---
# <a name="strtime-wstrtime"></a>_strtime, _wstrtime

Copia o tempo para um buffer. Estão disponíveis versões mais seguras dessas funções; consulte [_strtime_s, _wstrtime_s](strtime-s-wstrtime-s.md).

## <a name="syntax"></a>Sintaxe

```C
char *_strtime(
   char *timestr
);
wchar_t *_wstrtime(
   wchar_t *timestr
);
template <size_t size>
char *_strtime(
   char (&timestr)[size]
); // C++ only
template <size_t size>
wchar_t *_wstrtime(
   wchar_t (&timestr)[size]
); // C++ only
```

### <a name="parameters"></a>Parâmetros

*timestr*<br/>
Cadeia de caracteres de hora.

## <a name="return-value"></a>Valor de retorno

Retorna um ponteiro para a cadeia de caracteres resultante *timestr*.

## <a name="remarks"></a>Comentários

O **strtime** função copia a hora local atual para o buffer apontado por *timestr*. A hora é formatada como **hh** onde **hh** são dois dígitos que representa a hora na notação de 24 horas **mm** são dois dígitos que representa os minutos após a hora e os **ss** são dois dígitos que representam os segundos. Por exemplo, a cadeia de caracteres **18:23:44** representa 23 minutos e 44 segundos após 6 horas. O tamanho do buffer deve ser de, ao menos, 9 bytes.

**wstrtime** é uma versão de caractere largo de **strtime**; o argumento e o valor retornado de **wstrtime** são cadeias de caracteres largos. Caso contrário, essas funções se comportam de forma idêntica. Se *timestr* é um **nulo** ponteiro ou se *timestr* está formatado incorretamente, o inválido manipulador de parâmetro é invocado, conforme descrito em [parâmetro Validação](../../c-runtime-library/parameter-validation.md). Se a exceção tiver permissão para continuar, essas funções retornarão uma **nulo** e defina **errno** para **EINVAL** se *timestr* foi um **Nulo** ou definir **errno** para **ERANGE** se *timestr* está formatado incorretamente.

No C++, essas funções têm sobrecargas de modelo que invocam os equivalentes mais novos e seguros dessas funções. Para obter mais informações, consulte [Sobrecargas de modelo seguro](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina TCHAR.H|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime**|**_strtime**|**_strtime**|**_wstrtime**|

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**_strtime**|\<time.h>|
|**_wstrtime**|\<time.h> ou \<wchar.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_strtime.c
// compile with: /W3

#include <time.h>
#include <stdio.h>

int main( void )
{
   char tbuffer [9];
   _strtime( tbuffer ); // C4996
   // Note: _strtime is deprecated; consider using _strtime_s instead
   printf( "The current time is %s \n", tbuffer );
}
```

```Output
The current time is 14:21:44
```

## <a name="see-also"></a>Consulte também

[Gerenciamento de Tempo](../../c-runtime-library/time-management.md)<br/>
[asctime, _wasctime](asctime-wasctime.md)<br/>
[ctime, _ctime32, _ctime64, _wctime, _wctime32, _wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime, _gmtime32, _gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime, _localtime32, _localtime64](localtime-localtime32-localtime64.md)<br/>
[mktime, _mktime32, _mktime64](mktime-mktime32-mktime64.md)<br/>
[time, _time32, _time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
