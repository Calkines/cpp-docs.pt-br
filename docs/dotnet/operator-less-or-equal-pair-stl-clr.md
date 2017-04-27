---
title: "operador&lt;= (pair) (STL/CLR) | Microsoft Docs"
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
  - "cliext::pair::operator<="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Membro operator<= [STL/CLR]"
ms.assetid: 94a4cc0a-cef4-4050-bd59-f826bd318e7b
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# operador&lt;= (pair) (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Pares menor que ou igual comparação.  
  
## Sintaxe  
  
```  
template<typename Value1,  
    typename Value2>  
    bool operator<=(pair<Value1, Value2>% left,  
        pair<Value1, Value2>% right);  
```  
  
#### Parâmetros  
 esquerda  
 Pares à esquerda da ser comparada.  
  
 direita  
 Pares direitos a ser comparado.  
  
## Comentários  
 A função do operador retorna `!(``right` `<` `left``)`.  Você usa para testar se `left` não está ordenado depois de `right` quando os dois pares são elemento comparado pelo elemento.  
  
## Exemplo  
  
```  
// cliext_pair_operator_le.cpp   
// compile with: /clr   
#include <cliext/utility>   
  
int main()   
    {   
    cliext::pair<wchar_t, int> c1(L'x', 3);   
    System::Console::WriteLine("[{0}, {1}]", c1.first, c1.second);   
    cliext::pair<wchar_t, int> c2(L'x', 4);   
    System::Console::WriteLine("[{0}, {1}]", c2.first, c2.second);   
  
    System::Console::WriteLine("[x 3] <= [x 3] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[x 4] <= [x 3] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
  
```  
  
  **\[x, 3\]**  
**\[x, 4\]**  
**\[\] \<\= \[x 3 x 3\] é true**  
**\[\] \<\= \[x 4 x 3\] é false**   
## Requisitos  
 cliext \<\/utilitário de**Cabeçalho:** \>  
  
 cliext de**Namespace:**  
  
## Consulte também  
 [par](../dotnet/pair-stl-clr.md)   
 [operador\=\= \(pair\)](../dotnet/operator-equality-pair-stl-clr.md)   
 [operador\!\= \(pair\)](../dotnet/operator-inequality-pair-stl-clr.md)   
 [operador\< \(pair\)](../dotnet/operator-less-than-pair-stl-clr.md)   
 [operador\>\= \(pair\)](../dotnet/operator-greater-or-equal-pair-stl-clr.md)   
 [operador\> \(pair\)](../dotnet/operator-greater-than-pair-stl-clr.md)