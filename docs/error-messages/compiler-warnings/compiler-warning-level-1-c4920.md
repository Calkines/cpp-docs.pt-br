---
title: Compilador aviso (nível 1) C4920
ms.date: 11/04/2016
f1_keywords:
- C4920
helpviewer_keywords:
- C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
ms.openlocfilehash: cd501cf0e3b434523623276027056c93c77fc278
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393474"
---
# <a name="compiler-warning-level-1-c4920"></a>Compilador aviso (nível 1) C4920

membro de membro de enumeração de enum = valor já visto em enumeração de enum como membro = valor

Se um TLB que você passa para #import tem o mesmo símbolo definido em dois ou mais enumerações, este aviso indica que símbolos idênticos subsequentes serão ignorados e serão ser comentados no arquivo. TLH.

Supondo que um. tlb que contém:

```
library MyLib
{
    typedef enum {
        enumMember = 512
    } AProblem;

    typedef enum {
        enumMember = 1024
    } BProblem;
};
```

Os exemplos a seguir gera C4920,

```
// C4920.cpp
// compile with: /W1
#import "t4920.tlb"   // C4920

int main() {
}
```