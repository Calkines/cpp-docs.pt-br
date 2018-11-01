---
title: exp2, exp2f, exp2l
ms.date: 04/05/2018
apiname:
- exp2
- exp2f
- exp2l
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- exp2
- math/exp2
- exp2f
- math/exp2f
- exp2l
- math/exp2l
helpviewer_keywords:
- exp2 function
- exp2f function
- exp2l function
ms.assetid: 526e3e10-201a-4610-a886-533f44ece344
ms.openlocfilehash: 70a3b7eb610556d4a26de7cf0aad55affcdbdc94
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50562754"
---
# <a name="exp2-exp2f-exp2l"></a>exp2, exp2f, exp2l

Calcula o 2 gerado para o valor especificado.

## <a name="syntax"></a>Sintaxe

```C
double exp2(
   double x
);

float exp2(
   float x
);  // C++ only

long double exp2(
   long double x
); // C++ only

float exp2f(
   float x
);

long double exp2l(
   long double x
);
```

### <a name="parameters"></a>Parâmetros

*x*<br/>
O valor do expoente.

## <a name="return-value"></a>Valor de retorno

Se for bem-sucedido, retorna o expoente de base 2 de *x*, ou seja, 2<sup>x</sup>. Caso contrário, ele retorna um dos seguintes valores:

|Problema|Valor de|
|-----------|------------|
|*x* = ±0|1|
|*x* = - infinito|+0|
|*x* = + infinito|+INFINITY|
|*x* = NaN|NaN|
|Erro de intervalo de estouro|+HUGE_VAL, +HUGE_VALF ou +HUGE_VALL|
|Erro de intervalo de estouro negativo|Resultado correto, após o arredondamento|

Os erros são relatados conforme especificado em [_matherr](matherr.md).

## <a name="remarks"></a>Comentários

Como C++ permite sobrecargas, é possível chamar sobrecargas de **exp2** que usam e retornam **float** e **longo duplo** tipos. Em um programa do C **exp2** sempre usa e retorna um **duplo**.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho C|Cabeçalho C++|
|-------------|--------------|------------------|
|**EXP**, **expf**, **expl**|\<math.h>|\<cmath>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte também

[Referência da Função Alfabética](crt-alphabetical-function-reference.md)<br/>
[exp, expf, expl](exp-expf.md)<br/>
[log2, log2f, log2l](log2-log2f-log2l.md)<br/>
