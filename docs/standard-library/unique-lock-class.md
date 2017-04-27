---
title: Classe unique_lock | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- mutex/std::unique_lock
dev_langs:
- C++
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
caps.latest.revision: 10
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 27145bb5aab7087ddf9dd7d56d51f242062268ff
ms.lasthandoff: 02/25/2017

---
# <a name="uniquelock-class"></a>Classe unique_lock
Representa um modelo que pode ser instanciado para criar objetos que gerenciam o bloqueio e o desbloqueio de um `mutex`.  
  
## <a name="syntax"></a>Sintaxe  
  
```
template <class Mutex>
class unique_lock;
```  
  
## <a name="remarks"></a>Comentários  
 O argumento de modelo `Mutex` deve nomear um *tipo mutex*.  
  
 Internamente, uma `unique_lock` armazena um ponteiro para um tipo de `mutex` objeto e um `bool` que indica se o thread atual possui o `mutex`.  
  
## <a name="members"></a>Membros  
  
### <a name="public-typedefs"></a>Typedefs públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|`mutex_type`|Sinônimo para o argumento de modelo `Mutex`.|  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Construtor unique_lock](#unique_lock__unique_lock_constructor)|Constrói um objeto `unique_lock`.|  
|[Destruidor ~unique_lock](#unique_lock___dtorunique_lock_destructor)|Libera quaisquer recursos que são usados pelo objeto `unique_lock`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[lock](#unique_lock__lock_method)|Bloqueia o thread de chamada até que ele tenha obtido a propriedade do `mutex` associado.|  
|[mutex](#unique_lock__mutex_method)|Recupera o ponteiro armazenado para `mutex` associado.|  
|[owns_lock](#unique_lock__owns_lock_method)|Especifica se o thread de chamada possui o `mutex` associado.|  
|[release](#unique_lock__release_method)|Desassocia o `unique_lock` objeto do objeto `mutex` associado.|  
|[swap](#unique_lock__swap_method)|Alterna o `mutex` associado e status de propriedade com um objeto especificado.|  
|[try_lock](#unique_lock__try_lock_method)|Tenta obter a propriedade do `mutex` associado, sem o bloqueio.|  
|[try_lock_for](#unique_lock__try_lock_for_method)|Tenta obter a propriedade do `mutex` associado, sem o bloqueio.|  
|[try_lock_until](#unique_lock__try_lock_until_method)|Tenta obter a propriedade do `mutex` associado, sem o bloqueio.|  
|[unlock](#unique_lock__unlock_method)|Libera a propriedade do `mutex` associado.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[operator bool](#unique_lock__operator_bool)|Especifica se o thread de chamada tem o `mutex` associado.|  
|[operator=](#unique_lock__operator_eq)|Copia o ponteiro `mutex` armazenado e o status de propriedade associados de um objeto especificado.|  
  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 `unique_lock`  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** mutex  
  
 **Namespace:** std  
  
##  <a name="a-nameuniquelocklockmethoda--lock"></a><a name="unique_lock__lock_method"></a>  lock  
 Bloqueia o thread de chamada até que ele tenha obtido a propriedade do `mutex` associado.  
  
```cpp  
void lock();
```  
  
### <a name="remarks"></a>Comentários  
 Se o ponteiro `mutex` armazenado for `null`, esse método lançará um [system_error](../standard-library/system-error-class.md) que tem um código de erro `operation_not_permitted`.  
  
 Se o thread de chamada já possui `mutex` associado, esse método lançará um `system_error` que tem um código de erro de `resource_deadlock_would_occur`.  
  
 Caso contrário, esse método chama `lock` no `mutex` associado e define o sinalizador de propriedade do thread interno para `true`.  
  
##  <a name="a-nameuniquelockmutexmethoda--mutex"></a><a name="unique_lock__mutex_method"></a>  mutex  
 Recupera o ponteiro armazenado para `mutex` associado.  
  
```cpp  
mutex_type *mutex() const noexcept;
```  
  
##  <a name="a-nameuniquelockoperatorboola--operator-bool"></a><a name="unique_lock__operator_bool"></a>  operator bool  
 Especifica se o thread de chamada tem o mutex associado.  
  
```cpp  
explicit operator bool() noexcept
```  
  
### <a name="return-value"></a>Valor de retorno  
 `true` se o thread possui o mutex; Caso contrário, `false`.  
  
##  <a name="a-nameuniquelockoperatoreqa--operator"></a><a name="unique_lock__operator_eq"></a>  operator=  
 Copia o ponteiro `mutex` armazenado e o status de propriedade associados de um objeto especificado.  
  
```cpp  
unique_lock& operator=(unique_lock&& Other) noexcept;
```  
  
### <a name="parameters"></a>Parâmetros  
 `Other`  
 Um objeto `unique_lock`.  
  
### <a name="return-value"></a>Valor de retorno  
 `*this`  
  
### <a name="remarks"></a>Comentários  
 Se o thread de chamada possui o `mutex` previamente associado, antes desse método chamar `unlock` no `mutex`, ele atribui novos valores.  
  
 Após a cópia, esse método define `Other` para um estado construído por padrão.  
  
##  <a name="a-nameuniquelockownslockmethoda--ownslock"></a><a name="unique_lock__owns_lock_method"></a>  owns_lock  
 Especifica se o thread de chamada possui o `mutex` associado.  
  
```cpp  
bool owns_lock() const noexcept;
```  
  
### <a name="return-value"></a>Valor de retorno  
 `true` se o thread possui o `mutex`; Caso contrário, `false`.  
  
##  <a name="a-nameuniquelockreleasemethoda--release"></a><a name="unique_lock__release_method"></a>  release  
 Desassocia o `unique_lock` objeto do objeto `mutex` associado.  
  
```cpp  
mutex_type *release() noexcept;
```  
  
### <a name="return-value"></a>Valor de retorno  
 O valor anterior do ponteiro `mutex` armazenado.  
  
### <a name="remarks"></a>Comentários  
 Esse método define o valor de ponteiro `mutex` armazenado como 0 e define sinalizador `mutex` interno de propriedade para `false`.  
  
##  <a name="a-nameuniquelockswapmethoda--swap"></a><a name="unique_lock__swap_method"></a>  swap  
 Alterna o `mutex` associado e status de propriedade com um objeto especificado.  
  
```
void swap(unique_lock& Other) noexcept;
```  
  
### <a name="parameters"></a>Parâmetros  
 `Other`  
 Um objeto `unique_lock`.  
  
##  <a name="a-nameuniquelocktrylockmethoda--trylock"></a><a name="unique_lock__try_lock_method"></a>  try_lock  
 Tenta obter a propriedade do `mutex` associado, sem o bloqueio.  
  
```cpp  
bool try_lock() noexcept;
```  
  
### <a name="return-value"></a>Valor de retorno  
 `true` se o método obtiver a propriedade do `mutex` com êxito; caso contrário, `false`.  
  
### <a name="remarks"></a>Comentários  
 Se o ponteiro `mutex` armazenado for `null`, o método lançará um [system_error](../standard-library/system-error-class.md) que tem um código de erro `operation_not_permitted`.  
  
 Se o thread de chamada já possui o `mutex`, esse método lança um `system_error` que tem um código de erro de `resource_deadlock_would_occur`.  
  
##  <a name="a-nameuniquelocktrylockformethoda--trylockfor"></a><a name="unique_lock__try_lock_for_method"></a>  try_lock_for  
 Tenta obter a propriedade do `mutex` associado, sem o bloqueio.  
  
```
template <class Rep, class Period>
bool try_lock_for(
    const chrono::duration<Rep, Period>& Rel_time);
```  
  
### <a name="parameters"></a>Parâmetros  
 `Rel_time`  
 Um objeto [chrono::duration](../standard-library/duration-class.md) que especifica o tempo máximo que o método tenta obter a propriedade do `mutex`.  
  
### <a name="return-value"></a>Valor de retorno  
 `true` se o método obtiver a propriedade do `mutex` com êxito; caso contrário, `false`.  
  
### <a name="remarks"></a>Comentários  
 Se o ponteiro `mutex` armazenado for `null`, o método lançará um [system_error](../standard-library/system-error-class.md) que tem um código de erro `operation_not_permitted`.  
  
 Se o thread de chamada já possui o `mutex`, esse método lança um `system_error` que tem um código de erro de `resource_deadlock_would_occur`.  
  
##  <a name="a-nameuniquelocktrylockuntilmethoda--trylockuntil"></a><a name="unique_lock__try_lock_until_method"></a>  try_lock_until  
 Tenta obter a propriedade do `mutex` associado, sem o bloqueio.  
  
```cpp  
template <class Clock, class Duration>
bool try_lock_until(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```  
  
### <a name="parameters"></a>Parâmetros  
 `Abs_time`  
 Um ponto no tempo que especifica o limite após o qual o método não tenta mais obter a propriedade do `mutex`.  
  
### <a name="return-value"></a>Valor de retorno  
 `true` se o método obtiver a propriedade do `mutex` com êxito; caso contrário, `false`.  
  
### <a name="remarks"></a>Comentários  
 Se o ponteiro `mutex` armazenado for `null`, o método lançará um [system_error](../standard-library/system-error-class.md) que tem um código de erro `operation_not_permitted`.  
  
 Se o thread de chamada já possui o `mutex`, esse método lança um `system_error` que tem um código de erro de `resource_deadlock_would_occur`.  
  
##  <a name="a-nameuniquelockuniquelockconstructora--uniquelock-constructor"></a><a name="unique_lock__unique_lock_constructor"></a> Construtor unique_lock  
 Constrói um objeto `unique_lock`.  
  
```cpp  
unique_lock() noexcept;
unique_lock(unique_lock&& Other) noexcept;
explicit unique_lock(mutex_type& Mtx);

unique_lock(mutex_type& Mtx, adopt_lock_t Adopt);

unique_lock(mutex_type& Mtx, defer_lock_t Defer) noexcept;
unique_lock(mutex_type& Mtx, try_to_lock_t Try);

template <class Rep, class Period>
unique_lock(mutex_type& Mtx,
    const chrono::duration<Rep, Period>  
Rel_time);

template <class Clock, class Duration>
unique_lock(mutex_type& Mtx,
    const chrono::time_point<Clock, Duration>  
Abs_time);

unique_lock(mutex_type& Mtx,
    const xtime* Abs_time) noexcept;
```  
  
### <a name="parameters"></a>Parâmetros  
 `Mtx`  
 Um objeto do tipo mutex.  
  
 `Rel_time`  
 Um objeto [chrono::duration](../standard-library/duration-class.md) que especifica o tempo máximo que o método tenta obter a propriedade do `mutex`.  
  
 `Abs_time`  
 Um ponto no tempo que especifica o limite após o qual o método não tenta mais obter a propriedade do `mutex`.  
  
 `Other`  
 Um objeto `unique_lock`.  
  
### <a name="remarks"></a>Comentários  
 O primeiro construtor constrói um objeto que tem um valor de ponteiro mutex associado de 0.  
  
 O segundo construtor move o status mutex associado de `Other`. Após a movimentação, `Other` não está associado a um mutex.  
  
 Os construtores restantes armazenado & `Mtx` conforme o ponteiro `mutex` armazenado. Propriedade do `mutex` será determinada pelo segundo argumento, se ele existir.  
  
|||  
|-|-|  
|`No argument`|Propriedade é obtida chamando o método de `lock` no objeto `mutex` associado.|  
|`Adopt`|Propriedade será assumida. `Mtx` deve ser bloqueado quando esse construtor for chamado.|  
|`Defer`|O thread de chamada é presumido como não possuindo o objeto `mutex`. `Mtx` não deve ser bloqueado quando esse construtor for chamado.|  
|`Try`|Propriedade é obtida chamando `try_lock` no objeto `mutex` associado. O construtor não lança nada.|  
|`Rel_time`|Propriedade é determinada pela chamada de `try_lock_for(Rel_time)`.|  
|`Abs_time`|Propriedade é determinada pela chamada de `try_lock_until(Abs_time)`.|  
  
##  <a name="a-nameuniquelockdtoruniquelockdestructora--uniquelock-destructor"></a><a name="unique_lock___dtorunique_lock_destructor"></a> Destruidor ~unique_lock  
 Libera quaisquer recursos que são usados pelo objeto `unique_lock`.  
  
```cpp  
~unique_lock() noexcept;
```  
  
### <a name="remarks"></a>Comentários  
 Se o thread de chamada possui `mutex` associado, o destruidor libera a propriedade chamando desbloqueio no objeto `mutex`.  
  
##  <a name="a-nameuniquelockunlockmethoda--unlock"></a><a name="unique_lock__unlock_method"></a>  unlock  
 Libera a propriedade do `mutex` associado.  
  
```cpp  
void unlock();
```  
  
### <a name="remarks"></a>Comentários  
 Se o thread de chamada não possui `mutex` associado, esse método lança um [system_error](../standard-library/system-error-class.md) que tem um código de erro de `operation_not_permitted`.  
  
 Caso contrário, esse método chama `unlock` no `mutex` associado e define o sinalizador de propriedade do thread interno para `false`.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Arquivos de Cabeçalho](../standard-library/cpp-standard-library-header-files.md)   
 [\<mutex>](../standard-library/mutex.md)



