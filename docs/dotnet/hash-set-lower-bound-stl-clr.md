---
title: "hash_set::lower_bound (STL/CLR) | Microsoft Docs"
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
  - "cliext::hash_set::lower_bound"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Membro lower_bound [STL/CLR]"
ms.assetid: 54fe8ee5-1977-4192-9cc6-b51e84b03a16
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# hash_set::lower_bound (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Localiza o início do intervalo que corresponde a uma chave especificada.  
  
## Sintaxe  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### Parâmetros  
 key  
 Valor de chave para pesquisar por.  
  
## Comentários  
 A função de membro determina o primeiro elemento `X` na sequência controlada que o uso do mesmo partição que `key` e tem o equivalente de ordenação da `key`.  Se tal elemento, ele retornará [hash\_set::end](../dotnet/hash-set-end-stl-clr.md)`()`; se não retorna um iterador que designa `X`.  Você usa para localizar no início de uma sequência de elementos na sequência controlada que correspondem a uma chave especificada.  
  
## Exemplo  
  
```  
// cliext_hash_set_lower_bound.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_set<wchar_t> Myhash_set;   
int main()   
    {   
    Myhash_set c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*lower_bound(L'a') = {0}",   
        *c1.lower_bound(L'a'));   
    System::Console::WriteLine("*lower_bound(L'b') = {0}",   
        *c1.lower_bound(L'b'));   
    return (0);   
    }  
  
```  
  
  **um b c**  
**lower\_bound\(L'x'\)\=\=end\(\) \= retifica**  
**\*lower\_bound \(L'a\) \= a**  
**\*lower\_bound \(L'b\) \= b**   
## Requisitos  
 cliext \<\/hash\_set de**Cabeçalho:** \>  
  
 cliext de**Namespace:**  
  
## Consulte também  
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [hash\_set::count](../dotnet/hash-set-count-stl-clr.md)   
 [hash\_set::equal\_range](../dotnet/hash-set-equal-range-stl-clr.md)   
 [hash\_set::find](../Topic/hash_set::find%20\(STL-CLR\).md)   
 [hash\_set::upper\_bound](../dotnet/hash-set-upper-bound-stl-clr.md)