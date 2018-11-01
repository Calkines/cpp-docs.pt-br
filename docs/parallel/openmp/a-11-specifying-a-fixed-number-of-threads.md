---
title: A.11   especificando um número fixo de threads
ms.date: 11/04/2016
ms.assetid: 1d06b142-4c35-44b8-994b-20f2aed5462b
ms.openlocfilehash: 832afac9abc7edd03d3af6f567657aefd596aae0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492033"
---
# <a name="a11---specifying-a-fixed-number-of-threads"></a>A.11   especificando um número fixo de threads

Alguns programas dependem de um número fixo previamente especificado de threads para executar corretamente.  Como a configuração padrão para o ajuste dinâmico do número de threads é definido pela implementação, esses programas podem optar por desativar o recurso dinâmico de threads e definir o número de threads explicitamente para garantir a portabilidade. O exemplo a seguir mostra como fazer isso usando `omp_set_dynamic` ([seção 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na página 39), e `omp_set_num_threads` ([seção 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na página de 36):

```
omp_set_dynamic(0);
omp_set_num_threads(16);
#pragma omp parallel shared(x, npoints) private(iam, ipoints)
{
    if (omp_get_num_threads() != 16)
      abort();
    iam = omp_get_thread_num();
    ipoints = npoints/16;
    do_by_16(x, iam, ipoints);
}
```

Neste exemplo, o programa seja executado corretamente somente se ele é executado pelo 16 threads. Se a implementação não é capaz de dar suporte a 16 threads, o comportamento deste exemplo é definido pela implementação.

Observe que o número de threads de execução de uma região parallel permanece constante durante uma região parallel, independentemente dos threads dinâmicos de configuração. O mecanismo de threads dinâmica determina o número de threads a serem usados no início da região paralela e mantém constante para a duração da região.