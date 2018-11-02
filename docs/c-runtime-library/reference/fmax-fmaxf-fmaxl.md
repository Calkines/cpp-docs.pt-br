---
title: fmax, fmaxf, fmaxl
ms.date: 04/05/2018
apiname:
- fmax
- fmaxf
- fmaxl
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
- fmax
- fmaxf
- fmaxl
- math/fmax
- math/fmaxf
- math/fmaxl
helpviewer_keywords:
- fmax function
- fmaxf function
- fmaxl function
ms.assetid: a773ccf7-495e-4a9a-8c6d-dfb53e341e35
ms.openlocfilehash: 0fbe23a4b7d6e0c59523d62f844dd89e66642933
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465150"
---
# <a name="fmax-fmaxf-fmaxl"></a>fmax, fmaxf, fmaxl

Determine o maior entre dois valores numéricos especificados.

## <a name="syntax"></a>Sintaxe

```C
double fmax(
   double x,
   double y
);

float fmax(
   float x,
   float y
); //C++ only

long double fmax(
   long double x,
   long double y
); //C++ only

float fmaxf(
   float x,
   float y
);

long double fmaxl(
   long double x,
   long double y
);

```

### <a name="parameters"></a>Parâmetros

*x*<br/>
O primeiro valor a ser comparado.

*y*<br/>
O segundo valor a ser comparado.

## <a name="return-value"></a>Valor de retorno

Se for bem-sucedido, retorna o maior dos *x* ou *y*. O valor retornado é exato e não depende de nenhuma forma de arredondamento.

Caso contrário, pode retornar um dos seguintes valores:

|Problema|Valor de|
|-----------|------------|
|*x* = NaN|*y*|
|*y* = NaN|*x*|
|*x* e *y* = NaN|NaN|

Essa função não usa os erros especificados em [_matherr](matherr.md).

## <a name="remarks"></a>Comentários

Uma vez que C++ permite sobrecargas, é possível chamar sobrecargas de fmax que utilizam e retornam tipos double flutuantes e longos. Em um programa C, fmax sempre usa e retorna um double.

## <a name="requirements"></a>Requisitos

|Função|Cabeçalho C|Cabeçalho C++|
|--------------|--------------|------------------|
|**fmax**, **fmaxf**, **fmaxl**|\<math.h>|\<cmath> ou \<math.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte também

[Referência da Função Alfabética](crt-alphabetical-function-reference.md)<br/>
[fmin, fminf, fminl](fmin-fminf-fminl.md)<br/>
