---
title: Classe concurrent_unordered_map | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::at
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::hash_function
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::insert
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::key_eq
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::swap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::unsafe_erase
dev_langs:
- C++
helpviewer_keywords:
- concurrent_unordered_map class
ms.assetid: b2d879dd-87ef-4af9-a266-a5443fd538b8
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: e5b8af640c48630c6c2c132a10b160bb85c39380
ms.lasthandoff: 03/17/2017

---
# <a name="concurrentunorderedmap-class"></a>Classe concurrent_unordered_map
O `concurrent_unordered_map` classe é um contêiner de prova de simultaneidade que controla uma sequência de comprimento variado de elementos do tipo `std::pair<const K, _Element_type>`. A sequência é representada de forma que permite a prova de simultaneidade acrescentar, acesso de elemento, acesso de iterador e operações de passagem do iterador.  
  
## <a name="syntax"></a>Sintaxe  
  
```
template <typename K,
    typename _Element_type,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>
>,
 typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>> class concurrent_unordered_map : public details::_Concurrent_hash<details::_Concurrent_unordered_map_traits<K,
    _Element_type,
 details::_Hash_compare<K,
    _Hasher,
 key_equality>,
    _Allocator_type,
 false>>;
```  
  
#### <a name="parameters"></a>Parâmetros  
 `K`  
 O tipo principal.  
  
 `_Element_type`  
 O tipo mapeado.  
  
 `_Hasher`  
 O tipo de objeto da função de hash. Esse argumento é opcional e o valor padrão é `std::hash<``K``>`.  
  
 `key_equality`  
 O tipo de objeto da função de comparação de igualdade. Esse argumento é opcional e o valor padrão é `std::equal_to<``K``>`.  
  
 `_Allocator_type`  
 O tipo que representa o objeto de alocador armazenado que encapsula detalhes sobre a alocação e desalocação de memória para o mapa não ordenado simultânea. Esse argumento é opcional e o valor padrão é `std::allocator<std::pair<``K`, `_Element_type``>>`.  
  
## <a name="members"></a>Membros  
  
### <a name="public-typedefs"></a>Typedefs públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|`allocator_type`|O tipo de um distribuidor para gerenciar o armazenamento.|  
|`const_iterator`|O tipo de um iterador de constante para a sequência controlada.|  
|`const_local_iterator`|O tipo de um iterador de bucket de constante para a sequência controlada.|  
|`const_pointer`|O tipo de um ponteiro de constante para um elemento.|  
|`const_reference`|O tipo de uma referência de constante para um elemento.|  
|`difference_type`|O tipo de uma distância com sinal entre dois elementos.|  
|`hasher`|O tipo de função de hash.|  
|`iterator`|O tipo de um iterador para a sequência controlada.|  
|`key_equal`|O tipo da função de comparação.|  
|`key_type`|O tipo de uma chave de classificação.|  
|`local_iterator`|O tipo de um iterador de bucket para a sequência controlada.|  
|`mapped_type`|O tipo de um valor mapeado associado a cada chave.|  
|`pointer`|O tipo de um ponteiro para um elemento.|  
|`reference`|O tipo de uma referência para um elemento.|  
|`size_type`|O tipo de uma distância sem sinal entre dois elementos.|  
|`value_type`|O tipo de um elemento.|  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[concurrent_unordered_map](#ctor)|Sobrecarregado. Constrói um mapa não ordenado simultâneo.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[at](#at)|Sobrecarregado. Localiza um elemento em um `concurrent_unordered_map` com um valor de chave especificado. Esse método é uma prova de simultaneidade.|  
|[hash_function](#hash_function)|Obtém o objeto armazenado da função de hash.|  
|[insert](#insert)|Sobrecarregado. Adiciona elementos para o `concurrent_unordered_map` objeto.|  
|[key_eq](#key_eq)|Obtém o objeto de função de comparação de igualdade armazenado.|  
|[swap](#swap)|Troca o conteúdo dos dois `concurrent_unordered_map` objetos. Esse método não é uma prova de simultaneidade.|  
|[unsafe_erase](#unsafe_erase)|Sobrecarregado. Remove elementos do `concurrent_unordered_map` em posições especificadas. Esse método não é uma prova de simultaneidade.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[operador]](#operator_at)|Sobrecarregado. Localiza ou insere um elemento com a chave especificada. Esse método é uma prova de simultaneidade.|  
|[operator=](#operator_eq)|Sobrecarregado. Atribui o conteúdo de outro `concurrent_unordered_map` objeto a este. Esse método não é uma prova de simultaneidade.|  
  
## <a name="remarks"></a>Comentários  
 Para obter informações detalhadas sobre o `concurrent_unordered_map` classe, consulte [paralela contêineres e objetos](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 `_Traits`  
  
 `_Concurrent_hash`  
  
 `concurrent_unordered_map`  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** concurrent_unordered_map.h  
  
 **Namespace:** simultaneidade  
  
##  <a name="at"></a>em 

 Localiza um elemento em um `concurrent_unordered_map` com um valor de chave especificado. Esse método é uma prova de simultaneidade.  
  
```
mapped_type& at(const key_type& KVal);

const mapped_type& at(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `KVal`  
 O valor de chave a ser localizado.  
  
### <a name="return-value"></a>Valor de retorno  
 Uma referência ao valor de dados do elemento encontrado.  
  
### <a name="remarks"></a>Comentários  
 Se o valor da chave de argumento não for encontrado, a função gera um objeto da classe `out_of_range`.  
  
##  <a name="begin"></a>começar 

 Retorna um iterador apontando para o primeiro elemento no contêiner simultâneo. Esse método é seguro de simultaneidade.  
  
```
iterator begin();

const_iterator begin() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um iterador para o primeiro elemento no contêiner simultâneo.  
  
##  <a name="cbegin"></a>cbegin 

 Retorna um iterador const que aponta para o primeiro elemento no contêiner simultâneo. Esse método é seguro de simultaneidade.  
  
```
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um iterador const para o primeiro elemento no contêiner simultâneo.  
  
##  <a name="cend"></a>cend 

 Retorna um iterador const apontando para o local após o último elemento no contêiner simultâneo. Esse método é seguro de simultaneidade.  
  
```
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um iterador const para o local após o último elemento no contêiner simultâneo.  
  
##  <a name="clear"></a>Limpar 

 Apaga todos os elementos no contêiner simultâneo. Essa função não é seguro de simultaneidade.  
  
```
void clear();
```  
  
##  <a name="ctor"></a>concurrent_unordered_map 

 Constrói um mapa não ordenado simultâneo.  
  
```
explicit concurrent_unordered_map(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_map(_Iterator _Begin,
    _Iterator _End,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap);

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap,
    const allocator_type& _Allocator);

concurrent_unordered_map(
    concurrent_unordered_map&& _Umap);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Iterator`  
 O tipo do iterador de entrada.  
  
 `_Number_of_buckets`  
 O número inicial de buckets para esse mapa não ordenado.  
  
 `_Hasher`  
 A função de hash para este mapa não ordenado.  
  
 `key_equality`  
 A função de comparação de igualdade para esse mapa não ordenado.  
  
 `_Allocator`  
 O alocador para esse mapa não ordenado.  
  
 `_Begin`  
 A posição do primeiro elemento no intervalo de elementos a serem copiados.  
  
 `_End`  
 A posição do primeiro elemento além do intervalo de elementos a serem copiados.  
  
 `_Umap`  
 A fonte `concurrent_unordered_map` copiar ou mover elementos de objeto.  
  
### <a name="remarks"></a>Comentários  
 Todos os construtores armazenam um objeto alocador `_Allocator` e inicializar o mapa não ordenado.  
  
 O primeiro construtor Especifica um mapa inicial vazio e explicitamente Especifica o número de buckets, tipo de função de hash, função de igualdade e alocador a ser usado.  
  
 O segundo construtor Especifica um alocador para o mapa não ordenado.  
  
 O terceiro construtor especifica valores fornecidos pelo intervalo iterador [ `_Begin`, `_End`).  
  
 Os construtores quarto e quinto especificam uma cópia do mapa não ordenado simultânea `_Umap`.  
  
 O último construtor Especifica uma movimentação do mapa não ordenado simultânea `_Umap`.  
  
##  <a name="count"></a>Contagem 

 Conta o número de elementos que correspondem a uma chave especificada. Essa função é seguro de simultaneidade.  
  
```
size_type count(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `KVal`  
 A chave para pesquisar.  
  
### <a name="return-value"></a>Valor de retorno  
 O número de vezes o número de vezes que a chave é exibida no contêiner.  
  
##  <a name="empty"></a>vazio 

 Testa se nenhum elemento está presente. Esse método é seguro de simultaneidade.  
  
```
bool empty() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 `true`Se o contêiner simultâneo estiver vazio, `false` caso contrário.  
  
### <a name="remarks"></a>Comentários  
 Na presença de inserções simultâneas, ou não o contêiner simultâneo está vazio pode alterar imediatamente depois de chamar essa função, antes que o valor de retorno é ler.  
  
##  <a name="end"></a>final 

 Retorna um iterador apontando para o local após o último elemento no contêiner simultâneo. Esse método é seguro de simultaneidade.  
  
```
iterator end();

const_iterator end() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um iterador para o local após o último elemento no contêiner simultâneo.  
  
##  <a name="equal_range"></a>equal_range 

 Localiza um intervalo que corresponde a uma chave especificada. Essa função é seguro de simultaneidade.  
  
```
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `KVal`  
 O valor da chave para pesquisar.  
  
### <a name="return-value"></a>Valor de retorno  
 A [par](http://msdn.microsoft.com/en-us/c5a37023-d939-4eb2-ae24-ce8e0cd4505d) onde o primeiro elemento é um iterador para o início e o segundo elemento é um iterador para o final do intervalo.  
  
### <a name="remarks"></a>Comentários  
 É possível para inserções simultâneas fazer com que as chaves adicionais a serem inseridos após o iterador inicial e antes do iterador de fim.  
  
##  <a name="find"></a>localizar 

 Localiza um elemento que corresponde a uma chave especificada. Essa função é seguro de simultaneidade.  
  
```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `KVal`  
 O valor da chave para pesquisar.  
  
### <a name="return-value"></a>Valor de retorno  
 Um iterador apontando para o local do primeiro elemento que corresponde à chave fornecida ou o iterador `end()` se esse elemento não existir.  
  
##  <a name="get_allocator"></a>get_allocator 

 Retorna o objeto de alocador armazenado para esse contêiner simultânea. Esse método é seguro de simultaneidade.  
  
```
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 O objeto de alocador armazenado para esse contêiner simultânea.  
  
##  <a name="hash_function"></a>hash_function 

 Obtém o objeto armazenado da função de hash.  
  
```
hasher hash_function() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 O objeto de função de hash armazenado.  
  
##  <a name="insert"></a>Inserir 

 Adiciona elementos para o `concurrent_unordered_map` objeto.  
  
```
std::pair<iterator,
    bool> insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
std::pair<iterator,
    bool> insert(
    V&& value);

template<class V>
typename std::enable_if<!std::is_same<const_iterator,
    typename std::remove_reference<V>::type>::value,
    iterator>::type insert(
    const_iterator _Where,
    V&& value);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Iterator`  
 O tipo de iterador usado para inserção.  
  
 `V`  
 O tipo do valor inserido no mapa.  
  
 `value`  
 O valor a ser inserido.  
  
 `_Where`  
 O local inicial para procurar por um ponto de inserção.  
  
 `first`  
 O início do intervalo para inserir.  
  
 `last`  
 O final do intervalo para inserir.  
  
### <a name="return-value"></a>Valor de retorno  
 Um par que contém um iterador e um valor booleano. Consulte a seção de comentários para obter mais detalhes.  
  
### <a name="remarks"></a>Comentários  
 A primeira função de membro determina se um elemento X existe na sequência cuja chave tem ordenação equivalente do `value`. Se não, ele cria tal elemento X e o inicializa com `value`. A função determina o iterador `where` que designa X. Se ocorreu uma inserção, a função retornará `std::pair(where, true)`. Caso contrário, retornará `std::pair(where, false)`.  
  
 A segunda função de membro retorna insert ( `value`), usando `_Where` como um ponto de partida na sequência controlada para procurar o ponto de inserção.  
  
 A terceira função de membro insere a sequência de valores de elemento do intervalo [ `first`, `last`).  
  
 As funções de membro de dois últimos se comportam da mesma maneira como os dois primeiros, exceto que `value` é usado para construir o valor inserido.  
  
##  <a name="key_eq"></a>key_eq 

 Obtém o objeto de função de comparação de igualdade armazenado.  
  
```
key_equal key_eq() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 O objeto de função de comparação de igualdade armazenado.  
  
##  <a name="load_factor"></a>load_factor 

 Calcula e retorna o fator de carga atual do contêiner. O fator de carga é o número de elementos no contêiner dividido pelo número de buckets.  
  
```
float load_factor() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 O fator de carga para o contêiner.  
  
##  <a name="max_load_factor"></a>max_load_factor 

 Obtém ou define o fator de carga máxima do contêiner. O fator de carga máxima é o maior número de elementos que podem estar em qualquer bucket antes do contêiner aumenta sua tabela interna.  
  
```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Newmax`  
  
### <a name="return-value"></a>Valor de retorno  
 A primeira função membro retorna o fator de carga máxima armazenado. A segunda função de membro não retorna um valor, mas lança um [out_of_range](../../../standard-library/out-of-range-class.md) exceção se o fator de carga fornecido é inválido.  
  
##  <a name="max_size"></a>max_size 

 Retorna o tamanho máximo do contêiner simultâneo, determinado pelo alocador. Esse método é seguro de simultaneidade.  
  
```
size_type max_size() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 O número máximo de elementos que podem ser inseridas neste contêiner simultâneo.  
  
### <a name="remarks"></a>Comentários  
 Esse valor de limite superior, na verdade, pode ser maior que o contêiner pode realmente manter.  
  
##  <a name="operator_at"></a>operador] 

 Localiza ou insere um elemento com a chave especificada. Esse método é uma prova de simultaneidade.  
  
```
mapped_type& operator[](const key_type& kval);

mapped_type& operator[](key_type&& kval);
```  
  
### <a name="parameters"></a>Parâmetros  
 `KVal`  
 O valor da chave para  
  
 localizar ou inserir.  
  
### <a name="return-value"></a>Valor de retorno  
 Uma referência ao valor dos dados do elemento encontrado ou inserido.  
  
### <a name="remarks"></a>Comentários  
 Se o valor de chave do argumento não for encontrado, ele será inserido juntamente com o valor padrão do tipo de dados.  
  
 `operator[]`pode ser usado para inserir elementos em um mapa `m` usando `m[key] = DataValue;`, onde `DataValue` é o valor da `mapped_type` do elemento com um valor de chave de `key`.  
  
 Ao usar `operator[]` para inserir elementos, a referência retornada não indica se uma inserção está alterando um elemento preexistente ou criando outro. As funções de membro `find` e [inserir](#insert) pode ser usado para determinar se um elemento com uma chave especificada já está presente antes de uma inserção.  
  
##  <a name="operator_eq"></a>operador = 

 Atribui o conteúdo de outro `concurrent_unordered_map` objeto a este. Esse método não é uma prova de simultaneidade.  
  
```
concurrent_unordered_map& operator= (const concurrent_unordered_map& _Umap);

concurrent_unordered_map& operator= (concurrent_unordered_map&& _Umap);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Umap`  
 A fonte `concurrent_unordered_map` objeto.  
  
### <a name="return-value"></a>Valor de retorno  
 Uma referência a esta `concurrent_unordered_map` objeto.  
  
### <a name="remarks"></a>Comentários  
 Depois de apagar os elementos de um vetor simultâneo, `operator=` copia ou move o conteúdo de `_Umap` para o vetor simultâneo.  
  
##  <a name="rehash"></a>rehash 

 Recria a tabela de hash.  
  
```
void rehash(size_type _Buckets);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Buckets`  
 O número de buckets desejado.  
  
### <a name="remarks"></a>Comentários  
 A função membro altera o número de buckets para que seja pelo menos `_Buckets` e recria a tabela de hash, conforme necessário. O número de buckets deve ser uma potência de 2. Se não é uma potência de 2, ele será arredondado para a próxima maior potência de 2.  
  
 Ele gera um [out_of_range](../../../standard-library/out-of-range-class.md) exceção se o número de buckets é inválido (0 ou maior que o número máximo de segmentos).  
  
##  <a name="size"></a>tamanho 

 Retorna o número de elementos neste contêiner simultâneas. Esse método é seguro de simultaneidade.  
  
```
size_type size() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 O número de itens no contêiner.  
  
### <a name="remarks"></a>Comentários  
 Na presença de inserções simultâneas, o número de elementos no contêiner simultâneo pode alterar imediatamente depois de chamar essa função, antes que o valor de retorno é ler.  
  
##  <a name="swap"></a>troca 

 Troca o conteúdo dos dois `concurrent_unordered_map` objetos. Esse método não é uma prova de simultaneidade.  
  
```
void swap(concurrent_unordered_map& _Umap);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Umap`  
 O `concurrent_unordered_map` objeto para troca.  
  
##  <a name="unsafe_begin"></a>unsafe_begin 

 Retorna um iterador para o primeiro elemento neste contêiner para um bloco específico.  
  
```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Bucket`  
 O índice de bucket.  
  
### <a name="return-value"></a>Valor de retorno  
 Um iterador apontando para o início da partição.  
  
##  <a name="unsafe_bucket"></a>unsafe_bucket 

 Retorna o índice de bucket que mapeia uma chave específica neste contêiner.  
  
```
size_type unsafe_bucket(const key_type& KVal) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `KVal`  
 A chave do elemento que está sendo pesquisada.  
  
### <a name="return-value"></a>Valor de retorno  
 O índice de bucket para a chave neste contêiner.  
  
##  <a name="unsafe_bucket_count"></a>unsafe_bucket_count 

 Retorna o número atual de buckets neste contêiner.  
  
```
size_type unsafe_bucket_count() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 O número atual de buckets neste contêiner.  
  
##  <a name="unsafe_bucket_size"></a>unsafe_bucket_size 

 Retorna o número de itens em um bloco específico desse contêiner.  
  
```
size_type unsafe_bucket_size(size_type _Bucket);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Bucket`  
 O bucket para pesquisar.  
  
### <a name="return-value"></a>Valor de retorno  
 O número atual de buckets neste contêiner.  
  
##  <a name="unsafe_cbegin"></a>unsafe_cbegin 

 Retorna um iterador para o primeiro elemento neste contêiner para um bloco específico.  
  
```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Bucket`  
 O índice de bucket.  
  
### <a name="return-value"></a>Valor de retorno  
 Um iterador apontando para o início da partição.  
  
##  <a name="unsafe_cend"></a>unsafe_cend 

 Retorna um iterador para o local após o último elemento em um bloco específico.  
  
```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Bucket`  
 O índice de bucket.  
  
### <a name="return-value"></a>Valor de retorno  
 Um iterador apontando para o início da partição.  
  
##  <a name="unsafe_end"></a>unsafe_end 

 Retorna um iterador para o último elemento neste contêiner para um bloco específico.  
  
```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Bucket`  
 O índice de bucket.  
  
### <a name="return-value"></a>Valor de retorno  
 Um iterador apontando para o final da partição.  
  
##  <a name="unsafe_erase"></a>unsafe_erase 

 Remove elementos do `concurrent_unordered_map` em posições especificadas. Esse método não é uma prova de simultaneidade.  
  
```
iterator unsafe_erase(
    const_iterator _Where);

iterator unsafe_erase(
    const_iterator _Begin,
    const_iterator _End);

size_type unsafe_erase(
    const key_type& KVal);
```  
  
### <a name="parameters"></a>Parâmetros  
 `_Where`  
 A posição do iterador para apagar da.  
  
 `_Begin`  
 A posição do primeiro elemento no intervalo de elementos a serem apagados.  
  
 `_End`  
 A posição do primeiro elemento além do intervalo de elementos a serem apagados.  
  
 `KVal`  
 O valor da chave para apagar.  
  
### <a name="return-value"></a>Valor de retorno  
 As funções de membro de dois primeiro retornam um iterador que designa o primeiro elemento restante além de quaisquer elementos removidos, ou `concurrent_unordered_map::end`() se esse elemento não existir. A terceira função de membro retorna o número de elementos remove.  
  
### <a name="remarks"></a>Comentários  
 A primeira função de membro remove o elemento da sequência controlada apontada por `_Where`. A segunda função de membro remove os elementos no intervalo [ `_Begin`, `_End`).  
  
 A terceira função de membro remove os elementos no intervalo delimitado por `concurrent_unordered_map::equal_range`(KVal).  
  
##  <a name="unsafe_max_bucket_count"></a>unsafe_max_bucket_count 

 Retorna o número máximo de buckets neste contêiner.  
  
```
size_type unsafe_max_bucket_count() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 O número máximo de buckets neste contêiner.  
  
## <a name="see-also"></a>Consulte também  
 [Namespace de simultaneidade](concurrency-namespace.md)   
 [Contêineres e objetos em paralelo](../../../parallel/concrt/parallel-containers-and-objects.md)



