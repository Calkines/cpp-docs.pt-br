---
title: Erro do compilador C3176
ms.date: 11/04/2016
f1_keywords:
- C3176
helpviewer_keywords:
- C3176
ms.assetid: 6cc8d602-8e15-47a7-b1b5-e93e5d50e271
ms.openlocfilehash: 8c92a49499a18c12807f97cb97b24cc3beaf700b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174101"
---
# <a name="compiler-error-c3176"></a>Erro do compilador C3176

'type': não é possível declarar tipo value local

Uma classe somente pode ser declarada como um tipo de valor no escopo global.

## <a name="example"></a>Exemplo

O exemplo a seguir gera C3176.

```
// C3176.cpp
// compile with: /clr
int main () {
   enum class C {};   // C3176
}
```