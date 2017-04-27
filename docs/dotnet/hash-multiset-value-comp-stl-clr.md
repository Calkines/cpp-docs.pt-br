---
title: "hash_multiset:: value_comp (STL CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::value_comp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Membro value_comp [STL/CLR]"
ms.assetid: c5b25ded-9b27-43d5-9821-3f6e17338919
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::value_comp (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Copia o delegado de pedidos para os dois valores de elemento.  
  
## Sintaxe  
  
```  
value_compare^ value_comp();  
```  
  
## Comentários  
 A função de membro retorna o delegado de ordenação usado para ordenar a sequência controlada. Você pode usá\-lo para comparar dois valores de elemento.  
  
## Exemplo  
  
```  
// cliext_hash_multiset_value_comp.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
Comparar (L'a', L'a') = True compare (L'a', L'b') = True compare (L'b', L'a') = False  
```  
  
## Requisitos  
 **Cabeçalho:** \< cliext\/hash\_set \>  
  
 **Namespace:** cliext  
  
## Consulte também  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::value\_compare](../dotnet/hash-multiset-value-compare-stl-clr.md)   
 [hash\_multiset::value\_type](../dotnet/hash-multiset-value-type-stl-clr.md)