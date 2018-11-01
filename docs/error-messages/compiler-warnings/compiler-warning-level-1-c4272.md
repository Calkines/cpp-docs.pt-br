---
title: Compilador aviso (nível 1) C4272
ms.date: 11/04/2016
f1_keywords:
- C4272
helpviewer_keywords:
- C4272
ms.assetid: 0d6c1de4-2eef-42c4-b861-c221f8b495ef
ms.openlocfilehash: 26e136aa395729d520f4a71a06b6dc212cf21f8b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479983"
---
# <a name="compiler-warning-level-1-c4272"></a>Compilador aviso (nível 1) C4272

'function': está marcado como __declspec(dllimport); deve especificar a convenção de chamada nativa ao importar uma função.

É um erro ao exportar uma função marcada com o [clrcall](../../cpp/clrcall.md) convenção de chamada e o compilador emite esse aviso se você tentar importar uma função marcada como `__clrcall`.

O exemplo a seguir gera C4272:

```
// C4272.cpp
// compile with: /c /W1 /clr
__declspec(dllimport) void __clrcall Test();   // C4272
__declspec(dllimport) void Test2();   // OK
```