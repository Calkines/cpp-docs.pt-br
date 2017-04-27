---
title: Classe subtract_with_carry_engine | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- subtract_with_carry_engine
- random/std::subtract_with_carry_engine
- random/std::subtract_with_carry_engine::default_seed
- random/std::subtract_with_carry_engine::discard
- random/std::subtract_with_carry_engine::min
- random/std::subtract_with_carry_engine::max
- random/std::subtract_with_carry_engine::seed
dev_langs:
- C++
helpviewer_keywords:
- subtract_with_carry_engine class
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
caps.latest.revision: 20
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
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: 3bfa6cd48bad52958dbc0f9563e46f11bf516d39
ms.lasthandoff: 02/25/2017

---
# <a name="subtractwithcarryengine-class"></a>Classe subtract_with_carry_engine
Gera uma sequência aleatória usando o algoritmo de subtração com transferência (Fibonacci com retardo).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
template <class UIntType, size_t W, size_t S, size_t R>  
class subtract_with_carry_engine;  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `UIntType`  
 O tipo de resultado inteiro sem sinal. Para ver os tipos possíveis, consulte [\<random>](../standard-library/random.md).  
  
 `W`  
 **Tamanho da palavra**. Tamanho de cada palavra da sequência de estado, em bits. **Pré-condição**: `0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `S`  
 **Curto retardo**. Número de valores inteiros. **Pré-condição**: `0 < S < R`  
  
 `R`  
 **Longo retardo**. Determina a recorrência na série gerada.  
  
## <a name="members"></a>Membros  
  
||||  
|-|-|-|  
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|  
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|  
|`default_seed` é um membro constante, definido como `19780503u`, usado como valor padrão do parâmetro `subtract_with_carry_engine::seed` e construtor de valor único.|||  
  
 Para obter mais informações sobre membros do mecanismo, consulte [\<random>](../standard-library/random.md).  
  
## <a name="remarks"></a>Comentários  
 A classe de modelo `substract_with_carry_engine` é uma melhoria em relação a [linear_congruential_engine](../standard-library/linear-congruential-engine-class.md). Nenhum desses mecanismos é tão rápido nem apresenta resultados de qualidade tão altos quanto o [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md).  
  
 Esse mecanismo produz valores de um tipo integral sem sinal especificado pelo usuário usando a relação de recorrência (*ponto final*) `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M`, em que `cy(i)` terá o valor `1` se `x(i - S) - x(i - R) - cy(i - 1) < 0`; caso contrário, `0` e `M` terão o valor `2`<sup>W</sup>. O estado do mecanismo é um indicador de transferência mais `R` valores. Esses valores são formados pelos últimos valores `R` retornados se `operator()` tiver sido chamado pelo menos `R` vezes; caso contrário, são formados pelos valores `N` que foram retornados e os últimos valores de `R - N` da semente.  
  
 O argumento de modelo `UIntType` deve ser grande o suficiente para manter valores até `M - 1`.  
  
 Embora seja possível construir um gerador diretamente com base nesse mecanismo, também é possível usar um dos typedefs predefinidos:  
  
 `ranlux24_base`: usado como base para `ranlux24`.                   
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`  
  
 `ranlux48_base`: usado como base para `ranlux48`.                   
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`  
  
 Para obter informações detalhadas sobre o algoritmo de mecanismo de subtração com transferência, consulte o artigo da Wikipédia [Lagged Fibonacci generator](http://go.microsoft.com/fwlink/LinkId=402445) (Gerador de retardamento de Fibonacci).  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<random>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>Consulte também  
 [\<random>](../standard-library/random.md)

