---
title: Erro do compilador C2046
ms.date: 11/04/2016
f1_keywords:
- C2046
helpviewer_keywords:
- C2046
ms.assetid: f0c8f9dd-dbd7-4c4a-8838-fde54208ec71
ms.openlocfilehash: b502c70c62d87d6807f586e289aaa5c67be9f048
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182828"
---
# <a name="compiler-error-c2046"></a>Erro do compilador C2046

case inválido

A palavra-chave `case` pode aparecer somente em um `switch` instrução.

O exemplo a seguir gera C2046:

```
// C2046.cpp
int main() {
   case 0:   // C2046
}
```

Solução possível:

```
// C2046b.cpp
int main() {
   int i = 0;

   switch(i) {
      case 0:
      break;

      default:
      break;
   }
}
```