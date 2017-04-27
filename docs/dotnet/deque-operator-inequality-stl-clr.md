---
title: "deque::operator!= (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::deque::operator!="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Membro operator!= [STL/CLR]"
ms.assetid: c23c7bd1-813e-4518-9947-eb13d1176a13
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# deque::operator!= (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Comparação diferente de Deque.  
  
## Sintaxe  
  
```  
template<typename Value>  
    bool operator!=(deque<Value>% left,  
        deque<Value>% right);  
```  
  
#### Parâmetros  
 esquerda  
 Contêiner esquerdo da ser comparada.  
  
 direita  
 Contêiner direito da ser comparada.  
  
## Comentários  
 A função do operador retorna `!(``left` `==` `right``)`.  Use\-a para testar se `left` não está ordenado da mesma forma que `right` quando os dois deques elemento são comparados pelo elemento.  
  
## Exemplo  
  
```  
// cliext_deque_operator_ne.cpp   
// compile with: /clr   
#include <cliext/deque>   
  
int main()   
    {   
    cliext::deque<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::deque<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
  
```  
  
  **um b c**  
 **um de b**  
**\[um b c\!\]\= \[um b c\] é false**  
**\[um b c\!\]\= um\] \[de b é true**   
## Requisitos  
 **Cabeçalho:** \<cliext\/deque\>  
  
 cliext de**Namespace:**  
  
## Consulte também  
 [deque](../dotnet/deque-stl-clr.md)   
 [operador\=\= \(deque\)](../dotnet/operator-equality-deque-stl-clr.md)   
 [operador\< \(deque\)](../dotnet/operator-less-than-deque-stl-clr.md)   
 [operador\>\= \(deque\)](../dotnet/operator-greater-or-equal-deque-stl-clr.md)   
 [operador\> \(deque\)](../dotnet/operator-greater-than-deque-stl-clr.md)   
 [operador\<\= \(deque\)](../dotnet/operator-less-or-equal-deque-stl-clr.md)