---
title: Classe allocator_unbounded | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdext::allocators::allocator_unbounded
- allocator_unbounded
- allocators/stdext::allocator_unbounded
- allocators::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
dev_langs:
- C++
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
caps.latest.revision: 17
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
ms.openlocfilehash: edaecf775fb9f678d1f936fac60967bedb61f65f
ms.lasthandoff: 02/25/2017

---
# <a name="allocatorunbounded-class"></a>Classe allocator_unbounded
Descreve um objeto que gerencia a alocação e a liberação de armazenamento de objetos do tipo `Type`, usando um cache do tipo [cache_freelist](../standard-library/cache-freelist-class.md) com um comprimento gerenciado por [max_unbounded](../standard-library/max-unbounded-class.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```
template <class Type>  
class allocator_unbounded;
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`Type`|O tipo dos elementos alocados pelo alocador.|  
  
## <a name="remarks"></a>Comentários  
 A macro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) passa essa classe como o parâmetro `name` na instrução a seguir: `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<allocators>  
  
 **Namespace:** stdext  
  
## <a name="see-also"></a>Consulte também  
 [\<allocators>](../standard-library/allocators-header.md)



