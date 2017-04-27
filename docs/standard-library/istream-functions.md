---
title: "Funções &lt;istream&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: aa35f177bcb986e141d0e46e48dc007a96f94498
ms.lasthandoff: 02/25/2017

---
# <a name="ltistreamgt-functions"></a>Função &lt;istream&gt;
|||  
|-|-|  
|[swap](#istream_swap)|[ws](#ws)|  
  
##  <a name="istream_swap"></a>  swap  
 Troca os elementos de dois objetos de fluxo.  
  
```  
template <class Elem, class Tr>  
void swap(
    basic_istream<Elem, Tr>& left,  
    basic_istream<Elem, Tr>& right);

template <class Elem, class Tr>  
void swap(
    basic_iostream<Elem, Tr>& left,  
    basic_iostream<Elem, Tr>& right);
```  
  
### <a name="parameters"></a>Parâmetros  
 `left`  
 Um fluxo.  
  
 `right`  
 Um fluxo.  
  
##  <a name="ws"></a>  ws  
 Ignora o espaço em branco no fluxo.  
  
```  
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Istr`  
 Um fluxo.  
  
### <a name="return-value"></a>Valor de retorno  
 O fluxo.  
  
### <a name="remarks"></a>Comentários  
 O manipulador extrai e descarta quaisquer elementos `ch` para os quais [use_facet](../standard-library/basic-filebuf-class.md#basic_filebuf__open)< **ctype**\< **Elem**> >( [getloc](../standard-library/ios-base-class.md#ios_base__getloc)). **is**( **ctype**\< **Elem**>:: **space**, **ch**) for verdadeiro.  
  
 A função chamará [setstate](../standard-library/basic-ios-class.md#basic_ios__setstate)( **eofbit**) se encontrar o fim do arquivo enquanto extrai os elementos. Ele retorna `_Istr`.  
  
### <a name="example"></a>Exemplo  
  Consulte [operator>>](../standard-library/istream-operators.md#operator_gt__gt_) para ver um exemplo de como usar `ws`.  
  
## <a name="see-also"></a>Consulte também  
 [\<istream>](../standard-library/istream.md)

