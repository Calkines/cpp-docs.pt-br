---
title: Classe binder1st
ms.date: 02/21/2019
f1_keywords:
- functional/std::binder1st
helpviewer_keywords:
- binder1st class
ms.assetid: 6b8ee343-c82f-48f8-867d-06f9d1d324c0
ms.openlocfilehash: 384a870a10c9f806684443d8c67647e924b6b2aa
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243379"
---
# <a name="binder1st-class"></a>Classe binder1st

Uma classe de modelo que fornece um construtor que converte um objeto de função binária em um objeto de função unária, associando o primeiro argumento da função binária a um valor especificado. Preterido no c++11 em favor da [associar](functional-functions.md#bind)e removidos em c++17.

## <a name="syntax"></a>Sintaxe

```cpp
template <class Operation>
class binder1st
    : public unaryFunction <typename Operation::second_argument_type,
                             typename Operation::result_type>
{
public:
    typedef typename Operation::argument_type argument_type;
    typedef typename Operation::result_type result_type;
    binder1st(
        const Operation& binary_fn,
        const typename Operation::first_argument_type& left);

    result_type operator()(const argument_type& right) const;
    result_type operator()(const argument_type& right) const;

protected:
    Operation op;
    typename Operation::first_argument_type value;
};
```

### <a name="parameters"></a>Parâmetros

*binary_fn*\
O objeto de função binária a ser convertido em um objeto de função unária.

*À esquerda*\
O valor ao qual o primeiro argumento do objeto de função binária deve ser associado.

*Certo*\
O valor do argumento que o objeto binário adaptado compara ao valor fixo do segundo argumento.

## <a name="return-value"></a>Valor de retorno

O objeto de função unária que resulta da associação o primeiro argumento do objeto de função binária ao valor *esquerdo*.

## <a name="remarks"></a>Comentários

A classe de modelo armazena uma cópia de um objeto de função binária *binary_fn* na `op`e uma cópia de *esquerdo* em `value`. Ela define sua função de membro `operator()` como retornando `op(value, right)`.

Se *binary_fn* é um objeto do tipo `Operation` e `c` é uma constante, então `bind1st(binary_fn, c)` é um equivalente mais conveniente para `binder1st<Operation>(binary_fn, c)`. Para obter mais informações, consulte [bind1st](../standard-library/functional-functions.md#bind1st).

## <a name="example"></a>Exemplo

```cpp
// functional_binder1st.cpp
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
        binder1st<less<int> >(less<int>(), 10));
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;

    // Compare use of binder2nd fixing 2nd argument:
    // count the number of integers < 10 in the vector
    vector<int>::iterator::difference_type result2;
    result2 = count_if(v1.begin(), v1.end(),
        binder2nd<less<int> >(less<int>(), 10));
    cout << "The number of elements in v1 less than 10 is: "
         << result2 << "." << endl;
}
```

```Output
The vector v1 = ( 0 5 10 15 20 25 )
The number of elements in v1 greater than 10 is: 3.
The number of elements in v1 less than 10 is: 2.
```
