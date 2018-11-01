---
title: Erro do compilador C2360
ms.date: 11/04/2016
f1_keywords:
- C2360
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
ms.openlocfilehash: 6e956ccb021dc3bce4d107e4aa6e0bbe4356283b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498170"
---
# <a name="compiler-error-c2360"></a>Erro do compilador C2360

inicialização de 'identifier' é ignorada por rótulo 'case'

A inicialização de `identifier` pode ser ignorada em um `switch` instrução. Você não pode ir após uma declaração com um inicializador, a menos que a declaração é incluída em um bloco. (A menos que ela é declarada dentro de um bloco, a variável está dentro do escopo até o final do `switch` instrução.)

O exemplo a seguir gera C2360:

```
// C2360.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      int i = 1;
      { int j = 1; }
   case 1 :   // C2360
      int k = 1;
   }
}
```

Solução possível:

```
// C2360b.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      { int j = 1; int i = 1;}
   case 1 :
      int k = 1;
   }
}
```