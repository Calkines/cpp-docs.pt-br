---
title: Compilador aviso (nível 1) C4141
ms.date: 11/04/2016
f1_keywords:
- C4141
helpviewer_keywords:
- C4141
ms.assetid: 6ce8c058-7f4c-41cf-93e7-90a466744656
ms.openlocfilehash: bbc2aea86c367c4977c8899e7aa9b8418e7fedcf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255649"
---
# <a name="compiler-warning-level-1-c4141"></a>Compilador aviso (nível 1) C4141

'modificador': usado mais de uma vez

## <a name="example"></a>Exemplo

```
// C4141.cpp
// compile with: /W1 /LD
inline inline void func ();   // C4141
```