---
title: Erro do compilador C2272
ms.date: 11/04/2016
f1_keywords:
- C2272
helpviewer_keywords:
- C2272
ms.assetid: 1517706a-9c27-452e-9b10-3424b3d232bc
ms.openlocfilehash: 1a5a1e47a721cb6edd795012cc45943e63708936
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388885"
---
# <a name="compiler-error-c2272"></a>Erro do compilador C2272

'function': modificadores não permitidos em funções de membro estático

Um `static` função de membro é declarada com um especificador de modelo de memória, como [const](../../cpp/const-cpp.md) ou [volátil](../../cpp/volatile-cpp.md), e esses modificadores não são permitidos em `static` funções de membro.

O exemplo a seguir gera C2272:

```
// C2272.cpp
// compile with: /c
class CMyClass {
public:
   static void func1() const volatile;   // C2272  func1 is static
   void func2() const volatile;   // OK
};
```