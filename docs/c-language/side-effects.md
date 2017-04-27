---
title: Efeitos colaterais | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- expression evaluation, side effects
- side effects in expression evaluation
ms.assetid: d9b3004a-830e-43a0-bea5-8989d501d670
caps.latest.revision: 7
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
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 597519660c82da25e8f2bcd9e12cb9762dd92b5c
ms.lasthandoff: 02/25/2017

---
# <a name="side-effects"></a>Efeitos colaterais
A ordem de avaliação das expressões é definida pela implementação específica, exceto quando a linguagem garante uma determinada ordem de avaliação (conforme descrito em [Precedência e ordem de avaliação](../c-language/precedence-and-order-of-evaluation.md)). Por exemplo, os efeitos colaterais ocorrem nas seguintes chamadas de função:  
  
```  
add( i + 1, i = j + 2 );  
myproc( getc(), getc() );  
```  
  
 Os argumentos de uma chamada de função podem ser avaliados em qualquer ordem. A expressão `i + 1` pode ser avaliada antes de `i = j + 2`, ou `i = j + 2` pode ser avaliada antes de `i + 1`. O resultado é diferente em cada caso. De maneira similar, não é possível garantir quais caracteres serão passados para `myproc`. Como os incrementos unários e operações de redução envolvem atribuições, essas operações podem causar efeitos colaterais, conforme mostrado no seguinte exemplo:  
  
```  
x[i] = i++;  
```  
  
 Neste exemplo, o valor de `x` alterado é imprevisível. O valor do subscrito pode ser o valor novo ou antigo de `i`. O resultado pode variar em compiladores diferentes ou níveis de otimização diferentes.  
  
 Como C não define a ordem de avaliação de efeitos colaterais, ambos os métodos de avaliação discutidos anteriormente estão corretos e qualquer um pode ser implementado. Para garantir que o seu código seja portátil e claro, evite as instruções que dependem de um pedido específico de avaliação quanto aos efeitos colaterais.  
  
## <a name="see-also"></a>Consulte também  
 [Avaliação de expressão](../c-language/expression-evaluation-c.md)