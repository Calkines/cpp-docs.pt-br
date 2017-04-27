---
title: "multimap::rbegin (STL/CLR) | Microsoft Docs"
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
  - "cliext::multimap::rbegin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "membro rbegin [STL/CLR]"
ms.assetid: fd5a2a04-b03d-4920-b8f2-e01985cb91e3
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multimap::rbegin (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Designa o início da sequência controlada invertida.  
  
## Sintaxe  
  
```  
reverse_iterator rbegin();  
```  
  
## Comentários  
 A função de membro retorna um iterador invertido que designa o elemento o último de sequência controlada, ou apenas além do início de uma sequência vazia.  Consequentemente, designa `beginning` de sequência inversa.  Use\-a para obter um iterador que designa o início de `current` de sequência controlada consultada em ordem inversa, mas seu status pode ser alterado se o comprimento da sequência controlada é alterado.  
  
## Exemplo  
  
```  
// cliext_multimap_rbegin.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Mymultimap::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
  
```  
  
  **um \[1\] \[2\] \[b3 c\]**  
**\= \[\*rbegin\(\) 3 c\]**  
**\= \[\*\+\+rbegin\(\) b 2\]**   
## Requisitos  
 cliext \<\/mapa de**Cabeçalho:** \>  
  
 cliext de**Namespace:**  
  
## Consulte também  
 [multimapa](../dotnet/multimap-stl-clr.md)   
 [multimap::begin](../dotnet/multimap-begin-stl-clr.md)   
 [multimap::end](../dotnet/multimap-end-stl-clr.md)   
 [multimap::rend](../dotnet/multimap-rend-stl-clr.md)