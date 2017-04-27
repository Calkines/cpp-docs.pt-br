---
title: "operador&lt;= (vector) (STL/CLR) | Microsoft Docs"
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
  - "cliext::vector::operator<="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Membro operator<= [STL/CLR]"
ms.assetid: d4f9d0ba-1fa3-4895-aef4-c9f9a06dbe05
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operador&lt;= (vector) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Vetor menor que ou igual comparação.  
  
## Sintaxe  
  
```  
template<typename Value>  
    bool operator<=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### Parâmetros  
 esquerda  
 Contêiner esquerdo da ser comparada.  
  
 direita  
 Contêiner direito da ser comparada.  
  
## Comentários  
 A função do operador retorna `!(``right` `<` `left``)`.  Você usa para testar se `left` não está ordenado depois de `right` quando os dois vetores elemento são comparados pelo elemento.  
  
## Exemplo  
  
```  
// cliext_vector_operator_le.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
  **um b c**  
 **um de b**  
**\[um b c \= um\] \<\[\] b c é true**  
**b de um \[\] \<\= \[um b c\] é false**   
## Requisitos  
 cliext \<\/vetor de**Cabeçalho:** \>  
  
 cliext de**Namespace:**  
  
## Consulte também  
 [vector](../dotnet/vector-stl-clr.md)   
 [operador\=\= \(vector\)](../Topic/operator==%20\(vector\)%20\(STL-CLR\).md)   
 [operador\!\= \(vector\)](../Topic/operator!=%20\(vector\)%20\(STL-CLR\).md)   
 [operador\< \(vector\)](../dotnet/operator-less-than-vector-stl-clr.md)   
 [operador\>\= \(vector\) \(STL\/CLR\)](../Topic/operator%3E=%20\(vector\)%20\(STL-CLR\).md)   
 [operador\> \(vector\)](../dotnet/operator-greater-than-vector-stl-clr.md)