---
title: Compilador aviso (nível 1) C4186
ms.date: 11/04/2016
f1_keywords:
- C4186
helpviewer_keywords:
- C4186
ms.assetid: caf3f7d8-f305-426b-8d4e-2b96f5c269ea
ms.openlocfilehash: fa5f0c3d3d409384b7cdc3c8a9cbe884732cbf8c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338500"
---
# <a name="compiler-warning-level-1-c4186"></a>Compilador aviso (nível 1) C4186

\#atributo de importação 'attribute' exige argumentos de contagem; ignorado

Um `#import` atributo tem um número incorreto de argumentos.

## <a name="example"></a>Exemplo

```
// C4186.cpp
// compile with: /W1 /c
#import "stdole2.tlb" no_namespace("abc") rename("a","b","c")  // C4186
```

O `no_namespace` atributo não utiliza argumentos. O **Renomear** atributo usa apenas dois argumentos.