---
title: rand
ms.date: 01/02/2018
api_name:
- rand
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- rand
helpviewer_keywords:
- generating pseudorandom numbers
- random numbers, generating
- numbers, pseudorandom
- rand function
- pseudorandom numbers
- numbers, generating pseudorandom
ms.openlocfilehash: 6042ab917083cf4131c16012b84afbbe43a7d834
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949547"
---
# <a name="rand"></a>rand

Gera um número pseudoaleatória usando um algoritmo bem conhecido e totalmente reproduzível. Uma versão mais programaticamente segura dessa função está disponível; consulte [rand_s](rand-s.md). Os números gerados por **Rand** não são criptograficamente seguros. Para geração de números aleatórios de segurança mais criptograficamente segura, use [rand_s](rand-s.md) ou as funções C++ declaradas na biblioteca padrão em [ \<> aleatórios](../../standard-library/random.md).

## <a name="syntax"></a>Sintaxe

```C
int rand( void );
```

## <a name="return-value"></a>Valor de retorno

**Rand** retorna um número pseudoaleatória, conforme descrito acima. Nenhum erro é retornado.

## <a name="remarks"></a>Comentários

A função **Rand** retorna um número inteiro pseudoaleatória no intervalo de 0 a **RAND_MAX** (32767). Use a função [srand](srand.md) para propagar o gerador de número de pseudoaleatória antes de chamar **Rand**.

A função **Rand** gera uma sequência bem conhecida e não é apropriada para uso como uma função criptográfica. Para geração de números aleatórios de segurança mais criptograficamente segura, use [rand_s](rand-s.md) ou as funções C++ declaradas na biblioteca padrão em [ \<> aleatórios](../../standard-library/random.md). Para obter informações sobre o que há de errado com \<Rand e como o > aleatório resolve essas deficiências, consulte este vídeo intitulado [Rand considerado prejudicial](https://channel9.msdn.com/Events/GoingNative/2013/rand-Considered-Harmful).

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**rand**|\<stdlib.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_rand.c
// This program seeds the random-number generator
// with the time, then exercises the rand function.
//

#include <stdlib.h>
#include <stdio.h>
#include <time.h>

void SimpleRandDemo( int n )
{
   // Print n random numbers.
   int i;
   for( i = 0; i < n; i++ )
      printf( "  %6d\n", rand() );
}

void RangedRandDemo( int range_min, int range_max, int n )
{
   // Generate random numbers in the half-closed interval
   // [range_min, range_max). In other words,
   // range_min <= random number < range_max
   int i;
   for ( i = 0; i < n; i++ )
   {
      int u = (double)rand() / (RAND_MAX + 1) * (range_max - range_min)
            + range_min;
      printf( "  %6d\n", u);
   }
}

int main( void )
{
   // Seed the random-number generator with the current time so that
   // the numbers will be different every time we run.
   srand( (unsigned)time( NULL ) );

   SimpleRandDemo( 10 );
   printf("\n");
   RangedRandDemo( -100, 100, 10 );
}
```

```Output
22036
18330
11651
27464
18093
3284
11785
14686
11447
11285

   74
   48
   27
   65
   96
   64
   -5
  -42
  -55
   66
```

## <a name="see-also"></a>Consulte também

[Suporte a ponto flutuante](../../c-runtime-library/floating-point-support.md)<br/>
[srand](srand.md)<br/>
[rand_s](rand-s.md)<br/>
