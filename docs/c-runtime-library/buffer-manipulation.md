---
title: Manipulação de buffer
ms.date: 04/04/2018
f1_keywords:
- c.memory
helpviewer_keywords:
- buffers, manipulation routines
- buffers
ms.assetid: 164f4860-ce66-412c-8291-396fbd70f03e
ms.openlocfilehash: e8a449cbfa6a52ccc2346e2215ce187c09d677e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590496"
---
# <a name="buffer-manipulation"></a>Manipulação de buffer

Use estas rotinas para trabalhar com áreas de memória em uma base byte por byte.

## <a name="buffer-manipulation-routines"></a>Rotinas de manipulação de buffer

|Rotina|Use|
|-------------|---------|
|[_memccpy](../c-runtime-library/reference/memccpy.md)|Copiar caracteres de um buffer para outro até que determinada caractere ou determinado número de caracteres foram copiados|
|[memchr, wmemchr](../c-runtime-library/reference/memchr-wmemchr.md)|Retorna o ponteiro para a primeira ocorrência dentro de um número especificado de caracteres, de determinado caractere no buffer|
|[memcmp, wmemcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|Compare o número especificado de caracteres de dois buffers|
|[memcpy, wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md), [memcpy_s, wmemcpy_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|Copia o número especificado de caracteres de um buffer para outro|
|[_memicmp, _memicmp_l](../c-runtime-library/reference/memicmp-memicmp-l.md)|Compare o número especificado de caracteres de dois buffers independentemente do caso|
|[memmove, wmemmove](../c-runtime-library/reference/memmove-wmemmove.md),[memmove_s, wmemmove_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|Copia o número especificado de caracteres de um buffer para outro|
|[memset, wmemset](../c-runtime-library/reference/memset-wmemset.md)|Dado o caractere para inicializar o número especificado de bytes no buffer de uso|
|[_swab](../c-runtime-library/reference/swab.md)|Troca os bytes de dados e armazená-os no local especificado|

Quando as áreas de origem e de destino se sobrepõem, apenas **memmove** é garantido para copiar a fonte completa corretamente.

## <a name="see-also"></a>Consulte também

[Rotinas de tempo de execução C universais por categoria](../c-runtime-library/run-time-routines-by-category.md)
