---
title: Compilador aviso (nível 1) C4572
ms.date: 11/04/2016
f1_keywords:
- C4572
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
ms.openlocfilehash: e32509e4d32eef4f53b8d43a7db769844f1182c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397231"
---
# <a name="compiler-warning-level-1-c4572"></a>Compilador aviso (nível 1) C4572

Atributo [ParamArray] é preterido sob /clr, use '...' em vez disso

Um estilo obsoleto para especificar uma lista de argumentos de variável foi usado. Ao compilar para o CLR, use a sintaxe de reticências, em vez de <xref:System.ParamArrayAttribute>. Para obter mais informações, consulte [listas de argumentos variáveis (...) (C++/CLI) ](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

## <a name="example"></a>Exemplo

O exemplo a seguir gera C4572.

```
// C4572.cpp
// compile with: /clr /W1
void Func([System::ParamArray] array<int> ^);   // C4572
void Func2(... array<int> ^){}   // OK

int main() {
   Func2(1, 2, 3);
}
```