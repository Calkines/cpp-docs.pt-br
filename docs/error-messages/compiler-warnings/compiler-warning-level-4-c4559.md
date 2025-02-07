---
title: Compilador aviso (nível 4) C4559
ms.date: 08/27/2018
f1_keywords:
- C4559
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
ms.openlocfilehash: afb4fb493c7c3e34ca691720a30d74517b0ab5b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220865"
---
# <a name="compiler-warning-level-4-c4559"></a>Compilador aviso (nível 4) C4559

> '*função*': redefinição; os ganhos de função declspec (*modificador*)

## <a name="remarks"></a>Comentários

Uma função foi redefinida ou declarado novamente e a segunda definição ou declaração adicionada uma **declspec** modificador (*modificador*). Esse aviso é informativo. Para corrigir este aviso, exclua uma das definições.

## <a name="example"></a>Exemplo

O exemplo a seguir gera C4559:

```cpp
// C4559.cpp
// compile with: /W4 /LD
void f();
__declspec(noalias) void f();   // C4559
```