---
title: Compilador aviso (nível 1) C4163
ms.date: 11/04/2016
f1_keywords:
- C4163
helpviewer_keywords:
- C4163
ms.assetid: b08413fd-03fc-4f41-9167-a98976ac12f2
ms.openlocfilehash: 737cf7ad00bfefd429792eed3f730844789e0c02
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391758"
---
# <a name="compiler-warning-level-1-c4163"></a>Compilador aviso (nível 1) C4163

'identifier': não disponível como uma função intrínseca

A função especificada não pode ser usada como um [intrínseco](../../preprocessor/intrinsic.md) função. O compilador ignora o nome de função inválido.

O exemplo a seguir gera C4163:

```
// C4163.cpp
// compile with: /W1 /LD
#include <math.h>
#pragma intrinsic(mysin)   // C4163
// try the following line instead
// #pragma intrinsic(sin)
```