---
title: Erro do compilador C3609
ms.date: 11/04/2016
f1_keywords:
- C3609
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
ms.openlocfilehash: 27eba3df800c42cc53a7031e958a675c84255440
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344521"
---
# <a name="compiler-error-c3609"></a>Erro do compilador C3609

'member': uma função selada ou final deve ser virtual

O [lacrado](../../extensions/sealed-cpp-component-extensions.md) e [final](../../cpp/final-specifier.md) palavras-chave são permitidas apenas em uma função de classe, struct ou membro marcada `virtual`.

O exemplo a seguir gera C3609:

```
// C3609.cpp
// compile with: /clr /c
ref class C {
   int f() sealed;   // C3609
   virtual int f2() sealed;   // OK
};
```
