---
title: _fpieee_flt
ms.date: 04/05/2018
apiname:
- _fpieee_flt
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fpieee_flt
- _fpieee_flt
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
ms.openlocfilehash: 9a49ec403b1cb95407b0a366accf1d9374d9cb22
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458611"
---
# <a name="fpieeeflt"></a>_fpieee_flt

Invoca um manipulador de interceptação definido pelo usuário para exceções de ponto flutuante do IEEE.

## <a name="syntax"></a>Sintaxe

```C
int _fpieee_flt(
   unsigned long excCode,
   struct _EXCEPTION_POINTERS *excInfo,
   int handler(_FPIEEE_RECORD *)
);
```

### <a name="parameters"></a>Parâmetros

*excCode*<br/>
Código da exceção.

*excInfo*<br/>
Ponteiro para a estrutura de informações de exceção do Windows NT.

*Manipulador*<br/>
Ponteiro para a rotina do manipulador de interceptação do IEEE do usuário.

## <a name="return-value"></a>Valor de retorno

O valor de retorno **fpieee_flt** é o valor retornado por *manipulador*. Sendo assim, a rotina de filtro do IEEE pode ser usada na cláusula except de um mecanismo de SEH (manipulação de exceção estruturada).

## <a name="remarks"></a>Comentários

O **fpieee_flt** função invocará um manipulador de interceptação definido pelo usuário para exceções de ponto flutuante do IEEE e fornece-a com todas as informações relevantes. Essa rotina serve como um filtro de exceção no mecanismo de SEH, que invoca seu próprio manipulador de exceção do IEEE quando necessário.

O **fpieee_record** estrutura, definida em fpieee, contém informações que pertencem a uma exceção de ponto flutuante IEEE. Essa estrutura é passada para o manipulador de interceptação definido pelo usuário por **fpieee_flt**.

|Campo _FPIEEE_RECORD|Descrição|
|----------------------------|-----------------|
|**RoundingMode**<br/>**Precisão**|Eles **sem sinal** **int** campos contêm informações sobre o ambiente de ponto flutuante no momento em que ocorreu a exceção.|
|**operação**|Isso **sem sinal** **int** campo indica o tipo de operação que causou a interceptação. Se o tipo é uma comparação (**_FpCodeCompare**), você pode fornecer um dos especiais **_FPIEEE_COMPARE_RESULT** valores (conforme definido em fpieee) nos **Result.Value** campo. O tipo de conversão (**_FpCodeConvert**) indica que a interceptação ocorreu durante uma operação de conversão de ponto flutuante. Você pode examinar os **necessário operando1** e **resultado** tipos para determinar o tipo de conversão que está sendo tentada.|
|**Necessário operando1**<br/>**Necessário operando2**<br/>**Result**|Eles **_FPIEEE_VALUE** estruturas indicam os tipos e valores do resultado proposto e operandos. Cada estrutura contém estes campos:<br /><br /> **OperandValid** – o sinalizador que indica se o valor de resposta é válido.<br />**Formato** -tipo de dados do valor correspondente. O tipo de formato pode ser retornado, mesmo que o valor correspondente não seja válido.<br />**Valor** -valor de dados de resultado ou do operando.|
|**Causa**<br/>**Habilitar**<br/>**Status**|**Fpieee_exception_flags** contém um campo de bits por tipo de exceção de ponto de flutuante. Há uma correspondência entre esses campos e os argumentos usados para mascarar as exceções fornecidas a [_controlfp](control87-controlfp-control87-2.md). O significado exato de cada bit depende do contexto:<br /><br /> **Causa** -cada bit definido indica que a exceção específica que foi gerada.<br />**Habilitar** -cada bit definido indica que a exceção específica está sendo desmascarada.<br />**Status** -cada bit definido indica que a exceção específica está pendente no momento. Isso inclui exceções que não foram geradas porque estavam mascaradas por **controlfp**.|

Exceções pendentes desabilitadas são geradas quando você as habilita. Isso pode resultar em comportamento indefinido ao usar **fpieee_flt** como um filtro de exceção. Sempre chame [_clearfp](clear87-clearfp.md) antes de habilitar exceções de ponto flutuante.

## <a name="requirements"></a>Requisitos

|Função|Cabeçalho necessário|
|--------------|---------------------|
|**_fpieee_flt**|\<fpieee.h>|

Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_fpieee.c
// This program demonstrates the implementation of
// a user-defined floating-point exception handler using the
// _fpieee_flt function.

#include <fpieee.h>
#include <excpt.h>
#include <float.h>
#include <stddef.h>

int fpieee_handler( _FPIEEE_RECORD * );

int fpieee_handler( _FPIEEE_RECORD *pieee )
{
   // user-defined ieee trap handler routine:
   // there is one handler for all
   // IEEE exceptions

   // Assume the user wants all invalid
   // operations to return 0.

   if ((pieee->Cause.InvalidOperation) &&
       (pieee->Result.Format == _FpFormatFp32))
   {
        pieee->Result.Value.Fp32Value = 0.0F;

        return EXCEPTION_CONTINUE_EXECUTION;
   }
   else
      return EXCEPTION_EXECUTE_HANDLER;
}

#define _EXC_MASK    \
    _EM_UNDERFLOW  + \
    _EM_OVERFLOW   + \
    _EM_ZERODIVIDE + \
    _EM_INEXACT

int main( void )
{
   // ...

   __try {
      // unmask invalid operation exception
      _controlfp_s(NULL, _EXC_MASK, _MCW_EM);

      // code that may generate
      // fp exceptions goes here
   }
   __except ( _fpieee_flt( GetExceptionCode(),
                GetExceptionInformation(),
                fpieee_handler ) ){

      // code that gets control

      // if fpieee_handler returns
      // EXCEPTION_EXECUTE_HANDLER goes here

   }

   // ...
}
```

## <a name="see-also"></a>Consulte também

[Suporte a ponto flutuante](../../c-runtime-library/floating-point-support.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
