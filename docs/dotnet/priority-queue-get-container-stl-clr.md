---
title: "priority_queue::get_container (STL/CLR) | Microsoft Docs"
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
  - "cliext::priority_queue::get_container"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Membro get_container [STL/CLR]"
ms.assetid: bd3cc63b-776f-495c-bf81-a9e8ba189a56
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# priority_queue::get_container (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Acessa o contêiner subjacente.  
  
## Sintaxe  
  
```  
container_type get_container();  
```  
  
## Comentários  
 A função de membro retorna o contêiner subjacente.  Use\-a para ignorar as restrições impostas pelo wrapper do contêiner.  
  
## Exemplo  
  
```  
// cliext_priority_queue_get_container.cpp   
// compile with: /clr   
#include <cliext/queue>   
  
typedef cliext::priority_queue<wchar_t> Mypriority_queue;   
int main()   
    {   
    Mypriority_queue c1;   
    c1.push(L'a');   
    c1.push(L'b');   
    c1.push(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1.get_container())   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **c um b**   
## Requisitos  
 cliext \<\/fila de**Cabeçalho:** \>  
  
 cliext de**Namespace:**  
  
## Consulte também  
 [priority\_queue](../Topic/priority_queue%20\(STL-CLR\).md)   
 [priority\_queue::container\_type](../Topic/priority_queue::container_type%20\(STL-CLR\).md)