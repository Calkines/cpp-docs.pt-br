---
title: "Compilador aviso (nível 1) C4155 | Documentos do Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4155
dev_langs:
- C++
helpviewer_keywords:
- C4155
ms.assetid: ba233353-09e3-4195-8127-13a27ddd8d70
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 8583c793d7511e354b9a32864b8b6a41f830f273
ms.lasthandoff: 02/25/2017

---
# <a name="compiler-warning-level-1-c4155"></a>Compilador C4155 de aviso (nível 1)
exclusão de uma expressão de matriz sem o uso da forma matricial de 'delete'  
  
 A forma de matriz de **excluir** deve ser usado para excluir uma matriz. Esse aviso ocorre apenas sob compatibilidade ANSI (/Za).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir gera C4155:  
  
```  
// C4155.cpp  
// compile with: /Za /W1  
#include <stdio.h>  
  
int main(void)  
{  
    int (*array)[ 10 ] = new int[ 5 ] [ 10 ];  
    array[0][0] = 8;  
  
    printf_s("%d\n", array[0][0]);  
  
   delete array;   // C4155  
    // try the following line instead  
    // delete [] array;   // C4155  
}  
```