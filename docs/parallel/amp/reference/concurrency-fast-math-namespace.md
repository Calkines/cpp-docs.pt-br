---
title: 'Namespace Concurrency:: fast_math | Documentos do Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_math/Concurrency::fast_math
dev_langs:
- C++
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: d8a94b0911b772f4972416722757bec24a4826ed
ms.lasthandoff: 03/17/2017

---
# <a name="concurrencyfastmath-namespace"></a>Namespace Concurrency::fast_math
Funções no `fast_math` namespace tiver menos precisão, só preciso de suporte (`float`) e chamar os intrínsecos do DirectX. Há duas versões de cada função, por exemplo `cos` e `cosf`. Ambas as versões levar e retornar um `float`, mas cada chama o DirectX mesmo intrínseco.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
namespace fast_math;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="functions"></a>Funções  
  
|Nome|Descrição|  
|----------|-----------------|  
|[cos](concurrency-fast-math-namespace-functions.md#cos)|Calcula o arco cosseno do argumento|  
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|Calcula o arco cosseno do argumento|  
|[asin](concurrency-fast-math-namespace-functions.md#asin)|Calcula o arco seno do argumento|  
|[asinf](concurrency-fast-math-namespace-functions.md#asinf)|Calcula o arco seno do argumento|  
|[atan](concurrency-fast-math-namespace-functions.md#atan)|Calcula o arco tangente do argumento|  
|[atan2](concurrency-fast-math-namespace-functions.md#atan2)|Calcula o arco tangente de y/x|  
|[atan2f](concurrency-fast-math-namespace-functions.md#atan2f)|Calcula o arco tangente de y/x|  
|[atanf](concurrency-fast-math-namespace-functions.md#atanf)|Calcula o arco tangente do argumento|  
|[ceil](concurrency-fast-math-namespace-functions.md#ceil)|Calcula o teto do argumento|  
|[ceilf](concurrency-fast-math-namespace-functions.md#ceilf)|Calcula o teto do argumento|  
|[cos](concurrency-fast-math-namespace-functions.md#cos)|Calcula o cosseno do argumento|  
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|Calcula o cosseno do argumento|  
|[cosh](concurrency-fast-math-namespace-functions.md#cosh)|Calcula o valor cosseno hiperbólico do argumento|  
|[coshf](concurrency-fast-math-namespace-functions.md#coshf)|Calcula o valor cosseno hiperbólico do argumento|  
|[exp](concurrency-fast-math-namespace-functions.md#exp)|Calcula a exponencial do argumento de base-e|  
|[exp2](concurrency-fast-math-namespace-functions.md#exp2)|Calcula o exponencial do argumento de base-2|  
|[exp2f](concurrency-fast-math-namespace-functions.md#exp2f)|Calcula o exponencial do argumento de base-2|  
|[expf](concurrency-fast-math-namespace-functions.md#expf)|Calcula a exponencial do argumento de base-e|  
|[fabs](concurrency-fast-math-namespace-functions.md#fabs)|Retorna o valor absoluto do argumento|  
|[fabsf](concurrency-fast-math-namespace-functions.md#fabsf)|Retorna o valor absoluto do argumento|  
|[floor](concurrency-fast-math-namespace-functions.md#floor)|Calcula a base do argumento|  
|[floorf](concurrency-fast-math-namespace-functions.md#floorf)|Calcula a base do argumento|  
|[fmax](concurrency-fast-math-namespace-functions.md#fmax)|Determinar o valor numérico máximo dos argumentos|  
|[fmaxf](concurrency-fast-math-namespace-functions.md#fmaxf)|Determinar o valor numérico máximo dos argumentos|  
|[fmin](concurrency-fast-math-namespace-functions.md#fmin)|Determinar o valor numérico mínimo dos argumentos|  
|[fminf](concurrency-fast-math-namespace-functions.md#fminf)|Determinar o valor numérico mínimo dos argumentos|  
|[fmod](concurrency-fast-math-namespace-functions.md#fmod)|Calcula o restante de ponto flutuante de x/y|  
|[fmodf](concurrency-fast-math-namespace-functions.md#fmodf)|Calcula o restante de ponto flutuante de x/y|  
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|Obtém a mantissa e expoente de x|  
|[frexpf](concurrency-fast-math-namespace-functions.md#frexpf)|Obtém a mantissa e expoente de x|  
|[isfinite](concurrency-fast-math-namespace-functions.md#isfinite)|Determina se o argumento tem um valor finito|  
|[isinf](concurrency-fast-math-namespace-functions.md#isinf)|Determina se o argumento for um infinito|  
|[isnan](concurrency-fast-math-namespace-functions.md#isnan)|Determina se o argumento é um NaN|  
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|Calcula um número real de mantissa e expoente|  
|[ldexpf](concurrency-fast-math-namespace-functions.md#ldexpf)|Calcula um número real de mantissa e expoente|  
|[log](concurrency-fast-math-namespace-functions.md#log)|Calcula o logaritmo de base e do argumento|  
|[log10](concurrency-fast-math-namespace-functions.md#log10)|Calcula o logaritmo de base&10; do argumento|  
|[log10f](concurrency-fast-math-namespace-functions.md#log10f)|Calcula o logaritmo de base&10; do argumento|  
|[log2](concurrency-fast-math-namespace-functions.md#log2)|Calcula o logaritmo de base&2; do argumento|  
|[log2f](concurrency-fast-math-namespace-functions.md#log2f)|Calcula o logaritmo de base&2; do argumento|  
|[logf](concurrency-fast-math-namespace-functions.md#logf)|Calcula o logaritmo de base e do argumento|  
|[modf](concurrency-fast-math-namespace-functions.md#modf)|Divide x em frações e partes do inteiro.|  
|[modff](concurrency-fast-math-namespace-functions.md#modff)|Divide x em frações e partes do inteiro.|  
|[pow](concurrency-fast-math-namespace-functions.md#pow)|Calcula x elevado à potência de y|  
|[powf](concurrency-fast-math-namespace-functions.md#powf)|Calcula x elevado à potência de y|  
|[round](concurrency-fast-math-namespace-functions.md#round)|Arredonda x para o inteiro mais próximo|  
|[roundf](concurrency-fast-math-namespace-functions.md#roundf)|Arredonda x para o inteiro mais próximo|  
|[rsqrt](concurrency-fast-math-namespace-functions.md#rsqrt)|Retorna o recíproco da raiz quadrada do argumento|  
|[rsqrtf](concurrency-fast-math-namespace-functions.md#rsqrtf)|Retorna o recíproco da raiz quadrada do argumento|  
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|Retorna o sinal do argumento|  
|[signbitf](concurrency-fast-math-namespace-functions.md#signbitf)|Retorna o sinal do argumento|  
|[sin](concurrency-fast-math-namespace-functions.md#sin)|Calcula o valor do seno do argumento|  
|[sincos](concurrency-fast-math-namespace-functions.md#sincos)|Calcula o seno e o cosseno o valor de x|  
|[sincosf](concurrency-fast-math-namespace-functions.md#sincosf)|Calcula o seno e o cosseno o valor de x|  
|[sinf](concurrency-fast-math-namespace-functions.md#sinf)|Calcula o valor do seno do argumento|  
|[sinh](concurrency-fast-math-namespace-functions.md#sinh)|Calcula o valor do seno hiperbólico do argumento|  
|[sinhf](concurrency-fast-math-namespace-functions.md#sinhf)|Calcula o valor do seno hiperbólico do argumento|  
|[sqrt](concurrency-fast-math-namespace-functions.md#sqrt)|Calcula a raiz quadrada do argumento|  
|[sqrtf](concurrency-fast-math-namespace-functions.md#sqrtf)|Calcula a raiz quadrada do argumento|  
|[tan](concurrency-fast-math-namespace-functions.md#tan)|Calcula o valor tangente do argumento|  
|[tanf](concurrency-fast-math-namespace-functions.md#tanf)|Calcula o valor tangente do argumento|  
|[tanh](concurrency-fast-math-namespace-functions.md#tanh)|Calcula o valor de tangente hiperbólico do argumento|  
|[tanhf](concurrency-fast-math-namespace-functions.md#tanhf)|Calcula o valor de tangente hiperbólico do argumento|  
|[trunc](concurrency-fast-math-namespace-functions.md#trunc)|Trunca o argumento para o componente inteiro|  
|[truncf](concurrency-fast-math-namespace-functions.md#truncf)|Trunca o argumento para o componente inteiro|  

## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** amp_math. h  
  
 **Namespace:** Concurrency:: fast_math  
  
## <a name="see-also"></a>Consulte também  
 [Namespace de simultaneidade (C++ AMP)](concurrency-namespace-cpp-amp.md)
