---
title: _vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l
ms.date: 11/04/2016
apiname:
- _vscprintf
- _vscprintf_l
- _vscwprintf_l
- _vscwprintf
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
- vscprintf_l
- vscwpeintf
- _vscwprintf
- _vsctprintf
- _vscprintf
- vscwprintf_l
- vscprintf
- _vscwprintf_l
helpviewer_keywords:
- vsctprintf function
- _vscprintf_l function
- _vsctprintf_l function
- _vsctprintf function
- _vscwprintf_l function
- vscwprintf_l function
- _vscprintf function
- _vscwprintf function
- vscwprintf function
- vsctprintf_l function
- formatted text [C++]
- vscprintf function
- vscprintf_l function
ms.assetid: 1bc67d3d-21d5-49c9-ac8d-69e26b16a3c3
ms.openlocfilehash: 18b177114fe0e2984fee518b06a72bea72905ed1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581526"
---
# <a name="vscprintf-vscprintfl-vscwprintf-vscwprintfl"></a>_vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l

Retorna o número de caracteres na cadeia de caracteres formatada usando um ponteiro para uma lista de argumentos.

## <a name="syntax"></a>Sintaxe

```C
int _vscprintf(
   const char *format,
   va_list argptr
);
int _vscprintf_l(
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vscwprintf(
   const wchar_t *format,
   va_list argptr
);
int _vscwprintf_l(
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Parâmetros

*format*<br/>
Cadeia de caracteres de controle de formato.

*argptr*<br/>
Ponteiro para a lista de argumentos.

*locale*<br/>
A localidade a ser usada.

Para obter mais informações, consulte [Especificações de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valor de retorno

**vsnprintf** retorna o número de caracteres que será gerado se a cadeia de caracteres apontada pela lista de argumentos tiver sido impressa ou enviado para um arquivo ou códigos de buffer usando a formatação especificado. O valor retornado não inclui o caractere nulo de terminação. **vscwprintf** executa a mesma função para caracteres largos.

As versões dessas funções com o **l** sufixo são idênticas, exceto que eles usam o parâmetro de localidade passado em vez da localidade do thread atual.

Se *formato* for um ponteiro nulo, o manipulador de parâmetro inválido será invocado, conforme descrito em [validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, as funções retornarão -1 e defina **errno** à **EINVAL**.

## <a name="remarks"></a>Comentários

Cada *argumento* (se houver) é convertido de acordo com a especificação de formato correspondente em *formato*. O formato consiste em caracteres comuns e tem o mesmo formato e função que o *formato* argumento para [printf](printf-printf-l-wprintf-wprintf-l.md).

> [!IMPORTANT]
> Certifique-se de que, se *formato* é uma cadeia de caracteres definida pelo usuário, ele é finalizada com null e tem o número correto e o tipo de parâmetros. Para obter mais informações, consulte [Avoiding Buffer Overruns](/windows/desktop/SecBP/avoiding-buffer-overruns) (Evitando estouros de buffer).

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina TCHAR.H|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**vsctprintf**|**_vscprintf**|**_vscprintf**|**_vscwprintf**|
|**vsctprintf_l**|**_vscprintf_l**|**_vscprintf_l**|**_vscwprintf_l**|

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**vsnprintf**, **vscprintf_l**|\<stdio.h>|
|**vscwprintf**, **vscwprintf_l**|\<stdio.h> ou \<wchar.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

Consulte o exemplo para [vsprintf](vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md).

## <a name="see-also"></a>Consulte também

[E/S de fluxo](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[Funções vprintf](../../c-runtime-library/vprintf-functions.md)<br/>
