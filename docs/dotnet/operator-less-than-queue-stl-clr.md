---
title: "operador&lt; (queue) (STL/CLR) | Microsoft Docs"
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
  - "cliext::queue::operator<"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Membro operator< [STL/CLR]"
ms.assetid: 2c981e2b-9a88-4b4a-8060-9ac24d5631f5
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operador&lt; (queue) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Linha menor que a comparação.  
  
## Sintaxe  
  
```  
template<typename Value,  
    typename Container>  
    bool operator<(queue<Value, Container>% left,  
        queue<Value, Container>% right);  
```  
  
#### Parâmetros  
 esquerda  
 Contêiner esquerdo da ser comparada.  
  
 direita  
 Contêiner direito da ser comparada.  
  
## Comentários  
 A função do operador retornará true se, da mais baixa posição `i` para que `!(``right``[i] <` `left``[i])` ele também será true `left`que`[i] <` `right``[i]`.  Caso contrário, retorna `left``->`[queue::size](../dotnet/queue-size-stl-clr.md)`() <` `right``->size()` que você usa para testar se `left` é ordenado antes de `right` quando as duas filas são elemento comparado pelo elemento.  
  
## Exemplo  
  
```  
// cliext_queue_operator_lt.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::queue<wchar_t> Myqueue;   
int main()   
    {   
    Myqueue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myqueue c2;   
    c2.push(L'a');   
    c2.push(L'b');   
    c2.push(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
  
```  
  
  **um b c**  
 **um de b**  
**\[um b c\] \< \[um b c\] é false**  
**\[um b c\] \< \[\] de um b é true**   
## Requisitos  
 cliext \<\/fila de**Cabeçalho:** \>  
  
 cliext de**Namespace:**  
  
## Consulte também  
 [queue](../Topic/queue%20\(STL-CLR\).md)   
 [operador\=\= \(queue\)](../dotnet/operator-equality-queue-stl-clr.md)   
 [operador\!\= \(queue\)](../dotnet/operator-inequality-queue-stl-clr.md)   
 [operador\>\= \(queue\)](../Topic/operator%3E=%20\(queue\)%20\(STL-CLR\).md)   
 [operador\> \(queue\)](../dotnet/operator-greater-than-queue-stl-clr.md)   
 [operador\<\= \(queue\)](../dotnet/operator-less-or-equal-queue-stl-clr.md)