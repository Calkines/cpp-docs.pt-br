---
title: Erro do compilador C2937
ms.date: 11/04/2016
f1_keywords:
- C2937
helpviewer_keywords:
- C2937
ms.assetid: 95671ca3-79f7-4b56-a5f2-a92296da1629
ms.openlocfilehash: 8ad25dbcec4ee8a8ed49449cf9e64ebae4af1321
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366519"
---
# <a name="compiler-error-c2937"></a>Erro do compilador C2937

'class': id de classe de tipo é redefinido como um typedef global

Você não pode usar uma classe de modelo ou genérico como global `typedef`.

O exemplo a seguir gera C2937:

```
// C2937.cpp
// compile with: /c
template<class T>
struct TC { };
typedef int TC<int>;   // C2937
typedef TC<int> c;   // OK
```

C2937 também podem ocorrer ao usar genéricos:

```
// C2937b.cpp
// compile with: /clr
generic<class T>
ref struct GC { };
typedef int GC<int>;   // C2937
typedef GC<int> xx;   // OK
```