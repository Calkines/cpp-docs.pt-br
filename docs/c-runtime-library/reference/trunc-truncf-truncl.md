---
title: trunc, truncf, truncl
ms.date: 04/05/2018
api_name:
- trunc
- truncf
- truncl
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- trunc
- truncf
- truncl
- math/trunc
- math/truncf
- math/truncl
helpviewer_keywords:
- trunc function
- truncf function
- truncl function
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
ms.openlocfilehash: b0c615c91e562fa45f791d8cc20f39a830013aeb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946003"
---
# <a name="trunc-truncf-truncl"></a>trunc, truncf, truncl

Determina o inteiro mais próximo que é menor ou igual ao valor de ponto flutuante especificado.

## <a name="syntax"></a>Sintaxe

```C
double trunc( double x );
float trunc( float x ); //C++ only
long double truncl( long double x );
```

```cpp
long double trunc( long double x ); //C++ only
float trunc( float x ); //C++ only
```

### <a name="parameters"></a>Parâmetros

*x*<br/>
O valor a ser truncado.

## <a name="return-value"></a>Valor de retorno

Se for bem-sucedido, retorna um valor inteiro de *x*, arredondado para zero.

Caso contrário, pode retornar um dos seguintes:

|Problema|Valor de|
|-----------|------------|
|*x* = ±INFINITY|x|
|*x* =  ±0|x|
|*x* = Nan|NaN|

Os erros são relatados conforme especificado em [_matherr](matherr.md).

## <a name="remarks"></a>Comentários

Como C++ o permite sobrecarga, você pode chamar sobrecargas de **truncar** que usam e retornam tipos **float** e **Long** **duplos** . Em um programa C, **trunc** sempre pega e retorna um **Double**.

Como os maiores valores de ponto flutuantes são inteiros exatos, essa função não estourará por conta própria. No entanto, você pode causar o estouro, retornando um valor para um tipo inteiro.

Você também pode arredondar para baixo pela conversão implícita de ponto flutuante para integral; no entanto, isso é limitado aos valores que podem ser armazenados no tipo de destino.

## <a name="requirements"></a>Requisitos

|Função|Cabeçalho C|Cabeçalho C++|
|--------------|--------------|------------------|
|**trunc**, **truncf**, **truncl**|\<math.h>|\<cmath>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte também

[Referência da Função Alfabética](crt-alphabetical-function-reference.md)<br/>
[floor, floorf, floorl](floor-floorf-floorl.md)<br/>
[ceil, ceilf, ceill](ceil-ceilf-ceill.md)<br/>
[round, roundf, roundl](round-roundf-roundl.md)<br/>
