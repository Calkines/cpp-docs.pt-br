---
title: Classe sync_per_thread | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- stdext::sync_per_thread
- sync_per_thread
- allocators/stdext::sync_per_thread
- allocators/stdext::sync_per_thread::allocate
- allocators/stdext::sync_per_thread::deallocate
- allocators/stdext::sync_per_thread::equals
dev_langs:
- C++
helpviewer_keywords:
- sync_per_thread class
ms.assetid: 47bf75f8-5b02-4760-b1d3-3099d08fe14c
caps.latest.revision: 19
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
ms.openlocfilehash: 5ac1ae540c5ff87555b549d6526a0df6b1d22406
ms.lasthandoff: 02/25/2017

---
# <a name="syncperthread-class"></a>Classe sync_per_thread
Descreve um [filtro de sincronização](../standard-library/allocators-header.md) que fornece um objeto de cache separado para cada thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```
template <class Cache>  
class sync_per_thread
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`Cache`|O tipo de cache associado ao filtro de sincronização. Pode ser [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) ou [cache_suballoc](../standard-library/cache-suballoc-class.md).|  
  
## <a name="remarks"></a>Comentários  
 Os alocadores que usam `sync_per_thread` podem ser comparados como iguais mesmo se os blocos alocados em um thread não podem ser desalocados de outro thread. Ao usar um desses alocadores, os blocos de memória alocados em um thread não devem ficar visíveis para outros threads. Na prática, isso significa que um contêiner que usa um desses alocadores deve ser acessado somente por um único thread.  
  
### <a name="member-functions"></a>Funções membro  
  
|||  
|-|-|  
|[allocate](#sync_per_thread__allocate)|Aloca um bloco de memória.|  
|[deallocate](#sync_per_thread__deallocate)|Libera um número especificado de objetos do armazenamento começando em uma posição especificada.|  
|[equals](#sync_per_thread__equals)|Compara a igualdade de dois caches.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<allocators>  
  
 **Namespace:** stdext  
  
##  <a name="sync_per_thread__allocate"></a>  sync_per_thread::allocate  
 Aloca um bloco de memória.  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`count`|O número de elementos na matriz a serem alocados.|  
  
### <a name="remarks"></a>Comentários  
 A função membro retorna o resultado de uma chamada a `cache::allocate(count)` no objeto de cache que pertence ao thread atual. Se nenhum objeto de cache tiver sido alocado para o thread atual, ele primeiro alocará um.  
  
##  <a name="sync_per_thread__deallocate"></a>  sync_per_thread::deallocate  
 Libera um número especificado de objetos do armazenamento começando em uma posição especificada.  
  
```
void deallocate(void* ptr, std::size_t count);
```  
  
### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`ptr`|Um ponteiro para o primeiro objeto a ser desalocado do armazenamento.|  
|`count`|O número de objetos a serem desalocados do armazenamento.|  
  
### <a name="remarks"></a>Comentários  
 A função membro chama `deallocate` no objeto de cache que pertence ao thread atual. Se nenhum objeto de cache tiver sido alocado para o thread atual, ele primeiro alocará um.  
  
##  <a name="sync_per_thread__equals"></a>  sync_per_thread::equals  
 Compara a igualdade de dois caches.  
  
```
bool equals(const sync<Cache>& Other) const;
```  
  
### <a name="parameters"></a>Parâmetros  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`Cache`|O objeto de cache do filtro de sincronização.|  
|`Other`|O objeto de cache a ser comparado quanto à igualdade.|  
  
### <a name="return-value"></a>Valor de retorno  
 `false` se nenhum objeto de cache foi alocado a esse objeto ou a `Other` no thread atual. Caso contrário, retornará o resultado da aplicação de `operator==` aos dois objetos de cache.  
  
### <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [\<allocators>](../standard-library/allocators-header.md)



