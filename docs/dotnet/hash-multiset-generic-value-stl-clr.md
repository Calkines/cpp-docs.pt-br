---
title: "hash_multiset::generic_value (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::generic_value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Membro generic_value [STL/CLR]"
ms.assetid: 0be03b86-3e1c-42d2-b96f-a6080c7c4050
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::generic_value (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

O tipo de um elemento para uso com a interface genérica para o contêiner.  
  
## Sintaxe  
  
```  
typedef GValue generic_value;  
```  
  
## Comentários  
 O tipo descreve um objeto do tipo `GValue` que descreve o valor armazenado do elemento para uso com a interface genérica para esta classe do contêiner do modelo.  
  
## Exemplo  
  
```  
// cliext_hash_multiset_generic_value.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_multiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_multiset::generic_iterator gcit = gc1->begin();   
    Myhash_multiset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
  **um b c**  
 **um b c**  
 **a**   
## Requisitos  
 cliext \<\/hash\_set de**Cabeçalho:** \>  
  
 cliext de**Namespace:**  
  
## Consulte também  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::generic\_container](../dotnet/hash-multiset-generic-container-stl-clr.md)   
 [hash\_multiset::generic\_iterator](../dotnet/hash-multiset-generic-iterator-stl-clr.md)   
 [hash\_multiset::generic\_reverse\_iterator](../dotnet/hash-multiset-generic-reverse-iterator-stl-clr.md)