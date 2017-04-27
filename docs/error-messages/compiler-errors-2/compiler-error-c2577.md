---
title: C2577 de erro do compilador | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2577
dev_langs:
- C++
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
caps.latest.revision: 9
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
ms.openlocfilehash: 45b144945ce801374abdc4b0175d674c9684d0b4
ms.lasthandoff: 02/25/2017

---
# <a name="compiler-error-c2577"></a>C2577 de erro do compilador
'member': destruidor/finalizador não pode ter um tipo de retorno  
  
 Um destruidor ou finalizador não pode retornar um valor de `void` ou qualquer outro tipo. Remover o `return` instrução da definição de destruidor.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir gera C2577.  
  
```  
// C2577.cpp  
// compile with: /c  
class A {  
public:  
   A() {}  
   ~A(){  
      return 0;   // C2577  
   }  
};  
```