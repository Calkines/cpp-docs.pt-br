---
title: Compilador aviso (nível 4) C4460
ms.date: 11/04/2016
f1_keywords:
- C4460
helpviewer_keywords:
- C4460
ms.assetid: c97ac1c9-598d-479e-bfff-c993690c4f3d
ms.openlocfilehash: a42562a2c35bb56de4ce7147e199f4db2dddb684
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400806"
---
# <a name="compiler-warning-level-4-c4460"></a>Compilador aviso (nível 4) C4460

WinRT ou CLR operador 'operator', parâmetro tiver passado por referência. O operador 'operator WinRT ou CLR' tem uma semântica diferente do operador de C++ 'operator', você pretendia passar por valor?

Um valor pode ser transmitido por referência para um operador de tempo de execução do Windows ou do CLR definidas pelo usuário. Se o valor for alterado dentro da função, observe que o valor retornado depois que a chamada de função será atribuída o valor de retorno da função. No C++ padrão, o valor alterado será refletido após a chamada de função.

## <a name="example"></a>Exemplo

O exemplo a seguir gera C4460 e mostra como corrigi-lo.

```
// C4460.cpp
// compile with: /W4 /clr
#include <stdio.h>

public value struct V {
   static V operator ++(V& me) {   // C4460
   // try the following line instead
   // static V operator ++(V me) {

      printf_s(__FUNCSIG__ " called\n");
      V tmp = me;
      me.m_i++;
      return tmp;
   }
   int m_i;
};

int main() {
   V v;
   v.m_i = 0;

   printf_s("%d\n", v.m_i);   // Should print 0
   v++;   // Translates to "v = V::operator ++(v)"
   printf_s("%d\n", v.m_i);   // will print 0, hence the warning
}
```