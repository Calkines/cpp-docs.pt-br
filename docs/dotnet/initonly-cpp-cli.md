---
title: initonly (C++/CLI)
ms.date: 11/04/2016
f1_keywords:
- initonly_cpp
- initonly
helpviewer_keywords:
- initonly attribute [C++]
ms.assetid: f745d7fa-dc08-46f1-9b97-0977be58a008
ms.openlocfilehash: cdfc278225ce4ab418dfaaf41fb413d088ad77df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188402"
---
# <a name="initonly-ccli"></a>initonly (C++/CLI)

**InitOnly** é uma palavra-chave contextual que indica essa atribuição de variável pode ocorrer apenas como parte da declaração ou em um construtor estático na mesma classe.

O exemplo a seguir mostra como usar `initionly`:

```
// mcpp_initonly.cpp
// compile with: /clr /c
ref struct Y1 {
   initonly
   static int staticConst1;

   initonly
   static int staticConst2 = 0;

   static Y1() {
      staticConst1 = 0;
   }
};
```

## <a name="see-also"></a>Consulte também

[Classes e Structs](../extensions/classes-and-structs-cpp-component-extensions.md)
