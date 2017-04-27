---
title: "Enumerações &lt;limits&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: e0f4b6ca5d11207787f9ff4f27b21dbbc78080c0
ms.lasthandoff: 02/25/2017

---
# <a name="ltlimitsgt-enums"></a>Enumerações &lt;limits&gt;
|||  
|-|-|  
|[Enumeração float_denorm_style](#float_denorm_style_enumeration)|[Enumeração float_round_style](#float_round_style_enumeration)|  
  
##  <a name="a-namefloatdenormstyleenumerationa--floatdenormstyle-enumeration"></a><a name="float_denorm_style_enumeration"></a> Enumeração float_denorm_style  
 A enumeração descreve os vários métodos que uma implementação pode escolher para representar um valor de ponto flutuante desnormalizado — um pequeno demais para ser representado como um valor normalizado:  
  
```
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```  
  
### <a name="return-value"></a>Valor de retorno  
 A enumeração retornará:  
  
- **denorm_indeterminate** se a presença ou ausência de formas desnormalizadas não puder ser determinada no momento da conversão.  
  
- **denorm_absent** se formas desnormalizadas estiverem ausentes.  
  
- **denorm_present** se formas desnormalizadas estiverem presentes.  
  
### <a name="example"></a>Exemplo  
  Consulte [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#numeric_limits__has_denorm) para ver um exemplo em que os valores da enumeração podem ser acessados.  
  
##  <a name="a-namefloatroundstyleenumerationa--floatroundstyle-enumeration"></a><a name="float_round_style_enumeration"></a> Enumeração float_round_style  
 A enumeração descreve os vários métodos que uma implementação pode escolher para fazer o arredondamento de um valor de ponto flutuante para um valor inteiro.  
  
```
enum float_round_style {    
    round_indeterminate = -1,
    round_toward_zero = 0,
    round_to_nearest = 1,
    round_toward_infinity = 2,
    round_toward_neg_infinity = 3    };
```  
  
### <a name="return-value"></a>Valor de retorno  
 A enumeração retornará:  
  
- **round_indeterminate** se o método de arredondamento não puder ser determinado.  
  
- **round_toward_zero** se o arredondamento for feito em direção a zero.  
  
- **round_to_nearest** se o arredondamento for feito para o inteiro mais próximo.  
  
- **round_toward_infinity** se o arredondamento for feito se distanciando de zero.  
  
- **round_toward_neg_infinity** se o arredondamento for feito para o inteiro mais negativo.  
  
### <a name="example"></a>Exemplo  
  Consulte [numeric_limits::round_style](../standard-library/numeric-limits-class.md#numeric_limits__round_style) para ver um exemplo em que os valores da enumeração podem ser acessados.  
  
## <a name="see-also"></a>Consulte também  
 [\<limits>](../standard-library/limits.md)



