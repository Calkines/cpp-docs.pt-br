---
title: 'hash_multiset:: lower_bound (STL/CLR) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_multiset::lower_bound
dev_langs: C++
helpviewer_keywords: lower_bound member [STL/CLR]
ms.assetid: 891898fa-c9e8-4132-a71d-36e5141793f1
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fb799c12bf153ed3279d8d3d6fb10d59bd1cf22d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="hashmultisetlowerbound-stlclr"></a>hash_multiset::lower_bound (STL/CLR)
Localiza o início do intervalo que corresponde a uma chave especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 key  
 O valor chave a ser pesquisado.  
  
## <a name="remarks"></a>Comentários  
 A função de membro determina o primeiro elemento `X` na sequência controlada coloca em hash para o mesmo bucket como `key` e tem ordenação equivalente ao `key`. Se esse elemento não existe, ele retorna [hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`; caso contrário, ele retorna um iterador que designa `X`. Você pode usá-lo para localizar o início de uma sequência de elementos no momento na sequência controlada que correspondem a uma chave especificada.  
  
## <a name="example"></a>Exemplo  
  
```  
// cliext_hash_multiset_lower_bound.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
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
  
```Output  
 a b c  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = a  
*lower_bound(L'b') = b  
```  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Consulte também  
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset:: Count (STL/CLR)](../dotnet/hash-multiset-count-stl-clr.md)   
 [hash_multiset:: equal_range (STL/CLR)](../dotnet/hash-multiset-equal-range-stl-clr.md)   
 [hash_multiset:: Find (STL/CLR)](../dotnet/hash-multiset-find-stl-clr.md)   
 [hash_multiset::upper_bound (STL/CLR)](../dotnet/hash-multiset-upper-bound-stl-clr.md)