---
title: Erro do compilador C2835
ms.date: 11/04/2016
f1_keywords:
- C2835
helpviewer_keywords:
- C2835
ms.assetid: 41c70630-983f-4da2-8342-513cf48b0519
ms.openlocfilehash: 069514d1a5d2b16e1175bbc1ce0c796bee64110a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406828"
---
# <a name="compiler-error-c2835"></a>Erro do compilador C2835

conversão definida pelo usuário 'type' não recebe parâmetros formais

Conversões de tipo definido pelo usuário não podem receber parâmetros formais.

O exemplo a seguir gera C2835:

```
// C2835.cpp
class A {
public:
   char v_char;

   A() {
      v_char = 'A';
   };
   operator char(char a) {   // C2835
   // try the following line instead
   // operator char() {
      return v_char + 1;
   };
};

int main() {
   A a;
}
```