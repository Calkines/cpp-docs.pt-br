---
title: Erro do compilador C3036
ms.date: 11/04/2016
f1_keywords:
- C3036
helpviewer_keywords:
- C3036
ms.assetid: 10c6993e-bc42-4a07-85c7-cdc34ac30906
ms.openlocfilehash: c1dc060a5d198b78e652a1b6b239655439209f66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350212"
---
# <a name="compiler-error-c3036"></a>Erro do compilador C3036

'operator': token de operador inválido em cláusula de OpenMP 'reduction'

Um [redução](../../parallel/openmp/reference/reduction.md) cláusula não foi especificada corretamente.

O exemplo a seguir gera C3036:

```
// C3036.cpp
// compile with: /openmp
static float a[1000], b[1000], c[1000];
void test1(int first, int last) {
   static float dp = 0.0f;
   #pragma omp for nowait reduction(.:dp)   // C3036
   // try the following line instead
   // #pragma omp for nowait reduction(+: dp)
   for (int i = first ; i <= last ; ++i)
      dp += a[i] * b[i];
}
```