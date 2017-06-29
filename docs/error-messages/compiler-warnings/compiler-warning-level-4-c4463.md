---
title: "Compilador (nível 4) de aviso C4463 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4463
dev_langs:
- C++
helpviewer_keywords:
- C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
caps.latest.revision: 0
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: 63f9c9172daffe11f91c521f514f0e8e53331b22
ms.contentlocale: pt-br
ms.lasthandoff: 05/10/2017

---
# <a name="compiler-warning-level-4-c4463"></a>Compilador C4463 de aviso (nível 4)  
  
> estouro; atribuindo *valor* para o campo de bits que pode conter apenas valores de *low_value* para *high_value*  
  
Atribuída *valor* está fora do intervalo de valores que o campo de bits pode conter. Tipos de campo de bits assinados usam a ordem de alto bit de entrada, portanto, se  *n*  é o tamanho de campo de bits, o intervalo para campos de bits assinados -2<sup>n-1</sup> 2<sup>n-1</sup>-1, enquanto os campos de bits sem sinal tem um intervalo de 0 a 2<sup>n</sup>-1.  
  
## <a name="example"></a>Exemplo  
  
Este exemplo gera C4463 porque ele tenta atribuir um valor de 3 a um campo de bits de tipo `int` com um tamanho de 2, que tem um intervalo de -2 para 1.  
  
Para corrigir esse problema, você pode alterar o valor atribuído para um valor no intervalo permitido. Se o campo de bits destina-se para manter os valores não assinados no intervalo de 0 a 3, você pode alterar o tipo de declaração para `unsigned`. Se o campo foi criado para manter os valores no intervalo -4 para 3, você pode alterar o tamanho de campo de bits para 3.  
  
```cpp  
// C4463_overflow.cpp
// compile with: cl /W4 /EHsc C4463_overflow.cpp
struct S { 
    int x : 2; // int type treats high-order bit as sign
}; 

int main() { 
    S s; 
    s.x = 3; // warning C4463: overflow; assigning 3 
    // to bit-field that can only hold values from -2 to 1 
    // To fix, change assigned value to fit in range,
    // increase size of bitfield, and/or change base type 
    // to unsigned.
} 
```  
