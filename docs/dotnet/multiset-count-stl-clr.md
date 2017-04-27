---
title: "multiset::count (STL/CLR) | Microsoft Docs"
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
  - "cliext::multiset::count"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contar membro [STL/CLR]"
ms.assetid: 6c668667-0047-4101-8dfc-0f538655b3d1
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# multiset::count (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Localiza o número de elementos que correspondem a uma chave especificada.  
  
## Sintaxe  
  
```  
size_type count(key_type key);  
```  
  
#### Parâmetros  
 key  
 Valor de chave para pesquisar por.  
  
## Comentários  
 A função de membro retorna o número de elementos na sequência controlada que têm o equivalente que regras com `key`.  Use\-a para determinar atualmente o número de elementos na sequência controlada que correspondem a uma chave especificada.  
  
## Exemplo  
  
```  
// cliext_multiset_count.cpp   
// compile with: /clr   
#include <cliext/set>   
  
typedef cliext::multiset<wchar_t> Mymultiset;   
int main()   
    {   
    Mymultiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));   
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));   
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));   
    return (0);   
    }  
  
```  
  
  **um b c**  
**count \(L'A\) \= 0**  
**count \(L'b\) \= 1**  
**count \(L'C\) \= 0**   
## Requisitos  
 cliext \<\/conjunto de**Cabeçalho:** \>  
  
 cliext de**Namespace:**  
  
## Consulte também  
 [multiset](../dotnet/multiset-stl-clr.md)   
 [multiset::equal\_range](../dotnet/multiset-equal-range-stl-clr.md)