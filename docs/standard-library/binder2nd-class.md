---
title: Classe binder2nd | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.binder2nd
- binder2nd
- xfunctional/std::binder2nd
- std::binder2nd
dev_langs:
- C++
helpviewer_keywords:
- binder2nd class
ms.assetid: b2a9c1d1-dfc4-4ca9-a10e-ae84e195a62d
caps.latest.revision: 22
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
ms.sourcegitcommit: 85c900f2263ae1c1089478badc85388e3b5e8548
ms.openlocfilehash: f19b476ae903c915d4231621c39a88bf70b08685
ms.lasthandoff: 02/25/2017

---
# <a name="binder2nd-class"></a>Classe binder2nd
Uma classe de modelo que fornece um construtor que converte um objeto de função binária em um objeto de função unária associando o segundo argumento da função binária a um valor especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```
template <class Operation>
class binder2nd
    : public unaryFunction <typename Operation::first_argument_type,
    typename Operation::result_type>
{
public:
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder2nd(
        const Operation& Func,
        const typename Operation::second_argument_type& right);

    result_type operator()(const argument_type& left) const;
    result_type operator()(argument_type& left) const;

protected:
    Operation op;
    typename Operation::second_argument_type value;
};
```  
  
#### <a name="parameters"></a>Parâmetros  
 `Func`  
 O objeto de função binária a ser convertido em um objeto de função unária.  
  
 `right`  
 O valor ao qual o segundo argumento do objeto de função binária deve ser associado.  
  
 `left`  
 O valor do argumento que o objeto binário adaptado compara ao valor fixo do segundo argumento.  
  
## <a name="return-value"></a>Valor de retorno  
 O objeto de função unária que resulta da associação do segundo argumento do objeto de função binária ao valor `right.`  
  
## <a name="remarks"></a>Comentários  
 A classe de modelo armazena uma cópia de um objeto de função binária _*Func* em **op** e uma cópia de `right` em **value**. Define sua função membro `operator()` como **op**( `left`, **value**) de retorno.  
  
 Se `Func` for um objeto do tipo **Operation** e c for uma constante, [bind2nd](../standard-library/functional-functions.md#bind2nd_function) (`Func`, `c`) será equivalente ao construtor `binder2nd`\< **Operation**> ( `Func`, `c`) da classe `binder2nd` e será mais conveniente.  
  
## <a name="example"></a>Exemplo  
  
```cpp  
// functional_binder2nd.cpp  
// compile with: /EHsc  
#include <vector>  
#include <functional>  
#include <algorithm>  
#include <iostream>  
  
using namespace std;  
  
int main()  
{  
    vector<int> v1;  
    vector<int>::iterator Iter;  
  
    int i;  
    for (i = 0; i <= 5; i++)  
    {  
        v1.push_back(5 * i);  
    }  
  
    cout << "The vector v1 = ( ";  
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)  
        cout << *Iter << " ";  
    cout << ")" << endl;  
  
    // Count the number of integers > 10 in the vector  
    vector<int>::iterator::difference_type result1;  
    result1 = count_if(v1.begin(), v1.end(),  
        binder2nd<greater<int> >(greater<int>(), 10));  
    cout << "The number of elements in v1 greater than 10 is: "  
         << result1 << "." << endl;  
  
    // Compare using binder1st fixing 1st argument:  
    // count the number of integers < 10 in the vector  
    vector<int>::iterator::difference_type result2;  
    result2 = count_if(v1.begin(), v1.end(),  
        binder1st<greater<int> >(greater<int>(), 10));  
    cout << "The number of elements in v1 less than 10 is: "  
         << result2 << "." << endl;  
}  
/* Output:  
The vector v1 = ( 0 5 10 15 20 25 )  
The number of elements in v1 greater than 10 is: 3.  
The number of elements in v1 less than 10 is: 2.  
*/  
```  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<functional>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>Consulte também  
 [Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Referência da biblioteca padrão C++](../standard-library/cpp-standard-library-reference.md)



