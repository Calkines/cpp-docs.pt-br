---
title: Erro do compilador C2691
ms.date: 11/04/2016
f1_keywords:
- C2691
helpviewer_keywords:
- C2691
ms.assetid: 6925f8f3-ea60-4909-91e6-b781492c645d
ms.openlocfilehash: 34287b785532394d33e94e37e7a6a9955d935f14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360184"
---
# <a name="compiler-error-c2691"></a>Erro do compilador C2691

'data type': gerenciada ou WinRTarray não pode ter esse tipo de elemento

O tipo de um ou um elemento da matriz WinRT pode ser um tipo de valor ou um tipo de referência.

O exemplo a seguir gera C2691:

```
// C2691a.cpp
// compile with: /clr
class A {};

int main() {
   array<A>^ a1 = gcnew array<A>(20);   // C2691
   array<int>^ a2 = gcnew array<int>(20);   // value type OK
}
```
