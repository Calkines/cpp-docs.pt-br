---
title: Erro do compilador C3296
ms.date: 11/04/2016
f1_keywords:
- C3296
helpviewer_keywords:
- C3296
ms.assetid: fc4c9dcd-16cf-4eee-a1ac-c43e7c29e443
ms.openlocfilehash: c0a162590ac2a72dda17b2ecfc96899e94cde24c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222538"
---
# <a name="compiler-error-c3296"></a>Erro do compilador C3296

'property': já existe uma propriedade com esse nome

O compilador encontrou mais de uma propriedade com o mesmo nome. Cada propriedade em um tipo deve ter um nome exclusivo.

Para obter mais informações, consulte [propriedade](../../extensions/property-cpp-component-extensions.md).

## <a name="example"></a>Exemplo

O exemplo a seguir gera C3296.

```
// C3296.cpp
// compile with: /clr /c
using namespace System;

ref class R {
public:
   property int MyProp[int] { int get(int); }

   property String^ MyProp[int] { void set(int, String^); }   // C3296
};
```