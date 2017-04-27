---
title: '&lt;future&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <future>
dev_langs:
- C++
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 4c83adc4b7365518275d5d54ac927012abc29657
ms.lasthandoff: 02/25/2017

---
# <a name="ltfuturegt"></a>&lt;future&gt;
Inclua o cabeçalho padrão \<future> para definir classes de modelos e modelos de suporte que simplificam a execução de uma função — possivelmente em um thread separado — e a recuperação de seu resultado. O resultado é o valor retornado pela função ou uma exceção que é emitida pela função, mas não é capturada na função.  
  
 Esse cabeçalho usa ConcRT (Tempo de Execução de Simultaneidade) para que você possa usá-lo juntamente com outros mecanismos ConcRT. Para obter mais informações sobre o ConcRT, consulte [Tempo de execução de simultaneidade](../parallel/concrt/concurrency-runtime.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
#include <future>  
```  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  No código que é compilado usando **/clr**, esse cabeçalho é bloqueado.  
  
 Um *provedor assíncrono* armazena o resultado de uma chamada de função. Um *objeto de retorno assíncrono* é usado para recuperar o resultado de uma chamada de função. Um *estado assíncrono associado* fornece comunicação entre um provedor assíncrono e um ou mais objetos de retorno assíncronos.  
  
 Um programa não cria diretamente nenhum objetos de estado assíncrono associado. O programa cria um provedor assíncrono sempre que precisa de um e, por meio dele, cria um objeto de retorno assíncrono que compartilha seu estado assíncrono associado com o provedor. Provedores assíncronos e objetos de retorno assíncronos gerenciam os objetos que mantêm seu estado assíncrono associado compartilhado. Quando o último objeto que faz referência ao estado assíncrono associado o libera, o objeto que contém o estado assíncrono associado é destruído.  
  
 Um provedor assíncrono ou um objeto de retorno assíncrono sem nenhum estado assíncrono associado fica *vazio*.  
  
 Um estado assíncrono associado ficará *pronto* somente se seu provedor assíncrono tiver armazenado um valor retornado ou armazenado uma exceção.  
  
 A função de modelo `async` e as classes de modelo `promise` e `packaged_task` são provedores assíncronos. As classes de modelo `future` e `shared_future` descrevem objetos de retorno assíncronos.  
  
 Cada uma das classes de modelo `promise`, `future` e `shared_future` tem uma especialização para o tipo `void` e uma especialização parcial para armazenar e recuperar um valor por referência. Essas especializações diferem do modelo primário somente quanto às assinaturas e à semântica das funções que armazenam e recuperam o valor retornado.  
  
 As classes de modelo `future` e `shared_future` nunca bloqueiam seus destruidores, exceto em um caso que é preservado para compatibilidade com versões anteriores: diferente de todos os outros futures, para um `future` — ou para o último `shared_future` — anexado a uma tarefa iniciada com `std::async`, o destruidor é bloqueado se a tarefa não tiver sido concluída, ou seja, ele é bloqueado se o thread ainda não tiver chamado `.get()` ou `.wait()` e a tarefa ainda estiver em execução. A observação de usabilidade a seguir foi adicionada à descrição de `std::async` no padrão de rascunho: "[Observação: se um future obtido de std::async for movido para fora do escopo local, outro código que usa o future deve estar ciente de que o destruidor do future pode ser bloqueado para que o estado compartilhado fique pronto. — final da observação]". Em todos os outros casos, os destruidores `future` e `shared_future` são obrigatórios e é garantido que eles nunca são bloqueados.  
  
## <a name="members"></a>Membros  
  
### <a name="classes"></a>Classes  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Classe future](../standard-library/future-class.md)|Descreve um objeto de retorno assíncrono.|  
|[Classe future_error](../standard-library/future-error-class.md)|Descreve um objeto de exceção que pode ser gerado por métodos de tipos que gerenciam objetos `future`.|  
|[Classe packaged_task](../standard-library/packaged-task-class.md)|Descreve um provedor assíncrono que é um wrapper de chamada e cuja assinatura de chamada é `Ty(ArgTypes...)`. O estado assíncrono associado mantém uma cópia de seu objeto que pode ser chamado, bem como o possível resultado.|  
|[Classe promise](../standard-library/promise-class.md)|Descreve um provedor assíncrono.|  
|[Classe shared_future](../standard-library/shared-future-class.md)|Descreve um objeto de retorno assíncrono. Diferente de um objeto `future`, um provedor assíncrono pode ser associado a qualquer quantidade de objetos `shared_future`.|  
  
### <a name="structures"></a>Estruturas  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Estrutura is_error_code_enum](../standard-library/is-error-code-enum-structure.md)|Especialização que indica que `future_errc` é adequado para armazenar um `error_code`.|  
|[Estrutura uses_allocator](../standard-library/uses-allocator-structure.md)|Especialização que sempre se aplica.|  
  
### <a name="functions"></a>Funções  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Função async](../standard-library/future-functions.md#async_function)|Representa um provedor assíncrono.|  
|[Função future_category](../standard-library/future-functions.md#future_category_function)|Retorna uma referência ao objeto `error_category` que caracteriza erros associados a objetos `future`.|  
|[Função make_error_code](../standard-library/future-functions.md#make_error_code_function)|Cria um `error_code` que tem o objeto `error_category` que caracteriza erros `future`.|  
|[Função make_error_condition](../standard-library/future-functions.md#make_error_condition_function)|Cria um `error_condition` que tem o objeto `error_category` que caracteriza erros `future`.|  
|[Função swap](../standard-library/future-functions.md#swap_function)|Troca o estado assíncrono associado de um objeto `promise` pelo de outro objeto.|  
  
### <a name="enumerations"></a>Enumerações  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Enumeração future_errc](../standard-library/future-enums.md#future_errc_enumeration)|Fornece nomes simbólicos para os erros relatados pela classe `future_error`.|  
|[Enumeração future_status](../standard-library/future-enums.md#future_status_enumeration)|Fornece nomes simbólicos para os motivos que uma função de espera temporizada pode retornar.|  
|[Enumeração launch](../standard-library/future-enums.md#launch_enumeration)|Representa um tipo de bitmask que descreve os modos possíveis para a função de modelo `async`.|  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Arquivos de Cabeçalho](../standard-library/cpp-standard-library-header-files.md)



