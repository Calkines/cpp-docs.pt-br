---
title: Erro do compilador C2233
ms.date: 11/04/2016
f1_keywords:
- C2233
helpviewer_keywords:
- C2233
ms.assetid: 236bdf0b-9607-4f26-a249-d8def0b1333c
ms.openlocfilehash: 7d96230f189a8f9371473d2da4df4e7be295ab03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375958"
---
# <a name="compiler-error-c2233"></a>Erro do compilador C2233

'identifier': matrizes de objetos contendo matrizes de tamanho zero são inválidas

Cada objeto em uma matriz deve conter pelo menos um elemento.

O exemplo a seguir gera C2233:

```
// C2233.cpp
// compile with: /c
class A {
   char somearray[1];
};

class B {
   char zeroarray[];
};

A array[100];   // OK
B array2[100];   // C2233
```