---
title: Erro do compilador C2428
ms.date: 11/04/2016
f1_keywords:
- C2428
helpviewer_keywords:
- C2428
ms.assetid: 74aa5714-e930-4f9e-9061-68ccce7f0d38
ms.openlocfilehash: 299a4e899a41bf47eec5eaf5b54d2307e557078e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165821"
---
# <a name="compiler-error-c2428"></a>Erro do compilador C2428

'operation': não é permitido em operando do tipo 'bool'

É possível aplicar um operador de decremento a objetos do tipo `bool`.

O exemplo a seguir gera C2428:

```
// C2428.cpp
void g(bool fFlag) {
   --fFlag;   // C2428
   fFlag--;   // C2428
}
```