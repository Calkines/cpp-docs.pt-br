---
title: nearbyint, nearbyintf, nearbyintl
ms.date: 04/05/2018
apiname:
- nearbyint
- nearbyintf
- nerabyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
ms.openlocfilehash: 4a36bddb28db9fb4c5809432dfaef9ca3ece4328
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668306"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint, nearbyintf, nearbyintl

Arredonda o valor especificado de ponto flutuante para um inteiro e retorna esse valor em um formato de ponto flutuante.

## <a name="syntax"></a>Sintaxe

```C
double nearbyint( double x );
float nearbyintf( float x );
long double nearbyintl( long double x );
```

```cpp
float nearbyint( float x ); //C++ only
long double nearbyint( long double x ); //C++ only
```

### <a name="parameters"></a>Parâmetros

*x*<br/>
O valor a ser arredondado.

## <a name="return-value"></a>Valor de retorno

Se for bem-sucedido, retornará *x*, arredondado para o inteiro mais próximo, usando o formato de arredondamento atual conforme relatado pelo [fegetround](fegetround-fesetround2.md). Caso contrário, a função pode retornar um dos seguintes valores:

|Problema|Valor de|
|-----------|------------|
|*x* = ±INFINITY|±INFINITY, sem modificações|
|*x* = ±0|±0, sem modificações|
|*x* = NaN|NaN|

Erros não são relatados por meio [matherr](matherr.md); especificamente, essa função não relata qualquer **FE_INEXACT** exceções.

## <a name="remarks"></a>Comentários

A principal diferença entre essa função e [rimir](rint-rintf-rintl.md) é que essa função não gera a exceção de ponto flutuante inexata.

Como os valores máximos de ponto flutuante são inteiros exatos, essa função nunca estourará sozinha. Em vez disso, a saída pode estourar o valor retornado, dependendo da versão da função que você usar.

C++ permite sobrecargas, portanto, é possível chamar sobrecargas de **nearbyint** que usam e retornam **float** ou **longo** **double** parâmetros. Em um programa do C **nearbyint** sempre usa dois valores duplos e retorna um valor duplo.

## <a name="requirements"></a>Requisitos

|Função|Cabeçalho C|Cabeçalho C++|
|--------------|--------------|------------------|
|**nearbyint**, **nearbyintf**, **nearbyintl**|\<math.h>|\<cmath> ou \<math.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte também

[Referência da Função Alfabética](crt-alphabetical-function-reference.md)<br/>
[Matemática e suporte de ponto flutuante](../floating-point-support.md)<br/>
