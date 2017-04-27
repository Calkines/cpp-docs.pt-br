---
title: Classe unchecked_array_iterator | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- unchecked_array_iterator
- stdext::unchecked_array_iterator
dev_langs:
- C++
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
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
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 850f1eced3ef5354a382d392c83b8180a18b4dfb
ms.lasthandoff: 02/25/2017

---
# <a name="uncheckedarrayiterator-class"></a>Classe unchecked_array_iterator
A classe `unchecked_array_iterator` permite que você encapsule uma matriz ou um ponteiro em um iterador não verificado. Use essa classe como um wrapper (usando a função [make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator)) para matrizes ou ponteiros brutos como uma maneira direcionada de gerenciar avisos de ponteiros não verificados, em vez de silenciar esses avisos globalmente. Se possível, prefira a versão verificada dessa classe, [checked_array_iterator](../standard-library/checked-array-iterator-class.md).  
  
> [!NOTE]
>  Essa classe é uma extensão da Microsoft da Biblioteca Padrão C++. O código implementado usando essa função não é portátil para ambientes de criação do C++ Standard que não oferecem suporte a essa extensão da Microsoft.  
  
## <a name="syntax"></a>Sintaxe  
  
```
template <class Iterator>  
class unchecked_array_iterator;
```  
  
## <a name="remarks"></a>Comentários  
 Essa classe é definida no namespace [stdext](../standard-library/stdext-namespace.md).  
  
 Esta é a versão não verificada da [classe checked_array_iterator](../standard-library/checked-array-iterator-class.md) e dá suporte a todos os mesmos membros e sobrecargas. Para obter mais informações sobre o recurso de iterador verificado com exemplos de código, consulte [Checked Iterators](../standard-library/checked-iterators.md).  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<iterator>  
  
 **Namespace:** stdext  
  
## <a name="see-also"></a>Consulte também  
 [\<iterator>](../standard-library/iterator.md)   
 [Referência da biblioteca padrão C++](../standard-library/cpp-standard-library-reference.md)



