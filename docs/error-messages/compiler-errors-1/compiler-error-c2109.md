---
title: Erro do compilador C2109
ms.date: 11/04/2016
f1_keywords:
- C2109
helpviewer_keywords:
- C2109
ms.assetid: 2d1ac79d-a985-4904-a38b-b270578d664d
ms.openlocfilehash: 6592f36b29fe643e088669089b1af1b69b7b2125
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62364747"
---
# <a name="compiler-error-c2109"></a>Erro do compilador C2109

subscrito requer tipo ponteiro ou matriz

O subscrito foi usado em uma variável que não era uma matriz.

O exemplo a seguir gera C2109:

```
// C2109.cpp
int main() {
   int a, b[10] = {0};
   a[0] = 1;   // C2109
   b[0] = 1;   // OK
}
```