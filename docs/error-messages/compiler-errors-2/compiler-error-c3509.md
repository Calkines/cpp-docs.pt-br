---
title: Erro do compilador C3509
ms.date: 11/04/2016
f1_keywords:
- C3509
helpviewer_keywords:
- C3509
ms.assetid: cc2db39a-2f98-4e40-b803-496e585494e6
ms.openlocfilehash: e5e3c48581b5225bf1cf6777c9891c458034e11f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187471"
---
# <a name="compiler-error-c3509"></a>Erro do compilador C3509

'type': tipo de retorno de automação inválido; Quando um parâmetro está marcado como 'retval', o tipo de retorno deve ser 'void', 'HRESULT' ou 'SCODE'

Um método em uma interface COM deve retornar void ou um HRESULT.

O exemplo a seguir gera C3509:

```
// C3509.cpp
#define _ATL_DEBUG_QI

#define WIN32_LEAN_AND_MEAN   // Exclude rarely-used stuff from Windows headers
#define STRICT
#ifndef _WIN32_WINNT
#define _WIN32_WINNT 0x0400
#endif

#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
extern CComModule _Module;
#include <atlcom.h>
#include <atlctl.h>
#include <atlstr.h>

[module(name=oso)];

[dispinterface, uuid(00000000-0000-0000-0000-000000000001)]
__interface I {
   [id(1)] int f([out, retval] int*);   // C3509
   // try the following line instead
   // [id(1)] void f([out, retval] int*);
};

[coclass, uuid(00000000-0000-0000-0000-000000000002)]
struct C : I {
   int f(int*) {
   // try the following line instead, and delete return statement
   // void f(int*) {
      return 0;
   }
};

int main() {
}
```