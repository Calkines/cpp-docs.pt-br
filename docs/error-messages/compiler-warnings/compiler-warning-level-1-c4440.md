---
title: Compilador aviso (nível 1) C4440
ms.date: 11/04/2016
f1_keywords:
- C4440
helpviewer_keywords:
- C4440
ms.assetid: 78b9642a-a93e-401e-9d92-372f6451bc5d
ms.openlocfilehash: ccd7c14cbd078d4740795d25ad772bdc78840a60
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660040"
---
# <a name="compiler-warning-level-1-c4440"></a>Compilador aviso (nível 1) C4440

chamar a redefinição de convenção de 'calling_convention1' para 'calling_convention2' ignorado

Uma tentativa de alterar a convenção de chamada foi ignorada.

O exemplo a seguir gera C4440:

```
// C4440.cpp
// compile with: /W1 /LD /clr
typedef void __clrcall F();
typedef F __cdecl *PFV;   // C4440
```