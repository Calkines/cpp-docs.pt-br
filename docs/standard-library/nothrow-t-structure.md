---
title: Estrutura nothrow_t | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- nothrow_t
dev_langs:
- C++
helpviewer_keywords:
- nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
caps.latest.revision: 20
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
ms.sourcegitcommit: 85c900f2263ae1c1089478badc85388e3b5e8548
ms.openlocfilehash: b490cccf048b5d5b9be53508331cba89e66c952f
ms.lasthandoff: 02/25/2017

---
# <a name="nothrowt-structure"></a>Estrutura nothrow_t
O struct é usado como um parâmetro de função para o operador new para indicar que a função deve retornar um ponteiro nulo para relatar uma falha de alocação, em vez de lançar uma exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```
struct std::nothrow_t {};
```  
  
## <a name="remarks"></a>Comentários  
 O struct ajuda o compilador a selecionar a versão correta do construtor. [nothrow](../standard-library/new-functions.md#nothrow) é um sinônimo para objetos do tipo `std::nothrow_t`.  
  
## <a name="example"></a>Exemplo  
 Consulte [operador new](../standard-library/new-operators.md#operator_new) e [operador new&#91;&#93;](../standard-library/new-operators.md#operator_new_arr) para obter exemplos de como `std::nothrow_t` é usado como um parâmetro de função.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<new>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>Consulte também  
 [Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



