---
title: 'Como: Solicitar explicitamente a conversão Boxing'
ms.date: 11/04/2016
helpviewer_keywords:
- boxing, explicitly requesting
ms.assetid: 1359e6e5-162d-4f5d-9b6a-1690d93df3ee
ms.openlocfilehash: c27330e4e7699b6f0e9d6c612c2befe884a69b4c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387273"
---
# <a name="how-to-explicitly-request-boxing"></a>Como: Solicitar explicitamente a conversão Boxing

Você pode solicitar explicitamente a conversão boxing atribuindo uma variável para uma variável do tipo `Object`.

## <a name="example"></a>Exemplo

```
// vcmcppv2_explicit_boxing3.cpp
// compile with: /clr
using namespace System;

void f(int i) {
   Console::WriteLine("f(int i)");
}

void f(Object ^o) {
   Console::WriteLine("f(Object^ o)");
}

int main() {
   int i = 5;
   Object ^ O = i;   // forces i to be boxed
   f(i);
   f(O);
   f( (Object^)i );  // boxes i
}
```

```Output
f(int i)
f(Object^ o)
f(Object^ o)
```

## <a name="see-also"></a>Consulte também

[Conversão boxing](../extensions/boxing-cpp-component-extensions.md)
