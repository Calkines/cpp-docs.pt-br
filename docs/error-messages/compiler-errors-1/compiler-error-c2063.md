---
title: Erro do compilador C2063
ms.date: 11/04/2016
f1_keywords:
- C2063
helpviewer_keywords:
- C2063
ms.assetid: 0a90c18f-4029-416a-9128-e8713b53e6f1
ms.openlocfilehash: 5d91dc595798793899eb8ac33e2a6c71cabad02a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408635"
---
# <a name="compiler-error-c2063"></a>Erro do compilador C2063

'identifier': não é uma função

O identificador é usado como uma função, mas não declarado como uma função.

O exemplo a seguir gera C2063:

```
// C2063.c
int main() {
   int i, j;
   j = i();    // C2063, i is not a function
}
```

Solução possível:

```
// C2063b.c
int i() { return 0;}
int main() {
   int j;
   j = i();
}
```