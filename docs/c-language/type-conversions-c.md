---
title: "Conversões de tipo (C) | Microsoft Docs"
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
- conversions, type
- type conversion
- converting types
- integral promotions
- type casts, when performed
ms.assetid: d130ee7c-03c3-48f4-af7b-1fdba0d3b086
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
ms.openlocfilehash: 41796b03cca13a89d3519a0505faa3d5b6acd2b7
ms.lasthandoff: 02/25/2017

---
# <a name="type-conversions-c"></a>Conversões de tipo (C)
As conversões de tipos dependem do operador especificado e do tipo de operando ou dos operadores. As conversões de tipo são executadas nos seguintes casos:  
  
-   Quando um valor de um tipo é atribuído a uma variável de um tipo diferente ou um operador converte o tipo do seu operando ou operandos antes de executar uma operação  
  
-   Quando um valor de um tipo é explicitamente convertido em um tipo diferente  
  
-   Quando um valor é passado como um argumento para uma função ou quando um tipo é retornado de uma função  
  
 Um caractere, inteiro curto ou campo de bit de inteiro, todos assinados ou não, ou um objeto de tipo de enumeração, podem ser usados em uma expressão sempre que um inteiro puder ser usado. Se `int` puder representar todos os valores do tipo original, o valor será convertido em `int`; caso contrário, ele será convertido em `unsigned int`. Esse processo é chamado de “promoção de integral”. As promoções de integral preservam os valores. Ou seja, o valor após a promoção tem a garantia de ser o mesmo que antes de promoção. Consulte [Conversões aritméticas usuais](../c-language/usual-arithmetic-conversions.md) para obter mais informações.  
  
## <a name="see-also"></a>Consulte também  
 [Expressões e atribuições](../c-language/expressions-and-assignments.md)