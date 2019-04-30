---
title: __rdtsc
ms.date: 11/04/2016
f1_keywords:
- __rdtsc
helpviewer_keywords:
- __rdtsc intrinsic
- rdtsc instruction
- Read Time Stamp Counter instruction
ms.assetid: e31d0e51-c9bb-42ca-bbe9-a81ffe662387
ms.openlocfilehash: 6f30be3340ae1be237bb2f8a008a8cb60c7351f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396568"
---
# <a name="rdtsc"></a>__rdtsc

**Seção específica da Microsoft**

Gera o `rdtsc` instrução, que retorna o carimbo de data / hora do processador. O carimbo de data / hora do processador registra o número de ciclos de relógio desde a última reinicialização.

## <a name="syntax"></a>Sintaxe

```
unsigned __int64 __rdtsc();
```

## <a name="return-value"></a>Valor de retorno

Um inteiro sem sinal de 64 bits que representa uma contagem de tiques.

## <a name="requirements"></a>Requisitos

|Intrínseco|Arquitetura|
|---------------|------------------|
|`__rdtsc`|x86, x64|

**Arquivo de cabeçalho** \<intrin. h >

## <a name="remarks"></a>Comentários

Essa rotina só está disponível como um intrínseco.

A interpretação do valor TSC nessa geração de hardware é diferente do que em versões anteriores do x64. Consulte os manuais de hardware para obter mais informações.

## <a name="example"></a>Exemplo

```
// rdtsc.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(__rdtsc)

int main()
{
    unsigned __int64 i;
    i = __rdtsc();
    printf_s("%I64d ticks\n", i);
}
```

```Output
3363423610155519 ticks
```

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[Intrínsecos do compilador](../intrinsics/compiler-intrinsics.md)