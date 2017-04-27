---
title: Classe tuple | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- tuple
- std::tuple
- tuple/std::tuple
- tuple/std::tuple::operator=
dev_langs:
- C++
helpviewer_keywords:
- tuple class
ms.assetid: c38749be-ae4d-41f3-98ea-6aa3250de9a3
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: 5a06cb149bd08f733f2b43692747d33d81ab7a7b
ms.lasthandoff: 02/25/2017

---
# <a name="tuple-class"></a>Classe tupla
Encapsula uma sequência de comprimento fixo de elementos.  
  
## <a name="syntax"></a>Sintaxe  
```  
class tuple {  
public:  
   tuple();
   explicit tuple(P1, P2, ..., PN); // 0 < N  
   tuple(const tuple&);
   template <class U1, class U2, ..., class UN>  
      tuple(const tuple<U1, U2, ..., UN>&);
   template <class U1, class U2>  
      tuple(const pair<U1, U2>&); // N == 2  

   void swap(tuple& right);
   tuple& operator=(const tuple&);
   template <class U1, class U2, ..., class UN>  
      tuple& operator=(const tuple<U1, U2, ..., UN>&);
   template <class U1, class U2>  
      tuple& operator=(const pair<U1, U2>&); // N == 2  
   };  
  
#### Parameters  
 `TN`  
 The type of the Nth tuple element.  
  
## Remarks  
 The template class describes an object that stores N objects of types `T1`, `T2`, ..., `TN`, respectively, where where `0 <= N <= Nmax`. The extent of a tuple instance `tuple<T1, T2, ..., TN>` is the number `N` of its template arguments. The index of the template argument `Ti` and of the corresponding stored value of that type is `i - 1`. Thus, while we number the types from 1 to N in this documentation, the corresponding index values range from 0 to N - 1.  
  
## Example  
  
```cpp  
// tuple.cpp  
// compile with: /EHsc  
  
#include <vector>  
#include <iomanip>  
#include <iostream>  
#include <tuple>  
#include <string>  
  
using namespace std;  
  
typedef tuple <int, double, string> ids;  
  
void print_ids(const ids& i)  
{  
   cout << "( "  
        << get<0>(i) << ", "   
        << get<1>(i) << ", "   
        << get<2>(i) << " )." << endl;  
}  
  
int main( )  
{  
   // Using the constructor to declare and initialize a tuple  
   ids p1(10, 1.1e-2, "one");  
  
   // Compare using the helper function to declare and initialize a tuple  
   ids p2;  
   p2 = make_tuple(10, 2.22e-1, "two");  
  
   // Making a copy of a tuple  
   ids p3(p1);  
  
   cout.precision(3);  
   cout << "The tuple p1 is: ( ";  
   print_ids(p1);  
   cout << "The tuple p2 is: ( ";  
   print_ids(p2);  
   cout << "The tuple p3 is: ( ";  
   print_ids(p3);  
  
   vector<ids> v;  
  
   v.push_back(p1);  
   v.push_back(p2);  
   v.push_back(make_tuple(3, 3.3e-2, "three"));  
  
   cout << "The tuples in the vector are" << endl;  
   for(vector<ids>::const_iterator i = v.begin(); i != v.end(); ++i)  
   {  
      print_ids(*i);  
   }  
}  
```  
  
```Output  
The tuple p1 is: ( 10, 0.011, one ).  
The tuple p2 is: ( 10, 0.222, two ).  
The tuple p3 is: ( 10, 0.011, one ).  
The tuples in the vector are  
( 10, 0.011, one ).  
( 10, 0.222, two ).  
( 3, 0.033, three ).  
```  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<tuple>  
  
 **Namespace:** std  
  
##  <a name="a-nametupleoperatoreqa--tupleoperator"></a><a name="tuple__operator_eq"></a> tuple::operator=  
 Atribui um objeto `tuple`.  
  
```  
tuple& operator=(const tuple& right);

template <class U1, class U2, ..., class UN>  
   tuple& operator=(const tuple<U1, U2, ..., UN>& right);

template <class U1, class U2>  
   tuple& operator=(const pair<U1, U2>& right); // N == 2  

tuple& operator=(tuple&& right);
   
template <class U1, class U2>  
   tuple& operator=(pair<U1, U2>&& right);
```  
  
### <a name="parameters"></a>Parâmetros  
 `UN`  
 O tipo do enésimo elemento de tupla copiado.  
  
 `right`  
 A tupla da qual copiar.  
  
### <a name="remarks"></a>Comentários  
 Os primeiros dois operadores de membros atribuem os elementos de `right` aos elementos correspondentes de `*this`. O terceiro operador de membro atribui `right.first` para o elemento no índice 0 de `*this` e `right.second` para o elemento no índice 1. Todos os três operadores de membros retornam `*this`.  
  
 Os operadores de membro restantes são análogos aos anteriores, mas com o [Declarador de referência Rvalue: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// std__tuple__tuple_operator_as.cpp   
// compile with: /EHsc   
#include <tuple>   
#include <iostream>   
#include <utility>   
  
typedef std::tuple<int, double, int, double> Mytuple;   
int main()   
    {   
    Mytuple c0(0, 1, 2, 3);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
    Mytuple c1;   
    c1 = c0;   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c1);   
    std::cout << " " << std::get<1>(c1);   
    std::cout << " " << std::get<2>(c1);   
    std::cout << " " << std::get<3>(c1);   
    std::cout << std::endl;   
  
    std::tuple<char, int> c2;   
    c2 = std::make_pair('x', 4);   
  
// display contents " x 4"   
    std::cout << " " << std::get<0>(c2);   
    std::cout << " " << std::get<1>(c2);   
    std::cout << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
0 1 2 3  
0 1 2 3  
x 4  
```  
  
##  <a name="a-nametupleswapa--tupleswap"></a><a name="tuple_swap"></a> tuple:swap  
 Troca os elementos das duas tuplas.  
  
```  
template <class... Types>  
   void swap(tuple<Types...&> left, tuple<Types...&> right);
```  
  
### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`left`|Uma tupla cujos elementos serão trocados por aqueles da tupla `right`.|  
|`right`|Uma tupla cujos elementos serão trocados por aqueles da tupla `left`.|  
  
### <a name="remarks"></a>Comentários  
 A função executa `left.swap(right)`.  
  
##  <a name="a-nametupletuplea--tupletuple"></a><a name="tuple__tuple"></a> tuple::tuple  
 Constrói um objeto `tuple`.  
  
```  
constexpr tuple();
explicit constexpr tuple(const Types&...); 
template <class... UTypes>   
   explicit constexpr tuple(UTypes&&...);
  
tuple(const tuple&) = default;  
tuple(tuple&&) = default;  
  
template <class... UTypes>  
   constexpr tuple(const tuple<UTypes...>&);
template <class... UTypes>  
   constexpr tuple(tuple<UTypes...>&&);
  
// only if sizeof...(Types) == 2  
template <class U1, class U2>   
   constexpr tuple(const pair<U1, U2>&);
template <class U1, class U2>  
   constexpr tuple(pair<U1, U2>&&);
```  
  
### <a name="parameters"></a>Parâmetros  
 `UN`  
 O tipo do enésimo elemento de tupla copiado.  
  
 `right`  
 A tupla da qual copiar.  
  
### <a name="remarks"></a>Comentários  
 O primeiro construtor constrói um objeto cujos elementos são construídos por padrão.  
  
 O segundo construtor constrói um objeto cujos elementos são construídos de cópias dos argumentos `P1`, `P2`,..., `PN` com cada `Pi` inicializando o elemento no índice `i - 1`.  
  
 O terceiro e quarto construtores constroem um objeto cujos elementos são cópias criadas do elemento correspondente de `right`.  
  
 O quinto construtor constrói um objeto cujo elemento no índice 0 é cópia criada de `right.first` e cujo elemento no índice 1 é cópia criada de `right.second`.  
  
 Os construtores restantes são análogos aos anteriores, mas com o [Declarador de referência Rvalue: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
### <a name="example"></a>Exemplo  
  
```cpp  
// std__tuple__tuple_tuple.cpp   
// compile with: /EHsc   
#include <tuple>   
#include <iostream>   
#include <utility>   
  
typedef std::tuple<int, double, int, double> Mytuple;   
int main()   
    {   
    Mytuple c0(0, 1, 2, 3);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c0);   
    std::cout << " " << std::get<1>(c0);   
    std::cout << " " << std::get<2>(c0);   
    std::cout << " " << std::get<3>(c0);   
    std::cout << std::endl;   
  
    Mytuple c1;   
    c1 = c0;   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c1);   
    std::cout << " " << std::get<1>(c1);   
    std::cout << " " << std::get<2>(c1);   
    std::cout << " " << std::get<3>(c1);   
    std::cout << std::endl;   
  
    std::tuple<char, int> c2(std::make_pair('x', 4));   
  
// display contents " x 4"   
    std::cout << " " << std::get<0>(c2);   
    std::cout << " " << std::get<1>(c2);   
    std::cout << std::endl;   
  
    Mytuple c3(c0);   
  
// display contents " 0 1 2 3"   
    std::cout << " " << std::get<0>(c3);   
    std::cout << " " << std::get<1>(c3);   
    std::cout << " " << std::get<2>(c3);   
    std::cout << " " << std::get<3>(c3);   
    std::cout << std::endl;   
  
    typedef std::tuple<int, float, int, float> Mytuple2;   
    Mytuple c4(Mytuple2(4, 5, 6, 7));   
  
// display contents " 4 5 6 7"   
    std::cout << " " << std::get<0>(c4);   
    std::cout << " " << std::get<1>(c4);   
    std::cout << " " << std::get<2>(c4);   
    std::cout << " " << std::get<3>(c4);   
    std::cout << std::endl;   
  
    return (0);   
    }  
```  
  
```Output  
 0 1 2 3  
 0 1 2 3  
 x 4  
 0 1 2 3  
 4 5 6 7  
```  
  
## <a name="see-also"></a>Consulte também  
 [\<tuple>](../standard-library/tuple.md)   
 [Função make_tuple](../standard-library/tuple-functions.md#make_tuple_function)

