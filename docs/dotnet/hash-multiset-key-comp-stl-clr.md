---
title: "hash_multiset::key_comp (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_multiset::key_comp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Membro key_comp [STL/CLR]"
ms.assetid: b9653dd2-20f3-4ef3-875f-265749839ba6
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_multiset::key_comp (STL/CLR)
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
// cliext_hash_multiset_key_comp.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myhash_multiset c2 = cliext::greater<wchar_t>();   
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
  
  **compare \(L'a, L'a\) \= retificam**  
**compare \(L'a, L'b\) \= retificam**  
**compare \(L'b, L'a\) \= false**  
**compare \(L'a, L'a\) \= false**  
**compare \(L'a, L'b\) \= false**  
**compare \(L'b, L'a\) \= retificam**   
## Requisitos  
 cliext \<\/hash\_set de**Cabeçalho:** \>  
  
 cliext de**Namespace:**  
  
## Consulte também  
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_multiset::key\_compare](../dotnet/hash-multiset-key-compare-stl-clr.md)   
 [hash\_multiset::key\_type](../dotnet/hash-multiset-key-type-stl-clr.md)