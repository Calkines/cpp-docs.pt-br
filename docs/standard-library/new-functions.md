---
title: "Funções &lt;new&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
caps.latest.revision: 10
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 85c900f2263ae1c1089478badc85388e3b5e8548
ms.openlocfilehash: e32c8f5892764d2efc955bbf2d7930e0c8d3f3f0
ms.lasthandoff: 02/25/2017

---
# <a name="ltnewgt-functions"></a>Funções &lt;new&gt;
|||  
|-|-|  
|[nothrow](#nothrow)|[set_new_handler](#set_new_handler)|  
  
##  <a name="nothrow"></a>  nothrow  
 Fornece um objeto a ser usado como um argumento para as versões `nothrow` de **new** e **delete**.  
  
```  
extern const std::nothrow_t nothrow;  
```  
  
### <a name="remarks"></a>Comentários  
 O objeto é usado como um argumento de função para corresponder ao tipo de parâmetro [std::nothrow_t](../standard-library/nothrow-t-structure.md).  
  
### <a name="example"></a>Exemplo  
  Consulte [operador new](../standard-library/new-operators.md#operator_new) e [operador new&#91;&#93;](../standard-library/new-operators.md#operator_new_arr) para obter exemplos de como `std::nothrow_t` é usado como um parâmetro de função.  
  
##  <a name="set_new_handler"></a>  set_new_handler  
 Instala uma função de usuário que deve ser chamada quando `operator new` falhar ao tentar alocar memória.  
  
```  
new_handler set_new_handler(new_handler Pnew) throw();
```  
  
### <a name="parameters"></a>Parâmetros  
 `Pnew`  
 O new_handler a ser instalado.  
  
### <a name="return-value"></a>Valor de retorno  
 0 na primeira chamada e o anterior `new_handler` em chamadas subsequentes.  
  
### <a name="remarks"></a>Comentários  
 A função armazenará `Pnew` no ponteiro [new handler](../standard-library/new-typedefs.md#new_handler) estático que ele mantém e, então, retornará o valor armazenado anteriormente no ponteiro. O novo manipulador é usado por [operator new](../standard-library/new-operators.md#operator_new)( **size_t**).  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// new_set_new_handler.cpp  
// compile with: /EHsc  
#include<new>  
#include<iostream>  
  
using namespace std;  
void __cdecl newhandler( )  
{  
   cout << "The new_handler is called:" << endl;  
   throw bad_alloc( );  
   return;  
}  
  
int main( )   
{  
   set_new_handler (newhandler);  
   try  
   {  
      while ( 1 )   
      {  
         new int[5000000];  
         cout << "Allocating 5000000 ints." << endl;  
      }  
   }  
   catch ( exception e )  
   {  
      cout << e.what( ) << endl;  
   }  
}  
```  
  
```Output  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
Allocating 5000000 ints.  
The new_handler is called:  
bad allocation  
```  
  
## <a name="see-also"></a>Consulte também  
 [\<new>](../standard-library/new.md)

