---
title: 'List:: push_front (STL/CLR) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::list::push_front
dev_langs: C++
helpviewer_keywords: push_front member [STL/CLR]
ms.assetid: 47525641-1139-44fc-ac62-bdc04876d9e0
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8e58f2994755363b91b639eebc871066e321a479
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="listpushfront-stlclr"></a>list::push_front (STL/CLR)
Adiciona um novo elemento primeiro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
void push_front(value_type val);  
```  
  
## <a name="remarks"></a>Comentários  
 A função de membro insere um elemento com o valor `val` no início da sequência controlada. Você pode usá-lo para preceder a outro elemento à lista.  
  
## <a name="example"></a>Exemplo  
  
```  
// cliext_list_push_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_front(L'a');   
    c1.push_front(L'b');   
    c1.push_front(L'c');   
  
// display contents " c b a"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<cliext/lista >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Consulte também  
 [lista (STL/CLR)](../dotnet/list-stl-clr.md)   
 [List:: pop_back (STL/CLR)](../dotnet/list-pop-back-stl-clr.md)   
 [List:: pop_front (STL/CLR)](../dotnet/list-pop-front-stl-clr.md)   
 [list::push_back (STL/CLR)](../dotnet/list-push-back-stl-clr.md)