---
title: Erro do compilador C3047
ms.date: 11/04/2016
f1_keywords:
- C3047
helpviewer_keywords:
- C3047
ms.assetid: 91c14566-5958-433d-8549-0e8bc3196f76
ms.openlocfilehash: c73cdce4520b139c872c29b7809a46f55c3bebd1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187586"
---
# <a name="compiler-error-c3047"></a>Erro do compilador C3047

Bloco estruturado em um região de 'sections' deve ser precedido por '#pragma omp section' de OpenMP

Qualquer código em um bloco de código introduzido por uma [seções](../../parallel/openmp/reference/sections-openmp.md) diretiva deve estar em um bloco de código introduzido por um `section` diretiva.

O exemplo a seguir gera C3047:

```
// C3047.cpp
// compile with: /openmp /c
#include "omp.h"

int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
      {

         #pragma omp section
         {
            ++n3;
         }

         ++n2;   // C3047 not enclosed in #pragma omp section
      }
   }
}
```