---
title: "Compilador aviso (nível 1) C4929 | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4929
dev_langs:
- C++
helpviewer_keywords:
- C4929
ms.assetid: 95f8ab4f-4468-4caa-acd5-8f4592f03b3c
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: c9a662904f764c1eba48f24d7fc7b97254fe0e51
ms.lasthandoff: 02/25/2017

---
# <a name="compiler-warning-level-1-c4929"></a>Compilador C4929 de aviso (nível 1)
'arquivo': typelibrary contém uma união; Ignorando o qualificador 'embedded_idl'  
  
 O atributo embedded_idl do [#import](../../preprocessor/hash-import-directive-cpp.md) não pôde ser aplicada à biblioteca de tipos como uma união está presente na biblioteca de tipos. Para resolver esse aviso, não use embedded_idl.  
  
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