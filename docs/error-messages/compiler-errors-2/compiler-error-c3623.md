---
title: Erro do compilador C3623
ms.date: 11/04/2016
f1_keywords:
- C3623
helpviewer_keywords:
- C3623
ms.assetid: a0341b45-062a-4f67-beb9-ba74201ed1ed
ms.openlocfilehash: dd12e64e775807220b4ece1f4c26a2f52437c69e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221899"
---
# <a name="compiler-error-c3623"></a>Erro do compilador C3623

'variable': não há suporte para os campos de bits em gerenciado ou tipos WinRT

O uso de campos de bit não é permitido em variáveis em um gerenciado ou classe do WinRT.

O exemplo a seguir gera C3623:

```
// C3623.cpp
// compile with: /clr
using namespace System;
ref class CMyClass {
public:
   int i : 1;   // C3623
};

int main() {
   CMyClass^ pMyClass = gcnew CMyClass();
   pMyClass->i = 3;
   Console::Out->WriteLine(pMyClass->i);
}
```
