---
title: Erro do compilador C3120
ms.date: 11/04/2016
f1_keywords:
- C3120
helpviewer_keywords:
- C3120
ms.assetid: 9b6b210f-9948-4517-a4cc-b4aaadebde68
ms.openlocfilehash: 99d6280420111fde1a2e2187e3cbaeb529652d01
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62281593"
---
# <a name="compiler-error-c3120"></a>Erro do compilador C3120

'method_name': métodos de interface não podem conter uma lista de argumentos variáveis

Um método de interface não pode conter uma lista de argumentos variáveis. Por exemplo, a seguinte definição de interface gera C3120:

```
// C3120.cpp
__interface A {
int X(int i, ...);    // C3120
};

int main(void) { return(0); }
```