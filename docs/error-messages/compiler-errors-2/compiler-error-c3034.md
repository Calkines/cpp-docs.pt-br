---
title: Erro do compilador C3034
ms.date: 11/04/2016
f1_keywords:
- C3034
helpviewer_keywords:
- C3034
ms.assetid: 49db8bac-2720-4622-94e3-7988f1603fa3
ms.openlocfilehash: d0a5da87feeabc5d3d5b558ce0dd6bdfe3869d53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165561"
---
# <a name="compiler-error-c3034"></a>Erro do compilador C3034

Diretiva de OpenMP 'directive1' não pode ser aninhada diretamente dentro de diretiva de 'directive2'

Algumas políticas não podem ser aninhadas. Para corrigir esse erro, você pode mesclar as declarações de ambas as diretivas com o bloco de uma diretiva de, ou você pode construir diretivas consecutivas.

O exemplo a seguir gera C3034:

```
// C3034.cpp
// compile with: /openmp /link vcomps.lib
int main() {

   #pragma omp single
   {
      #pragma omp single   // C3034
      {
      ;
      }
   }

   // Two consecutive single clauses are OK.
   #pragma omp single
   {
   }

   #pragma omp single
   {
   }
}
```