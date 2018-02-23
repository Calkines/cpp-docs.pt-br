---
title: Map::to_array (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::map::to_array
dev_langs: C++
helpviewer_keywords: to_array member [STL/CLR]
ms.assetid: e7089d11-c968-4110-927a-97f9b5b8f992
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ae85e9ce43a5ce54b043e216ef7ee48d83c0f199
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="maptoarray-stlclr"></a>map::to_array (STL/CLR)
Copia uma nova matriz sequência controlada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
cli::array<value_type>^ to_array();  
```  
  
## <a name="remarks"></a>Comentários  
 A função de membro retorna uma matriz que contém a sequência controlada. Você pode usá-lo para obter uma cópia da sequência controlada no formulário de matriz.  
  
## <a name="example"></a>Exemplo  
  
```  
// cliext_map_to_array.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::map<wchar_t, int> Mymap;   
int main()   
    {   
    Mymap c1;   
    c1.insert(Mymap::make_value(L'a', 1));   
    c1.insert(Mymap::make_value(L'b', 2));   
    c1.insert(Mymap::make_value(L'c', 3));   
  
// copy the container and modify it   
    cli::array<Mymap::value_type>^ a1 = c1.to_array();   
  
    c1.insert(Mymap::make_value(L'd', 4));   
    for each (Mymap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (Mymap::value_type elem in a1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3] [d 4]  
[a 1] [b 2] [c 3]  
```  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<cliext/mapa >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Consulte também  
 [map (STL/CLR)](../dotnet/map-stl-clr.md)