---
title: Erro do compilador C2811
ms.date: 11/04/2016
f1_keywords:
- C2811
helpviewer_keywords:
- C2811
ms.assetid: 6a44b18e-44c1-49d8-9b99-e0545b9a6e7d
ms.openlocfilehash: 8dfc462cc0eedfff1661ae38f79bbb79c5c1a8fa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62281749"
---
# <a name="compiler-error-c2811"></a>Erro do compilador C2811

'type1': não pode herdar de 'type2', uma referência de classe pode herdar apenas de uma classe ref ou classe de interface

Você tentou usar uma classe não gerenciada como uma classe base para uma classe gerenciada.

O exemplo a seguir gera C2811:

```
// C2811.cpp
// compile with: /clr /c
struct S{};
ref struct T {};
ref class C : public S {};   // C2811
ref class D : public T {};   // OK
```