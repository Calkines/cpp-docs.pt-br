---
title: "hash_set::iterator (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_set::iterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "membro iterador [STL/CLR]"
ms.assetid: b75fc54f-6a9e-4ce8-a168-988afe7fe7e5
caps.latest.revision: 15
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_set::iterator (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

O tipo de um iterador para a sequência controlada.  
  
## Sintaxe  
  
```  
typedef T1 iterator;  
```  
  
## Comentários  
 O tipo descreve um objeto do tipo não for especificado `T1` que pode servir como um iterador bidirecional para a sequência controlada.  
  
## Exemplo  
  
```  
// cliext_hash_set_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myhash_set::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
  **um b c**   
## Requisitos  
 cliext \<\/hash\_set de**Cabeçalho:** \>  
  
 cliext de**Namespace:**  
  
## Consulte também  
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set::const\_iterator](../dotnet/hash-set-const-iterator-stl-clr.md)