---
title: Erro do compilador C3136
ms.date: 10/03/2018
f1_keywords:
- C3136
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
ms.openlocfilehash: e32ffca067c3b25120301527e7a708d53001d541
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376244"
---
# <a name="compiler-error-c3136"></a>Erro do compilador C3136

'interface': uma interface COM só pode herdar de outra interface COM, 'interface' não é uma interface COM

Uma interface para o qual você aplicou um [atributo interface](../../windows/attributes/interface-attributes.md) herda de uma interface que não é uma interface COM. Uma interface COM, por fim, herda `IUnknown`. Qualquer interface precedido por um atributo de interface é uma interface COM.

O exemplo a seguir gera C3136:

```
// C3136.cpp
#include "unknwn.h"

__interface A   // C3136
// try the following line instead
// _interface A : IUnknown
{
   int a();
};

[object]
__interface B : A
{
   int aa();
};
```