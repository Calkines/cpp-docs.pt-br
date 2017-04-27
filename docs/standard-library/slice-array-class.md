---
title: Classe slice_array | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- slice_array
- valarray/std::slice_array
dev_langs:
- C++
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: a56db37d5684438bac79bbc2d0273fcfbc53a2c1
ms.lasthandoff: 02/25/2017

---
# <a name="slicearray-class"></a>Classe slice_array
Uma classe de modelo auxiliar interna, que dá suporte a objetos de fatia fornecendo operações entre matrizes de subconjunto definidas pela fatia de um valarray.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
template <class Type>  
class slice_array : public slice {  
public:  
    typedef Type value_type;  
    void operator=(const valarray<Type>& x) const;

 
    void operator=(const Type& x) const;

 
    void operator*=(const valarray<Type>& x) const;

 
    void operator/=(const valarray<Type>& x) const;

 
    void operator%=(const valarray<Type>& x) const;

 
    void operator+=(const valarray<Type>& x) const;

 
    void operator-=(const valarray<Type>& x) const;

 
    void operator^=(const valarray<Type>& x) const;

 
    void operator&=(const valarray<Type>& x) const;

 
    void operator|=(const valarray<Type>& x) const;

 
    void operator<<=(const valarray<Type>& x) const;

 
    void operator>>=(const valarray<Type>& x) const;

 
// The rest is private or implementation defined  
}  
```  
  
## <a name="remarks"></a>Comentários  
 A classe descreve um objeto que armazena uma referência a um objeto da classe [valarray](../standard-library/valarray-class.md)**\<Type>**, bem como um objeto da classe [slice](../standard-library/slice-class.md), que descreve a sequência de elementos a serem selecionados do objeto **valarray\<Type>**.  
  
 A classe de modelo é criada indiretamente por determinadas operações de valarray e não pode ser usada diretamente no programa. Uma classe de modelo auxiliar interna que é usada pelo operador de subscrito da slice:  
  
 `slice_array`\<**Type**> `valarray`< **Type**:: `operator[]` ( `slice`).  
  
 Você constrói um objeto **slice_array\<Type>** apenas escrevendo uma expressão no formato [va&#91;sl&#93;](../standard-library/valarray-class.md#valarray__operator_at), para uma slice **sl** do valarray **va**. As funções membro da classe gslice_array, então, se comportam como as assinaturas de função correspondentes definidas para **valarray\<Type>**, exceto pelo fato de somente a sequência de elementos selecionados ser afetada. A sequência controlada por slice_array é definida pelos três parâmetros do construtor de slice, o índice do primeiro elemento na slice, o número de elementos e a distância entre os elementos. Um slice_array recortado de valarray **va** declarado pelo **va**[ `slice`(2, 5, 3)] seleciona elementos com índices 2, 5, 8, 11 e 14 de **va**. Os índices devem ser válidos para que o procedimento seja válido.  
  
## <a name="example"></a>Exemplo  
 Veja o exemplo de [slice::slice](../standard-library/slice-class.md#slice__slice) para obter um exemplo de como declarar e usar um slice_array.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<valarray>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>Consulte também  
 [Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

