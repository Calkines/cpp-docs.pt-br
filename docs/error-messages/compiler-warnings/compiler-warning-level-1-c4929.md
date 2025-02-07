---
title: Compilador aviso (nível 1) C4929
ms.date: 11/04/2016
f1_keywords:
- C4929
helpviewer_keywords:
- C4929
ms.assetid: 95f8ab4f-4468-4caa-acd5-8f4592f03b3c
ms.openlocfilehash: 07081f2b8e305e20eb1725d3d76a6d77638caa7e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393396"
---
# <a name="compiler-warning-level-1-c4929"></a>Compilador aviso (nível 1) C4929

'file': typelibrary contém uma união; Ignorando o qualificador 'embedded_idl'

O atributo embedded_idl [#import](../../preprocessor/hash-import-directive-cpp.md) não puderam ser aplicadas à biblioteca de tipos como uma união está presente na biblioteca de tipos. Para resolver este aviso, não use embedded_idl.

## <a name="example"></a>Exemplo

O exemplo a seguir define um componente.

```
// C4929a.cpp
// compile with: /LD /link /TLBOUT:C4929a.tlb
#include <objbase.h>
[module(name="Test")];
[public, switch_type(short)] typedef union _TD_UNION_TYPE   {
   [case(24)]
      float fM;
   [case(25)]
      double dMN;
   [default]
      int x;
} TD_UNION_TYPE;

[export, public] typedef struct _TDW_TYPE {
   [switch_is(sU)] TD_UNION_TYPE w;
      short sU;
} TD_TYPE;

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I {
   HRESULT f(TD_TYPE*);
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct C : I {
   HRESULT f(TD_TYPE*) { return 0; }
};
```

## <a name="example"></a>Exemplo

O exemplo a seguir gera C4929.

```
// C4929b.cpp
// compile with: /c /W1
#import "C4929a.tlb" embedded_idl   // C4929
```