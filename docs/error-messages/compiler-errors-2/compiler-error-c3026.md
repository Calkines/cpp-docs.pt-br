---
title: Erro do compilador C3026
ms.date: 11/04/2016
f1_keywords:
- C3026
helpviewer_keywords:
- C3026
ms.assetid: 3297060e-cc5b-4600-a2db-09bfc4ffa21f
ms.openlocfilehash: da3c42433448dccea9f33e34b771da85d7e5b747
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360054"
---
# <a name="compiler-error-c3026"></a>Erro do compilador C3026

'cláusula': expressão constante deve ser positiva

Uma cláusula foi passada um valor inteiro, mas o valor não era um número positivo. O número deve ser positivo.

## <a name="example"></a>Exemplo

O exemplo a seguir gera C3026:

```
// C3026.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

int main()
{
    int i;
    const int i1 = 0;

    #pragma omp parallel for num_threads(i1)   // C3026
    for (i = 1; i <= 2; ++i)
        printf_s("Hello World - thread %d - iteration %d\n",
                 omp_get_thread_num(), i);

    #pragma omp parallel for num_threads(i1 + 1)   // OK
    for (i = 1; i <= 2; ++i)
        printf_s("Hello World - thread %d - iteration %d\n",
                 omp_get_thread_num(), i);
}
```