---
title: "Compilador aviso (nível 1) C4154 | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4154
dev_langs:
- C++
helpviewer_keywords:
- C4154
ms.assetid: 4511afeb-e893-4cc6-83b6-4c7a0477f76b
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
ms.openlocfilehash: 6122e3bf663dae0c075351b32f97e9782588cb1f
ms.lasthandoff: 02/25/2017

---
# <a name="compiler-warning-level-1-c4154"></a>Compilador C4154 de aviso (nível 1)
exclusão de uma expressão de matriz; conversão para ponteiro fornecida  
  
 Não é possível usar `delete` em uma matriz, então o compilador converte a matriz a um ponteiro.  
  
## <a name="example"></a>Exemplo  
  
```  
// C4154.cpp  
// compile with: /c /W1  
int main() {  
   int array[ 10 ];  
   delete array;   // C4154 can't delete stack object  
  
   int *parray2 = new int [10];  
   int (&array2)[10] = (int(&)[10]) parray2;  
   delete [] array2;   // C4154  
  
   // try the following line instead  
   delete [] &array2;  
}  
```