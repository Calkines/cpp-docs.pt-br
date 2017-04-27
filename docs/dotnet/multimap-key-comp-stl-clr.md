---
title: "multimap::key_comp (STL/CLR) | Microsoft Docs"
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
  - "cliext::multimap::key_comp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Membro key_comp [STL/CLR]"
ms.assetid: 05250549-d589-4e1d-8ae9-321ff4ad384b
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multimap::key_comp (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Copia o representante de ordenação para duas chaves.  
  
## Sintaxe  
  
```  
key_compare^key_comp();  
```  
  
## Comentários  
 A função de membro retorna o delegado de classificação usado para ordenar a sequência controlada.  Use\-a para comparar duas chaves.  
  
## Exemplo  
  
```  
// cliext_multimap_key_comp.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    Mymultimap::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Mymultimap c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
  **compare \(L'a, L'a\) \= false**  
**compare \(L'a, L'b\) \= retificam**  
**compare \(L'b, L'a\) \= false**  
**compare \(L'a, L'a\) \= false**  
**compare \(L'a, L'b\) \= false**  
**compare \(L'b, L'a\) \= retificam**   
## Requisitos  
 cliext \<\/mapa de**Cabeçalho:** \>  
  
 cliext de**Namespace:**  
  
## Consulte também  
 [multimapa](../dotnet/multimap-stl-clr.md)   
 [multimap::key\_compare](../dotnet/multimap-key-compare-stl-clr.md)   
 [multimap::key\_type](../dotnet/multimap-key-type-stl-clr.md)