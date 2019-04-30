---
title: Erro do compilador C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 5d1260138bfdbc318817c336077eef326b62f8b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386623"
---
# <a name="compiler-error-c3755"></a>Erro do compilador C3755

'delegate': não é possível definir um delegado

Um [delegado (extensões de componentes C++)](../../extensions/delegate-cpp-component-extensions.md) pode ser declarada mas não definida.

## <a name="example"></a>Exemplo

O exemplo a seguir gera C3755.

```
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

## <a name="example"></a>Exemplo

C3755 também pode ocorrer se você tentar criar um modelo de delegado. O exemplo a seguir gera C3755.

```
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```