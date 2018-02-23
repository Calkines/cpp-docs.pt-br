---
title: 'Vector:: Insert (STL/CLR) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::vector::insert
dev_langs: C++
helpviewer_keywords: insert member [STL/CLR]
ms.assetid: f240cabf-f9d1-40c1-9cfb-975a90955546
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b330a9e0b8a11f41ceab4f604b73b93e8f1d735a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="vectorinsert-stlclr"></a>vector::insert (STL/CLR)
Adiciona os elementos em uma posição especificada.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 count  
 Número de elementos a inserir.  
  
 primeiro  
 Início do intervalo a ser inserido.  
  
 last  
 Fim do intervalo a ser inserido.  
  
 direita  
 Enumeração para inserir.  
  
 Val  
 Valor do elemento a ser inserido.  
  
 onde  
 Onde no contêiner para inserir antes.  
  
## <a name="remarks"></a>Comentários  
 Cada membro funções inserções, antes do elemento apontada pelo `where` na sequência controlada, uma sequência especificado pelo operandos restantes.  
  
 A primeira função de membro insere um elemento com o valor `val` e retorna um iterador que designa o elemento recentemente inserido. Você pode usá-lo para inserir um único elemento antes de um local designado por um iterador.  
  
 A segunda função membro insere uma repetição de elementos `count` de valor `val`. Você pode usá-lo para inserir zero ou mais elementos contíguos que são todas as cópias do mesmo valor.  
  
 Se `InIt` for um tipo inteiro, a terceira função membro se comportará da mesma forma que `insert(where, (size_type)first, (value_type)last)`. Caso contrário, ele insere a sequência [`first`, `last`). Você pode usá-lo para inserir zero ou mais elementos contíguos copiados de outra sequência.  
  
 A função de membro quarta insere a sequência designada pelo `right`. Você pode usá-lo para inserir uma sequência descrita por um enumerador.  
  
 Ao inserir um único elemento, o número de cópias do elemento é linear no número de elementos entre o ponto de inserção e a extremidade mais próximo da sequência. (Ao inserir um ou mais elementos em ambas as extremidades da sequência, nenhuma cópia do elemento ocorre). Se `InIt` é um iterador de entrada, a terceira função do membro efetivamente executa uma inserção única para cada elemento na sequência. Caso contrário, quando inserir `N` elementos, o número de cópias do elemento é linear em `N` mais o número de elementos entre o ponto de inserção e a extremidade mais próximo da sequência.  
  
## <a name="example"></a>Exemplo  
  
```  
// cliext_vector_insert.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::vector<wchar_t> c2;   
    c2.insert(c2.begin(), 2, L'y');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    it = c1.end();   
    c2.insert(c2.end(), c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    c2.insert(c2.begin(),   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(begin()+1, L'x') = x  
 a x b c  
 y y  
 y y a x b  
 a x b c y y a x b  
```  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<cliext/vetor >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>Consulte também  
 [vetor (STL/CLR)](../dotnet/vector-stl-clr.md)   
 [vector::assign (STL/CLR)](../dotnet/vector-assign-stl-clr.md)