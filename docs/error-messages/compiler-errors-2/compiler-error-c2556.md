---
title: Erro do compilador C2556
ms.date: 11/04/2016
f1_keywords:
- C2556
helpviewer_keywords:
- C2556
ms.assetid: fc4399ad-45b3-49fd-be1f-0b13956a595a
ms.openlocfilehash: 4a2b4dc9dcd71d518845651dee97c566b778eb0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353060"
---
# <a name="compiler-error-c2556"></a>Erro do compilador C2556

'identifier': funções sobrecarregadas diferem apenas pelo tipo de retorno

As funções sobrecarregadas têm diferentes tipos de retorno, mas a mesma lista de parâmetros. Cada função sobrecarregada deve ter uma lista de parâmetros formal distinta.

O exemplo a seguir gera C2556:

```
// C2556.cpp
// compile with: /c
class C {
   int func();
   double func();   // C2556
   int func(int i);   // ok parameter lists differ
};
```