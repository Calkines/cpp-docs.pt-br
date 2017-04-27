---
title: Classe scoped_allocator_adaptor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.scoped_allocator_adaptor
- scoped_allocator_adaptor
- scoped_allocator/std::scoped_allocator_adaptor
- std::scoped_allocator_adaptor
dev_langs:
- C++
helpviewer_keywords:
- scoped_allocator_adaptor Class
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
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
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: f4c343592c2c767d52a66091ecca5b1bd4ae9e88
ms.lasthandoff: 02/25/2017

---
# <a name="scopedallocatoradaptor-class"></a>Classe scoped_allocator_adaptor
Representa um aninhamento de alocadores.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
template <class Outer, class... Inner>  
class scoped_allocator_adaptor;  
```  
  
## <a name="remarks"></a>Comentários  
 A classe de modelo encapsula um aninhamento um ou mais alocadores de. Cada classe desse tipo tem um alocador mais externo do tipo `outer_allocator_type`, um sinônimo de `Outer`, que é uma base pública do objeto `scoped_allocator_adaptor`. `Outer` é usado para alocar memória para ser usada por um contêiner. Você pode obter uma referência a esse objeto base do alocador chamando `outer_allocator`.  
  
 O restante do aninhamento tem tipo `inner_allocator_type`. Um alocador interno é usado para alocar memória para elementos dentro de um contêiner. Você pode obter uma referência para o objeto armazenado desse tipo chamando `inner_allocator`. Se `Inner...` não está vazio, `inner_allocator_type` tem tipo `scoped_allocator_adaptor<Inner...>` e `inner_allocator` designa um objeto de membro. Caso contrário, `inner_allocator_type` tem tipo `scoped_allocator_adaptor<Outer>` e `inner_allocator` designa o objeto inteiro.  
  
 O aninhamento se comporta como se tivesse profundidade arbitrária, replicando seu alocador encapsulado mais interno, conforme necessário.  
  
 Vários conceitos que não fazem parte da interface visível ajudam a descrever o comportamento dessa classe de modelo. Um *alocador mais externo* media todas as chamadas para os métodos construct e destroy. Ele é definido efetivamente pela função recursiva `OUTERMOST(X)`, em que `OUTERMOST(X)` é um dos seguintes.  
  
-   Se `X.outer_allocator()` for bem formado, `OUTERMOST(X)` será `OUTERMOST(X.outer_allocator())`.  
  
-   Caso contrário, `OUTERMOST(X)` é `X`.  
  
 Três tipos são definidos para fins de exposição:  
  
|Tipo|Descrição|  
|----------|-----------------|  
|`Outermost`|O tipo de `OUTERMOST(*this)`.|  
|`Outermost_traits`|`allocator_traits<Outermost>`|  
|`Outer_traits`|`allocator_traits<Outer>`|  
  
### <a name="constructors"></a>Construtores  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Construtor scoped_allocator_adaptor::scoped_allocator_adaptor](#scoped_allocator_adaptor__scoped_allocator_adaptor_constructor)|Constrói um objeto `scoped_allocator_adaptor`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|Nome|Descrição|  
|----------|-----------------|  
|`const_pointer`|Esse tipo é um sinônimo do `const_pointer` que está associado com o alocador `Outer`.|  
|`const_void_pointer`|Esse tipo é um sinônimo do `const_void_pointer` que está associado com o alocador `Outer`.|  
|`difference_type`|Esse tipo é um sinônimo do `difference_type` que está associado com o alocador `Outer`.|  
|`inner_allocator_type`|Esse tipo é um sinônimo do tipo do adaptador aninhado `scoped_allocator_adaptor<Inner...>`.|  
|`outer_allocator_type`|Esse tipo é um sinônimo do tipo do alocador base `Outer`.|  
|`pointer`|Esse tipo é um sinônimo do `pointer` associado com o alocador `Outer`.|  
|`propagate_on_container_copy_assignment`|O tipo é true somente se `Outer_traits::propagate_on_container_copy_assignment` for true ou `inner_allocator_type::propagate_on_container_copy_assignment` for true.|  
|`propagate_on_container_move_assignment`|O tipo é true somente se `Outer_traits::propagate_on_container_move_assignment` for true ou `inner_allocator_type::propagate_on_container_move_assignment` for true.|  
|`propagate_on_container_swap`|O tipo é true somente se `Outer_traits::propagate_on_container_swap` for true ou `inner_allocator_type::propagate_on_container_swap` for true.|  
|`size_type`|Esse tipo é um sinônimo do `size_type` associado com o alocador `Outer`.|  
|`value_type`|Esse tipo é um sinônimo do `value_type` associado com o alocador `Outer`.|  
|`void_pointer`|Esse tipo é um sinônimo do `void_pointer` associado com o alocador `Outer`.|  
  
### <a name="structs"></a>Structs  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Struct scoped_allocator_adaptor::rebind](#scoped_allocator_adaptor__rebind_struct)|Define o tipo `Outer::rebind\<Other>::other` como um sinônimo de `scoped_allocator_adaptor\<Other, Inner...>`.|  
  
### <a name="methods"></a>Métodos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[Método scoped_allocator_adaptor::allocate](#scoped_allocator_adaptor__allocate_method)|Aloca memória usando o alocador `Outer`.|  
|[Método scoped_allocator_adaptor::construct](#scoped_allocator_adaptor__construct_method)|Cria um objeto.|  
|[Método scoped_allocator_adaptor::deallocate](#scoped_allocator_adaptor__deallocate_method)|Desaloca objetos usando o alocador externo.|  
|[Método scoped_allocator_adaptor::destroy](#scoped_allocator_adaptor__destroy_method)|Destrói um objeto especificado.|  
|[Método scoped_allocator_adaptor::inner_allocator](#scoped_allocator_adaptor__inner_allocator_method)|Recupera uma referência ao objeto armazenado do tipo `inner_allocator_type`.|  
|[Método scoped_allocator_adaptor::max_size](#scoped_allocator_adaptor__max_size_method)|Determina o número máximo de objetos que podem ser alocados pelo alocador externo.|  
|[Método scoped_allocator_adaptor::outer_allocator](#scoped_allocator_adaptor__outer_allocator_method)|Recupera uma referência ao objeto armazenado do tipo `outer_allocator_type`.|  
|[Método scoped_allocator_adaptor::select_on_container_copy_construction](#scoped_allocator_adaptor__select_on_container_copy_construction_method)|Cria um novo objeto `scoped_allocator_adaptor` com cada objeto de alocador armazenado inicializado, por meio da chamada de `select_on_container_copy_construction` para cada alocador correspondente.|  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** \<scoped_allocator>  
  
 **Namespace:** std  
  
##  <a name="a-namescopedallocatoradaptorallocatemethoda--scopedallocatoradaptorallocate-method"></a><a name="scoped_allocator_adaptor__allocate_method"></a> Método scoped_allocator_adaptor::allocate  
 Aloca memória usando o alocador `Outer`.  
  
```cpp  
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```  
  
### <a name="parameters"></a>Parâmetros  
 `count`  
 O número de elementos para os quais um armazenamento suficiente deve ser alocado.  
  
 `hint`  
 Um ponteiro que pode ajudar o objeto alocador localizando o endereço de um objeto alocado antes da solicitação.  
  
### <a name="return-value"></a>Valor de retorno  
 A primeira função membro retorna `Outer_traits::allocate(outer_allocator(), count)`. A segunda função membro retorna `Outer_traits::allocate(outer_allocator(), count, hint)`.  
  
##  <a name="a-namescopedallocatoradaptorconstructmethoda--scopedallocatoradaptorconstruct-method"></a><a name="scoped_allocator_adaptor__construct_method"></a> Método scoped_allocator_adaptor::construct  
 Cria um objeto.  
  
```cpp  
template <class Ty, class... Atypes>  
void construct(Ty* ptr, Atypes&&... args);

template <class Ty1, class Ty2, class... Atypes1, class... Atypes2>  
void construct(pair<Ty1, Ty2>* ptr, piecewise_construct_t,  
    tuple<Atypes1&&...>  
first, tuple<Atypes1&&...> second);

template <class Ty1, class Ty2>  
void construct(pair<Ty1, Ty2>* ptr);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr,  
    class Uy1&& first, class Uy2&& second);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr, const pair<Uy1, Uy2>& right);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr, pair<Uy1, Uy2>&& right);
```  
  
### <a name="parameters"></a>Parâmetros  
 `ptr`  
 Um ponteiro para o local da memória em que o objeto deve ser criado.  
  
 `args`  
 Uma lista de argumentos.  
  
 `first`  
 Um objeto do primeiro tipo em um par.  
  
 `second`  
 Um objeto do segundo tipo em um par.  
  
 `right`  
 Um objeto existente a ser movido ou copiado.  
  
### <a name="remarks"></a>Comentários  
 O primeiro método cria o objeto em `ptr` chamando `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)`, em que `xargs...` é um dos mostrados a seguir.  
  
-   Se `uses_allocator<Ty, inner_allocator_type>` contém false, `xargs...` é `args...`.  
  
-   Se `uses_allocator<Ty, inner_allocator_type>` for true e `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` for true, então `xargs...` será `allocator_arg, inner_allocator(), args...`.  
  
-   Se `uses_allocator<Ty, inner_allocator_type>` for true e `is_constructible<Ty, args..., inner_allocator()>` for true, então `xargs...` será `args..., inner_allocator()`.  
  
 O segundo método cria o objeto par em `ptr` chamando `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)`, em que `xargs...` é `first...` modificado assim como na lista acima; além disso, cria `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)`, em que `xargs...` é `second...` modificado assim como na lista acima.  
  
 O terceiro método se comporta da mesma maneira que `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)`.  
  
 O quarto método se comporta da mesma maneira que `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))`.  
  
 O quinto método se comporta da mesma maneira que `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))`.  
  
 O sexto método se comporta da mesma maneira que `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))`.  
  
##  <a name="a-namescopedallocatoradaptordeallocatemethoda--scopedallocatoradaptordeallocate-method"></a><a name="scoped_allocator_adaptor__deallocate_method"></a> Método scoped_allocator_adaptor::deallocate  
 Desaloca objetos usando o alocador externo.  
  
```cpp  
void deallocate(pointer ptr, size_type count);
```  
  
### <a name="parameters"></a>Parâmetros  
 `ptr`  
 Um ponteiro para o local inicial dos objetos a serem desalocados.  
  
 `count`  
 O número de objetos a serem desalocados.  
  
##  <a name="a-namescopedallocatoradaptordestroymethoda--scopedallocatoradaptordestroy-method"></a><a name="scoped_allocator_adaptor__destroy_method"></a> Método scoped_allocator_adaptor::destroy  
 Destrói um objeto especificado.  
  
```cpp  
template <class Ty>  
void destroy(Ty* ptr)  
```  
  
### <a name="parameters"></a>Parâmetros  
 `ptr`  
 Um ponteiro para o objeto a ser destruído.  
  
### <a name="return-value"></a>Valor de retorno  
 `Outermost_traits::destroy(OUTERMOST(*this), ptr)`  
  
##  <a name="a-namescopedallocatoradaptorinnerallocatormethoda--scopedallocatoradaptorinnerallocator-method"></a><a name="scoped_allocator_adaptor__inner_allocator_method"></a> Método scoped_allocator_adaptor::inner_allocator  
 Recupera uma referência ao objeto armazenado do tipo `inner_allocator_type`.  
  
```cpp  
inner_allocator_type& inner_allocator() noexcept;  
const inner_allocator_type& inner_allocator() const noexcept;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 Uma referência ao objeto armazenado do tipo `inner_allocator_type`.  
  
##  <a name="a-namescopedallocatoradaptormaxsizemethoda--scopedallocatoradaptormaxsize-method"></a><a name="scoped_allocator_adaptor__max_size_method"></a> Método scoped_allocator_adaptor::max_size  
 Determina o número máximo de objetos que podem ser alocados pelo alocador externo.  
  
```cpp  
size_type max_size();
```  
  
### <a name="return-value"></a>Valor de retorno  
 `Outer_traits::max_size(outer_allocator())`  
  
##  <a name="a-namescopedallocatoradaptorouterallocatormethoda--scopedallocatoradaptorouterallocator-method"></a><a name="scoped_allocator_adaptor__outer_allocator_method"></a> Método scoped_allocator_adaptor::outer_allocator  
 Recupera uma referência ao objeto armazenado do tipo `outer_allocator_type`.  
  
```cpp  
outer_allocator_type& outer_allocator() noexcept;  
const outer_allocator_type& outer_allocator() const noexcept;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 Uma referência ao objeto armazenado do tipo `outer_allocator_type`.  
  
##  <a name="a-namescopedallocatoradaptorrebindstructa--scopedallocatoradaptorrebind-struct"></a><a name="scoped_allocator_adaptor__rebind_struct"></a> Struct scoped_allocator_adaptor::rebind  
 Define o tipo `Outer::rebind\<Other>::other` como um sinônimo de `scoped_allocator_adaptor\<Other, Inner...>`.  
  
struct rebind{  
   typedef Other_traits::rebind\<Other>  
   Other_alloc;  
   typedef scoped_allocator_adaptor\<Other_alloc, Inner...> other;  
   };  
  
##  <a name="a-namescopedallocatoradaptorscopedallocatoradaptorconstructora--scopedallocatoradaptorscopedallocatoradaptor-constructor"></a><a name="scoped_allocator_adaptor__scoped_allocator_adaptor_constructor"></a> Construtor scoped_allocator_adaptor::scoped_allocator_adaptor  
 Constrói um objeto `scoped_allocator_adaptor`.  
  
```cpp  
scoped_allocator_adaptor();

scoped_allocator_adaptor(const scoped_allocator_adaptor& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(
 const scoped_allocator_adaptor<Outer2, Inner...>& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(
 scoped_allocator_adaptor<Outer2, Inner...>&& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(Outer2&& al,  
    const Inner&... rest) noexcept;  
```  
  
### <a name="parameters"></a>Parâmetros  
 `right`  
 Um `scoped_allocator_adaptor` existente.  
  
 `al`  
 Um alocador existente a ser usado como o alocador externo.  
  
 `rest`  
 Um alocador existente a ser usado como os alocadores internos.  
  
### <a name="remarks"></a>Comentários  
 O primeiro padrão de construtor cria seus objetos de alocador armazenado. Cada um dos três constructos de construtor seguintes cria seus objetos de alocador armazenado dos objetos correspondentes em `right`. O último construtor cria seus objetos de alocador armazenado dos argumentos correspondentes na lista de argumentos.  
  
##  <a name="a-namescopedallocatoradaptorselectoncontainercopyconstructionmethoda--scopedallocatoradaptorselectoncontainercopyconstruction-method"></a><a name="scoped_allocator_adaptor__select_on_container_copy_construction_method"></a> Método scoped_allocator_adaptor::select_on_container_copy_construction  
 Cria um novo objeto `scoped_allocator_adaptor` com cada objeto de alocador armazenado inicializado, por meio da chamada de `select_on_container_copy_construction` para cada alocador correspondente.  
  
```cpp  
scoped_allocator_adaptor select_on_container_copy_construction();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Esse método retorna efetivamente `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`. O resultado é um novo objeto `scoped_allocator_adaptor` com cada objeto de alocador armazenado inicializado, por meio da chamada de `al.select_on_container_copy_construction()` para o alocador `al` correspondente.  
  
## <a name="see-also"></a>Consulte também  
 [Referência de Arquivos de Cabeçalho](../standard-library/cpp-standard-library-header-files.md)



