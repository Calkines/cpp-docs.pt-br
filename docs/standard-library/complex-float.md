---
title: complex&lt;float&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::complex<float>
- std.complex<float>
- complex<float>
dev_langs:
- C++
helpviewer_keywords:
- complex<float> function
ms.assetid: 1178eb1e-39bd-4017-89cd-aea95f813939
caps.latest.revision: 23
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: b3c76d33bcdf1e5882bd09b49c73dcef4d0474b3
ms.lasthandoff: 02/25/2017

---
# <a name="complexltfloatgt"></a>complex&lt;float&gt;
Descreve um objeto que armazena um par ordenado de objetos do tipo **float***,* o primeiro representando a parte real de um número complexo e o segundo representando a parte imaginária.  
  
## <a name="syntax"></a>Sintaxe  
  
```
template <>
class complex<float> {
public:
    constexpr complex(
    float _RealVal = 0,
    float _ImagVal = 0);

constexpr complex(
    const complex<float>& complexNum);

constexpr complex(
    const complex<double>& complexNum);

constexpr complex(
    const complex<long double>& complexNum);
// rest same as template class complex
};
```  
  
#### <a name="parameters"></a>Parâmetros  
 `_RealVal`  
 O valor do tipo **float** da parte real do número complexo que está sendo construído.  
  
 `_ImagVal`  
 O valor do tipo **float** da parte imaginária do número complexo que está sendo construído.  
  
 `complexNum`  
 O número complexo do tipo **double** ou do tipo `long double` cujas partes reais e imaginárias são usadas para inicializar um número complexo do tipo **float** que está sendo construído.  
  
## <a name="return-value"></a>Valor de retorno  
 Um número complexo do tipo **float**.  
  
## <a name="remarks"></a>Comentários  
 A especialização explícita da classe de modelo complexa para uma classe complexa do tipo **float** difere apenas da classe de modelo nos construtores que ela define. A conversão de **float** em **double** pode ser implícita, mas a conversão menos segura de **float** em `long double` precisa ser **explícita**. O uso de **explícito** exclui a iniciação com conversão de tipo usando a sintaxe de atribuição.  
  
 Para obter mais informações sobre a classe do modelo `complex`, consulte [Classe complexa](../standard-library/complex-class.md). Para obter uma lista de membros da classe do modelo `complex`, consulte.  
  
## <a name="example"></a>Exemplo  
  
```cpp  
// complex_comp_flt.cpp  
// compile with: /EHsc  
#include <complex>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;  
   double pi = 3.14159265359;  
  
   // The first constructor specifies real & imaginary parts  
   complex <float> c1 ( 4.0 , 5.0 );  
   cout << "Specifying initial real & imaginary parts,\n"  
        << " as type float gives c1 = " << c1 << endl;  
  
   // The second constructor initializes values of the real &  
   // imaginary parts using those of complex number of type double  
   complex <double> c2double ( 1.0 , 3.0 );  
   complex <float> c2float ( c2double );  
   cout << "Implicit conversion from type double to type float,"  
        << "\n gives c2float = " << c2float << endl;  
  
   // The third constructor initializes values of the real &  
   // imaginary parts using those of a complex number  
   // of type long double  
   complex <long double> c3longdouble ( 3.0 , 4.0 );  
   complex <float> c3float ( c3longdouble );  
   cout << "Explicit conversion from type long double to type float,"  
        << "\n gives c3float = " << c3float << endl;  
  
   // The modulus and argument of a complex number can be recovered  
   double absc3 = abs ( c3float);  
   double argc3 = arg ( c3float);  
   cout << "The modulus of c3 is recovered from c3 using: abs ( c3 ) = "  
        << absc3 << endl;  
   cout << "Argument of c3 is recovered from c3 using:\n arg ( c3 ) = "  
        << argc3 << " radians, which is " << argc3 * 180 / pi  
        << " degrees." << endl;  
}  
\* Output:   
Specifying initial real & imaginary parts,  
 as type float gives c1 = (4,5)  
Implicit conversion from type double to type float,  
 gives c2float = (1,3)  
Explicit conversion from type long double to type float,  
 gives c3float = (3,4)  
The modulus of c3 is recovered from c3 using: abs ( c3 ) = 5  
Argument of c3 is recovered from c3 using:  
 arg ( c3 ) = 0.927295 radians, which is 53.1301 degrees.  
*\  
```  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho**: \<complexo>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>Consulte também  
 [Classe complex](../standard-library/complex-class.md)   
 [Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



