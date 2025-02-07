---
title: _mm_cvttss_si64x
ms.date: 09/02/2019
f1_keywords:
- _mm_cvttss_si64x
helpviewer_keywords:
- _mm_cvttss_si64x intrinsic
- cvttss2si instruction
ms.assetid: f9a3fd07-5bd8-4758-8744-6315c082cf87
ms.openlocfilehash: 69016a4e23b020b2c4c79c6b97a5a76f2b2dc028
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217421"
---
# <a name="_mm_cvttss_si64x"></a>_mm_cvttss_si64x

**Seção específica da Microsoft**

Emite a versão estendida x64 do número de ponto flutuante de conversão com truncamento de precisão única para instrução de inteiro de 64`cvttss2si`bits ().

## <a name="syntax"></a>Sintaxe

```C
__int64 _mm_cvttss_si64x(
   __m128 value
);
```

### <a name="parameters"></a>Parâmetros

*value*\
no Uma `__m128` estrutura que contém valores de ponto flutuante de precisão simples.

## <a name="return-value"></a>Valor retornado

O resultado da conversão do primeiro valor de ponto flutuante para um inteiro de 64 bits.

## <a name="requirements"></a>Requisitos

|Intrínseco|Arquitetura|
|---------------|------------------|
|`_mm_cvttss_si64x`|X64|

**Arquivo de cabeçalho** \<> intrin. h

## <a name="remarks"></a>Comentários

O intrínseco difere do `_mm_cvtss_si64x` somente nas conversões exatas que são truncadas para zero. Como a `__m128` estrutura representa um registro de XMM, a instrução gerada move os dados de um registro de XMM para a memória do sistema.

Essa rotina só está disponível como função intrínseca.

## <a name="example"></a>Exemplo

```cpp
// _mm_cvttss_si64x.cpp
// processor: x64
#include <intrin.h>
#include <stdio.h>

#pragma intrinsic(_mm_cvttss_si64x)

int main()
{
    __m128 a;
    __int64 b = 54;

    // _mm_load_ps requires an aligned buffer.
    __declspec(align(16)) float af[4] = { 101.5, 200.75,
                                          300.5, 400.5 };

    // Load a with the floating point values.
    // The values will be copied to the XMM registers.
    a = _mm_load_ps(af);

    // Extract the first element of a and convert to an integer
    b = _mm_cvttss_si64x(a);

    printf_s("%I64d\n", b);
}
```

```Output
101
```

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[__m128](../cpp/m128.md)\
[Intrínsecos do compilador](../intrinsics/compiler-intrinsics.md)
