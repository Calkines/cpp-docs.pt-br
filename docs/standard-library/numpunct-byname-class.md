---
title: Classe numpunct_byname | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- numpunct_byname
- xlocnum/std::numpunct_byname
dev_langs:
- C++
helpviewer_keywords:
- numpunct_byname class
ms.assetid: 18412924-e085-4771-b5e9-7a200cbdd7c0
caps.latest.revision: 24
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
ms.openlocfilehash: eea856d76ee0fcf12c1cdb4bf1bf0dd0f3125d5f
ms.lasthandoff: 02/25/2017

---
# <a name="numpunctbyname-class"></a>Classe numpunct_byname
A classe de modelo derivada que descreve um objeto que pode funcionar como uma faceta `numpunct` de uma determinada localidade, permitindo a formatação e pontuação de expressões numéricas e boolianas.  
  
## <a name="syntax"></a>Sintaxe  
  
```
template <class CharType>
class numpunct_byname : public numpunct<Elem> {
public:
    explicit numpunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit numpunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~numpunct_byname();

 };
```  
  
## <a name="remarks"></a>Comentários  
 Seu comportamento é determinado pela localidade [nomeada](../standard-library/locale-class.md#locale__name) `_Locname`. O construtor inicializa seu objeto base com [numpunct](../standard-library/numpunct-class.md#numpunct__numpunct)\<CharType>( `_Refs`).  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<locale>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>Consulte também  
 [Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



