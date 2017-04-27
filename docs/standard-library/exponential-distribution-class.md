---
title: Classe exponential_distribution | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- exponential_distribution
- std::exponential_distribution
- random/std::exponential_distribution
- std::exponential_distribution::reset
- random/std::exponential_distribution::reset
- std::exponential_distribution::lambda
- random/std::exponential_distribution::lambda
- std::exponential_distribution::param
- random/std::exponential_distribution::param
- std::exponential_distribution::min
- random/std::exponential_distribution::min
- std::exponential_distribution::max
- random/std::exponential_distribution::max
- std::exponential_distribution::operator()
- random/std::exponential_distribution::operator()
- std::exponential_distribution::param_type
- random/std::exponential_distribution::param_type
- std::exponential_distribution::param_type::lambda
- random/std::exponential_distribution::param_type::lambda
- std::exponential_distribution::param_type::operator==
- random/std::exponential_distribution::param_type::operator==
- std::exponential_distribution::param_type::operator!=
- random/std::exponential_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- exponential_distribution class
ms.assetid: d54f3126-a09b-45f9-a30b-0d94d03bcdc9
caps.latest.revision: 18
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
ms.sourcegitcommit: c7f3b346bc8abeab0c6bd913fc0b554bef4ed208
ms.openlocfilehash: 6681447dd9e5dda7515d04b4bdedfd9de9c62983
ms.lasthandoff: 02/25/2017

---
# <a name="exponentialdistribution-class"></a>Classe exponential_distribution
Gera uma distribuição exponencial.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
template<class RealType = double>
class exponential_distribution  
   {  
public:  
   // types  
   typedef RealType result_type;  
   struct param_type;  
   
   // constructors and reset functions  
   explicit exponential_distribution(result_type lambda = 1.0);
   explicit exponential_distribution(const param_type& parm);
   void reset();
   
   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
   result_type operator()(URNG& gen, const param_type& parm);
   
   // property functions  
   result_type lambda() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };  
``` 
### <a name="parameters"></a>Parâmetros  
*RealType*  
O tipo de resultado de ponto flutuante assume `double` como padrão. Para ver os tipos possíveis, consulte [\<random>](../standard-library/random.md).  
  
*URNG* O mecanismo gerador de números aleatórios. Para ver os tipos possíveis, consulte [\<random>](../standard-library/random.md).
  
  
## <a name="remarks"></a>Comentários  
 A classe do modelo descreve uma distribuição que produz valores de um tipo integral especificado pelo usuário ou o tipo `double` se nenhum for fornecido, distribuído de acordo com a Distribuição Exponencial. A tabela a seguir contém links para artigos sobre cada um dos membros.  
  
||||  
|-|-|-|  
|[exponential_distribution::exponential_distribution](#exponential_distribution__exponential_distribution)|`exponential_distribution::lambda`|`exponential_distribution::param`|  
|`exponential_distribution::operator()`||[exponential_distribution::param_type](#exponential_distribution__param_type)|  
  
A função membro de propriedade `lambda()` retorna o valor para o parâmetro de distribuição armazenado `lambda`.  
  
A função membro da propriedade `param()` define ou retorna o pacote de parâmetro de distribuição armazenado `param_type`.  
  
Para obter mais informações sobre as classes de distribuição e seus membros, consulte [\<random>](../standard-library/random.md).  
  
Para obter informações detalhadas sobre a distribuição exponencial, consulte o artigo de Wolfram MathWorld [Distribuição exponencial](http://go.microsoft.com/fwlink/LinkId=401098).  
  
## <a name="example"></a>Exemplo  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double l, const int s) {  
  
    // uncomment to use a non-deterministic generator  
    //    std::random_device gen;  
    std::mt19937 gen(1701);  
  
    std::exponential_distribution<> distr(l);  
  
    std::cout << std::endl;  
    std::cout << "min() == " << distr.min() << std::endl;  
    std::cout << "max() == " << distr.max() << std::endl;  
    std::cout << "lambda() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.lambda() << std::endl;  
  
    // generate the distribution as a histogram  
    std::map<double, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    std::cout << "Distribution for " << s << " samples:" << std::endl;  
    int counter = 0;  
    for (const auto& elem : histogram) {  
        std::cout << std::fixed << std::setw(11) << ++counter << ": "  
            << std::setw(14) << std::setprecision(10) << elem.first << std::endl;  
    }  
    std::cout << std::endl;  
}  
  
int main()  
{  
    double l_dist = 0.5;  
    int samples = 10;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the 'lambda' distribution parameter (must be greater than zero): ";  
    std::cin >> l_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(l_dist, samples);  
}  
  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'lambda' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == 0  
max() == 1.79769e+308  
lambda() == 1.0000000000  
Distribution for 10 samples:  
    1: 0.0936880533  
    2: 0.1225944894  
    3: 0.6443593183  
    4: 0.6551171649  
    5: 0.7313457551  
    6: 0.7313557977  
    7: 0.7590097389  
    8: 1.4466885214  
    9: 1.6434088411  
    10: 2.1201210996  
```  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<random>  
  
 **Namespace:** std  
  
##  <a name="a-nameexponentialdistributionexponentialdistributiona--exponentialdistributionexponentialdistribution"></a><a name="exponential_distribution__exponential_distribution"></a>  exponential_distribution::exponential_distribution  
 Constrói a distribuição.  
  
```  
explicit exponential_distribution(result_type lambda = 1.0);
explicit exponential_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Parâmetros  
*lambda*  
 O parâmetro de distribuição `lambda`.  
  
*parm*  
 O pacote de parâmetro usado para construir a distribuição.  
  
### <a name="remarks"></a>Comentários  
**Pré-condição:** `0.0 < lambda`  
  
O primeiro construtor constrói um objeto cujo valor `lambda` armazenado contém o valor *lambda*.  
  
O segundo construtor cria um objeto cujos parâmetros armazenados são inicializados de *parm*. Você pode chamar a função de membro `param()` para obter e definir os parâmetros atuais de uma distribuição existente.  
  
##  <a name="a-nameexponentialdistributionparamtypea--exponentialdistributionparamtype"></a><a name="exponential_distribution__param_type"></a>  exponential_distribution::param_type  
Armazena os parâmetros da distribuição.  
  
```
struct param_type {  
   typedef exponential_distribution<result_type> distribution_type;  
   param_type(result_type lambda = 1.0);
   result_type lambda() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };
```  
  
### <a name="parameters"></a>Parâmetros  
*lambda*  
O parâmetro de distribuição `lambda`.  
  
*right*  
O objeto `param_type` a ser comparado a este.  
  
### <a name="remarks"></a>Comentários  
**Pré-condição:** `0.0 < lambda`  
  
Essa estrutura pode ser enviada ao construtor de classe de distribuição na instanciação, para a função de membro `param()` para definir os parâmetros armazenados de uma distribuição existente e para `operator()` a ser usado no lugar dos parâmetros armazenados.  
  
## <a name="see-also"></a>Consulte também  
[\<random>](../standard-library/random.md)

