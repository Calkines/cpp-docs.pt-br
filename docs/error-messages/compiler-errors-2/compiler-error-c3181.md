---
title: Erro do compilador C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: dc848d4108ed4a1a7b6646647a1bbb1ec8dcadf7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382381"
---
# <a name="compiler-error-c3181"></a>Erro do compilador C3181

'type': operando inválido para o operador

Um parâmetro inválido foi passado para o [typeid](../../extensions/typeid-cpp-component-extensions.md) operador. O parâmetro deve ser um tipo gerenciado.

Observe que o compilador usa aliases para tipos nativos que são mapeados para tipos de common language runtime.

O exemplo a seguir gera C3181:

```
// C3181a.cpp
// compile with: /clr
using namespace System;

int main() {
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181
   Type ^pType2 = int::typeid;   // OK
}
```
