---
title: _mm_stream_ss
ms.date: 09/02/2019
f1_keywords:
- _mm_stream_ss
helpviewer_keywords:
- movntss instruction
- _mm_stream_ss intrinsic
ms.assetid: c53dffe9-0dfe-4063-85d3-e8987b870fce
ms.openlocfilehash: 005f4f697d64f6ea68b35dc32daf1217be463a2a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217357"
---
# <a name="_mm_stream_ss"></a>_mm_stream_ss

**Seção específica da Microsoft**

Grava dados de 32 bits em um local de memória sem poluir os caches.

## <a name="syntax"></a>Sintaxe

```C
void _mm_stream_ss(
   float * Destination,
   __m128 Source
);
```

### <a name="parameters"></a>Parâmetros

*Destino*\
fora Um ponteiro para o local onde os dados de origem são gravados.

*Source*\
no Um número de 128 bits que contém o `float` valor a ser gravado em seus últimos 32 bits.

## <a name="return-value"></a>Valor retornado

nenhuma.

## <a name="requirements"></a>Requisitos

|Intrínseco|Arquitetura|
|---------------|------------------|
|`_mm_stream_ss`|SSE4a|

**Arquivo de cabeçalho** \<> intrin. h

## <a name="remarks"></a>Comentários

O intrínseco gera a `movntss` instrução. Para determinar o suporte de hardware para essa instrução, `__cpuid` chame o `InfoType=0x80000001` intrínseco e verifique o bit `CPUInfo[2] (ECX)`6 de. Esse bit é 1 quando há suporte para a instrução e 0 caso contrário.

Se você executar o código que usa `_mm_stream_ss` o intrínseco em hardware que não oferece `movntss` suporte à instrução, os resultados serão imprevisíveis.

## <a name="example"></a>Exemplo

```cpp
// Compile this sample with: /EHsc
#include <iostream>
#include <intrin.h>
using namespace std;

int main()
{
    __m128 vals;
    float f[4];

    f[0] = -1.;
    f[1] = -2.;
    f[2] = -3.;
    f[3] = -4.;
    vals.m128_f32[0] = 0.;
    vals.m128_f32[1] = 1.;
    vals.m128_f32[2] = 2.;
    vals.m128_f32[3] = 3.;
    _mm_stream_ss(&f[3], vals);
    cout << "f[0] = " << f[0] << ", f[1] = " << f[1] << endl;
    cout << "f[1] = " << f[1] << ", f[3] = " << f[3] << endl;
}
```

```Output
f[0] = -1, f[1] = -2
f[2] = -3, f[3] = 3
```

**Fim da seção específica da Microsoft**

Partes de Copyright 2007 da Advanced Micro Devices, Inc. Todos os direitos reservados. Reproduzida com a permissão da Advanced Micro Devices, Inc.

## <a name="see-also"></a>Consulte também

[_mm_stream_sd](../intrinsics/mm-stream-sd.md)\
[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)\
[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)\
[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)\
[Intrínsecos do compilador](../intrinsics/compiler-intrinsics.md)
