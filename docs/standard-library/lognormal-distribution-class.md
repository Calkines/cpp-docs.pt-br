---
title: Classe lognormal_distribution | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- lognormal_distribution
- std::lognormal_distribution
- random/std::lognormal_distribution
- std::lognormal_distribution::reset
- random/std::lognormal_distribution::reset
- std::lognormal_distribution::m
- random/std::lognormal_distribution::m
- std::lognormal_distribution::s
- random/std::lognormal_distribution::s
- std::lognormal_distribution::param
- random/std::lognormal_distribution::param
- std::lognormal_distribution::min
- random/std::lognormal_distribution::min
- std::lognormal_distribution::max
- random/std::lognormal_distribution::max
- std::lognormal_distribution::operator()
- random/std::lognormal_distribution::operator()
- std::lognormal_distribution::param_type
- random/std::lognormal_distribution::param_type
- std::lognormal_distribution::param_type::m
- random/std::lognormal_distribution::param_type::m
- std::lognormal_distribution::param_type::s
- random/std::lognormal_distribution::param_type::s
- std::lognormal_distribution::param_type::operator==
- random/std::lognormal_distribution::param_type::operator==
- std::lognormal_distribution::param_type::operator!=
- random/std::lognormal_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- lognormal_distribution class
ms.assetid: f2d6a431-6c3a-4370-b12e-4adb4ddf6cc4
caps.latest.revision: 15
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
ms.sourcegitcommit: 28baed4badda4f2c1d7e5b20235fe8d40c2a7195
ms.openlocfilehash: 9e3e74b396e0f5026cc69c6cf4e2ca7cf5215ad5
ms.lasthandoff: 02/25/2017

---
# <a name="lognormaldistribution-class"></a>Classe lognormal_distribution
Gera uma distribuição normal de log.  
  
## <a name="syntax"></a>Sintaxe  
```  
template <class RealType = double>  
class lognormal_distribution  
   {  
public:  
   // types  
   typedef RealType result_type;  
   struct param_type;  
   // constructor and reset functions  
   explicit lognormal_distribution(result_type m = 0.0, result_type s = 1.0);
   explicit lognormal_distribution(const param_type& parm);
   void reset();
   // generating functions  
   template <class URNG>  
   result_type operator()(URNG& gen);
   template <class URNG>  
   result_type operator()(URNG& gen, const param_type& parm);
   // property functions  
   result_type m() const;
   result_type s() const;
   param_type param() const;
   void param(const param_type& parm);
   result_type min() const;
   result_type max() const;
   };  
```  
### <a name="parameters"></a>Parâmetros  
*RealType*  
O tipo de resultado de ponto flutuante assume `double` como padrão. Para ver os tipos possíveis, consulte [\<random>](../standard-library/random.md).  
  
## <a name="remarks"></a>Comentários  
A classe do modelo descreve uma distribuição que produz valores de um tipo integral especificado pelo usuário ou o tipo `double` se nenhum for fornecido, distribuído de acordo com a Distribuição Normal de Log. A tabela a seguir contém links para artigos sobre cada um dos membros.  
  
||||  
|-|-|-|  
|[lognormal_distribution::lognormal_distribution](#lognormal_distribution__lognormal_distribution)|`lognormal_distribution::m`|`lognormal_distribution::param`|  
|`lognormal_distribution::operator()`|`lognormal_distribution::s`|[lognormal_distribution::param_type](#lognormal_distribution__param_type)|  
  
As funções de propriedade `m()` e `s()` retornam os valores para os parâmetros de distribuição armazenados *m* e *s*, respectivamente.  
  
O membro da propriedade `param()` define ou retorna o pacote de parâmetros de distribuição armazenado `param_type`.  

As funções membro `min()` e `max()` retornam o menor resultado possível e o maior resultado possível, respectivamente.  
  
A função membro `reset()` descarta qualquer valor armazenado em cache, de forma que o resultado da próxima chamada para `operator()` não dependerá dos valores obtidos do mecanismo antes da chamada.  
  
As funções membro `operator()` retornam o próximo valor gerado com base no mecanismo URNG, do pacote de parâmetros atual ou do pacote de parâmetros especificado.
  
Para obter mais informações sobre as classes de distribuição e seus membros, consulte [\<random>](../standard-library/random.md).  
  
Para obter informações detalhadas sobre a distribuição LogNormal, consulte o artigo [Distribuição LogNormal](http://go.microsoft.com/fwlink/LinkId=400917), da Wolfram MathWorld.  
  
## <a name="example"></a>Exemplo  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
using namespace std;  
  
void test(const double m, const double s, const int samples) {  
  
    // uncomment to use a non-deterministic seed  
    //    random_device gen;  
    //    mt19937 gen(rd());  
    mt19937 gen(1701);  
  
    lognormal_distribution<> distr(m, s);  
  
    cout << endl;  
    cout << "min() == " << distr.min() << endl;  
    cout << "max() == " << distr.max() << endl;  
    cout << "m() == " << fixed << setw(11) << setprecision(10) << distr.m() << endl;  
    cout << "s() == " << fixed << setw(11) << setprecision(10) << distr.s() << endl;  
  
    // generate the distribution as a histogram  
    map<double, int> histogram;  
    for (int i = 0; i < samples; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    cout << "Distribution for " << samples << " samples:" << endl;  
    int counter = 0;  
    for (const auto& elem : histogram) {  
        cout << fixed << setw(11) << ++counter << ": "  
            << setw(14) << setprecision(10) << elem.first << endl;  
    }  
    cout << endl;  
}  
  
int main()  
{  
    double m_dist = 1;  
    double s_dist = 1;  
    int samples = 10;  
  
    cout << "Use CTRL-Z to bypass data entry and run using default values." << endl;  
    cout << "Enter a floating point value for the 'm' distribution parameter: ";  
    cin >> m_dist;  
    cout << "Enter a floating point value for the 's' distribution parameter (must be greater than zero): ";  
    cin >> s_dist;  
    cout << "Enter an integer value for the sample count: ";  
    cin >> samples;  
  
    test(m_dist, s_dist, samples);  
}  
```  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'm' distribution parameter: 0  
Enter a floating point value for the 's' distribution parameter (must be greater than zero): 1  
Enter an integer value for the sample count: 10  
 
min() == -1.79769e+308  
max() == 1.79769e+308  
m() == 0.0000000000  
s() == 1.0000000000  
Distribution for 10 samples:  
    1: 0.3862809339  
    2: 0.4128865601  
    3: 0.4490576787  
    4: 0.4862035428  
    5: 0.5930607126  
    6: 0.8190778771  
    7: 0.8902379317  
    8: 2.8332911667  
    9: 5.1359445565  
    10: 5.4406507912  
```  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<random>  
  
 **Namespace:** std  
  
##  <a name="a-namelognormaldistributionlognormaldistributiona--lognormaldistributionlognormaldistribution"></a><a name="lognormal_distribution__lognormal_distribution"></a>  lognormal_distribution::lognormal_distribution  
 Constrói a distribuição.  
  
```  
explicit lognormal_distribution(RealType m = 0.0, RealType s = 1.0);
explicit lognormal_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Parâmetros  
*m*  
O parâmetro de distribuição `m`.  
  
*s*  
O parâmetro de distribuição `s`.  
  
*parm*  
A estrutura `param_type` usada para construir a distribuição.  
  
### <a name="remarks"></a>Comentários  
**Pré-condição:** `0.0 < s`  
  
O primeiro construtor constrói um objeto cujo valor `m` armazenado contém o valor *m* e cujo valor armazenado `s` contém o valor *s*.  
  
O segundo construtor cria um objeto cujos parâmetros armazenados são inicializados de *parm*. Você pode chamar a função de membro `param()` para obter e definir os parâmetros atuais de uma distribuição existente.  
  
##  <a name="a-namelognormaldistributionparamtypea--lognormaldistributionparamtype"></a><a name="lognormal_distribution__param_type"></a>  lognormal_distribution::param_type  
Armazena os parâmetros da distribuição.  
  
```  
struct param_type {  
   typedef lognormal_distribution<result_type> distribution_type;  
   param_type(result_type m = 0.0, result_type s = 1.0);
   result_type m() const;
   result_type s() const;

   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
};  
```    
### <a name="parameters"></a>Parâmetros  
*m*  
O parâmetro de distribuição `m`.  
  
*s*  
O parâmetro de distribuição `s`.  
  
*right*  
A estrutura `param_type` usada para comparar.  
  
### <a name="remarks"></a>Comentários  
**Pré-condição:** `0.0 < s`  
  
Essa estrutura pode ser enviada ao construtor de classe de distribuição na instanciação, para a função de membro `param()` para definir os parâmetros armazenados de uma distribuição existente e para `operator()` a ser usado no lugar dos parâmetros armazenados.  
  
## <a name="see-also"></a>Consulte também  
[\<random>](../standard-library/random.md)

