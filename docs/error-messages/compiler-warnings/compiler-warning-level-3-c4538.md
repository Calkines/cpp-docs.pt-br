---
title: Compilador aviso (nível 3) C4538
ms.date: 11/04/2016
f1_keywords:
- C4538
helpviewer_keywords:
- C4538
ms.assetid: 747e3d51-b6d0-41c1-a726-7af3253b59d7
ms.openlocfilehash: e0f20c7b1d9f840bc272cd3b9d43f4872ac3f71d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401833"
---
# <a name="compiler-warning-level-3-c4538"></a>Compilador aviso (nível 3) C4538

'type': não há suporte para qualificadores const/volatile neste tipo

Uma palavra-chave qualificador foi aplicada a uma matriz incorretamente. Para obter mais informações, consulte [matriz](../../extensions/arrays-cpp-component-extensions.md).

O exemplo a seguir gera C4538:

```
// C4538.cpp
// compile with: /clr /W3 /LD
const array<int> ^f1();   // C4538
array<const int> ^f2();   // OK
```