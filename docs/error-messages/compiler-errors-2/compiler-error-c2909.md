---
title: Erro do compilador C2909
ms.date: 11/04/2016
f1_keywords:
- C2909
helpviewer_keywords:
- C2909
ms.assetid: 1c9df8ae-925d-4002-a5f8-a71413c45f9e
ms.openlocfilehash: 7a777e87d8110ac16740346a8494f9501ce93b37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404280"
---
# <a name="compiler-error-c2909"></a>Erro do compilador C2909

'identifier': instanciação explícita de modelo de função requer tipo de retorno

Uma instanciação explícita de um modelo de função exige a especificação explícita de seu tipo de retorno. Especificação de tipo de retorno implícito não funciona.

O exemplo a seguir gera C2909:

```
// C2909.cpp
// compile with: /c
template<class T> int f(T);
template f<int>(int);         // C2909
template int f<int>(int);   // OK
```