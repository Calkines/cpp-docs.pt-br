---
title: Classe linear_congruential_engine | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- linear_congruential_engine
- random/std::linear_congruential_engine
dev_langs:
- C++
helpviewer_keywords:
- linear_congruential_engine class
ms.assetid: 30e00ca6-1933-4701-9561-54f3e810a5a1
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: 0c2d3fb09db9b8f1bf1daca935fac34afd2c6ecb
ms.lasthandoff: 02/25/2017

---
# <a name="linearcongruentialengine-class"></a>Classe linear_congruential_engine
Gera uma sequência aleatória pelo algoritmo congruente linear.  
  
## <a name="syntax"></a>Sintaxe  
```  
class linear_congruential_engine{  
   public:  // types  
   typedef UIntType result_type;  
   // engine characteristics  
   static constexpr result_type multiplier = a;  
   static constexpr result_type increment = c;  
   static constexpr result_type modulus = m;  
   static constexpr result_type min() { return c == 0u  1u: 0u; }  
   static constexpr result_type max() { return m - 1u; }  
   static constexpr result_type default_seed = 1u;  
   // constructors and seeding functions  
   explicit linear_congruential_engine(result_type s = default_seed);
   template <class Sseq>  
   explicit linear_congruential_engine(Sseq& q);
   void seed(result_type s = default_seed);
   template <class Sseq>  
   void seed(Sseq& q);
   // generating functions  
   result_type operator()();
   void discard(unsigned long long z);
   };  
```  
#### <a name="parameters"></a>Parâmetros  
 `UIntType`  
 O tipo de resultado inteiro sem sinal. Para ver os tipos possíveis, consulte [\<random>](../standard-library/random.md).  
  
 `A`  
 **Multiplicador**. **Pré-condição**: consulte a seção Comentários.  
  
 `C`  
 **Incremento**. **Pré-condição**: consulte a seção Comentários.  
  
 `M`  
 **Módulo**. **Pré-condição**: consulte os comentários.  
  
## <a name="members"></a>Membros  
  
||||  
|-|-|-|  
|`linear_congruential_engine::linear_congruential_engine`|`linear_congruential_engine::min`|`linear_congruential_engine::discard`|  
|`linear_congruential_engine::operator()`|`linear_congruential_engine::max`|`linear_congruential_engine::seed`|  
  
 `default_seed` é um membro constante, definido como `1u`, usado como valor padrão do parâmetro `linear_congruential_engine::seed` e construtor de valor único.  
  
 Para obter mais informações sobre membros do mecanismo, consulte [\<random>](../standard-library/random.md).  
  
## <a name="remarks"></a>Comentários  
 A classe de modelo `linear_congruential_engine` é o mecanismo gerador mais simples, mas não o mais rápido nem de maior qualidade. Uma melhoria em relação a esse mecanismo é o [substract_with_carry_engine](../standard-library/subtract-with-carry-engine-class.md). Nenhum desses mecanismos é tão rápido nem tem resultados de qualidade tão altos quanto o [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md).  
  
 Esse mecanismo produz valores de um tipo integral não assinado especificado pelo usuário usando a relação de recorrência (*ponto final*) `x(i) = (A * x(i-1) + C) mod M`.  
  
 Se `M` for igual a zero, o valor usado para essa operação de módulo é `numeric_limits<result_type>::max() + 1`. O estado do mecanismo é o último valor retornado ou o valor semente, se nenhuma chamada tiver sido feita a `operator()`.  
  
 Se `M` for diferente de zero, os valores dos argumentos de modelo `A` e `C` devem ser inferiores a `M`.  
  
 Embora seja possível construir um gerador diretamente desse mecanismo, também é possível usar um dos typedefs predefinidos.  
  
 `minstd_rand0`: mecanismo padrão mínimo de 1988 (Lewis, Goodman e Miller, 1969).  
  
```  
typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;  
```  
  
 `minstd_rand`: mecanismo padrão mínimo atualizado `minstd_rand0` (Park, Miller e Stockmeyer, 1993).  
  
```  
typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;  
```  
  
 Para obter informações detalhadas sobre o algoritmo de mecanismo congruente linear, consulte o artigo da Wikipédia [Geradores congruentes lineares](http://go.microsoft.com/fwlink/LinkId=402446).  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<random>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>Consulte também  
 [\<random>](../standard-library/random.md)


