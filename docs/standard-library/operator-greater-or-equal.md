---
title: operator&gt;= | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- operator>=
- std::>=
- std.operator>=
- '>='
- std.>=
- std::operator>=
dev_langs:
- C++
helpviewer_keywords:
- '>= operator, comparing specific objects'
- operator >=
- operator>=
ms.assetid: 14fbebf5-8b75-4afa-a51b-3112d31c07cf
caps.latest.revision: 9
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
ms.openlocfilehash: 915c180caefa7f39cc0c9defcff688b3ed6520a0
ms.lasthandoff: 02/25/2017

---
# <a name="operatorgt"></a>operator&gt;=
> [!NOTE]
>  Este tópico faz parte da documentação do Visual C++ como um exemplo não funcional de contêineres usados na Biblioteca Padrão C++. Para obter mais informações, consulte [Contêineres da biblioteca padrão C++](../standard-library/stl-containers.md).  
  
 Sobrecarregue **operator>=** para comparar dois objetos da classe de modelo [Container](../standard-library/sample-container-class.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
 
    template <class Ty>  
bool operator>=(
    const Container <Ty>& left,  
    const Container <Ty>& right);
```  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna **!**(_*Left* < \_*Right*).  
  
## <a name="see-also"></a>Consulte também  
 [\<sample container>](../standard-library/sample-container.md)

