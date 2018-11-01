---
title: Classe CRBMap
ms.date: 11/04/2016
f1_keywords:
- CRBMap
- ATLCOLL/ATL::CRBMap
- ATLCOLL/ATL::CRBMap::CRBMap
- ATLCOLL/ATL::CRBMap::Lookup
- ATLCOLL/ATL::CRBMap::RemoveKey
- ATLCOLL/ATL::CRBMap::SetAt
helpviewer_keywords:
- CRBMap class
ms.assetid: 658e94dc-e835-4356-aed1-1513e1f66969
ms.openlocfilehash: fc702feacff5b2f2bbe53a9ea49f664a241d788c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677507"
---
# <a name="crbmap-class"></a>Classe CRBMap

Essa classe representa uma estrutura de mapeamento, usando uma árvore binária de vermelho / preto.

## <a name="syntax"></a>Sintaxe

```
template <typename K,
          typename V,
          class KTraits = CElementTraits<K>,
          class VTraits = CElementTraits<V>>
class CRBMap : public CRBTree<K, V, KTraits, VTraits>
```

#### <a name="parameters"></a>Parâmetros

*K*<br/>
O tipo de elemento-chave.

*V*<br/>
O tipo de elemento de valor.

*KTraits*<br/>
O código usado para copiar ou mover elementos-chave. Ver [classe CElementTraits](../../atl/reference/celementtraits-class.md) para obter mais detalhes.

*VTraits*<br/>
O código usado para copiar ou mover elementos de valor.

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|[CRBMap::CRBMap](#crbmap)|O construtor.|
|[CRBMap:: ~ CRBMap](#dtor)|O destruidor.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CRBMap::Lookup](#lookup)|Chame esse método para pesquisar as chaves ou valores no `CRBMap` objeto.|
|[CRBMap::RemoveKey](#removekey)|Chame esse método para remover um elemento de `CRBMap` objeto, de acordo com a chave.|
|[CRBMap::SetAt](#setat)|Chame esse método para inserir um par de elementos no mapa.|

## <a name="remarks"></a>Comentários

`CRBMap` fornece suporte para uma matriz de mapeamento de qualquer tipo, gerenciando uma matriz ordenada de elementos-chave e seus valores associados. Cada chave pode ter apenas um valor associado. Elementos (consistindo em uma chave e um valor) são armazenados em uma árvore binária estrutura, usando o [CRBMap::SetAt](#setat) método. Elementos podem ser removidos usando o [CRBMap::RemoveKey](#removekey) método, que exclui o elemento com o valor de chave fornecido.

Percorrer a árvore se tornou possível com métodos como [CRBTree::GetHeadPosition](../../atl/reference/crbtree-class.md#getheadposition), [CRBTree::GetNext](../../atl/reference/crbtree-class.md#getnext), e [CRBTree::GetNextValue](../../atl/reference/crbtree-class.md#getnextvalue).

O *KTraits* e *VTraits* parâmetros são classes de características que contém qualquer código complementar necessário para copiar ou mover elementos.

`CRBMap` é derivado de [CRBTree](../../atl/reference/crbtree-class.md), que implementa uma árvore binária usando o algoritmo de vermelho / preto. [CRBMultiMap](../../atl/reference/crbmultimap-class.md) é uma variação que permite vários valores para cada chave. Ela é derivada de muito `CRBTree`e portanto, compartilha muitos recursos com `CRBMap`.

Uma alternativa para ambos `CRBMap` e `CRBMultiMap` é oferecida pela [CAtlMap](../../atl/reference/catlmap-class.md) classe. Quando apenas um pequeno número de elementos precisa ser armazenados, considere o uso de [CSimpleMap](../../atl/reference/csimplemap-class.md) classe em vez disso.

Para obter uma discussão mais completa de várias classes de coleção e seus recursos e características de desempenho, consulte [Classes de coleção ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CRBTree](../../atl/reference/crbtree-class.md)

`CRBMap`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atlcoll.h

##  <a name="crbmap"></a>  CRBMap::CRBMap

O construtor.

```
explicit CRBMap(size_t nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parâmetros

*nBlockSize*<br/>
O tamanho do bloco.

### <a name="remarks"></a>Comentários

O *nBlockSize* parâmetro é uma medida da quantidade de memória alocada quando um novo elemento é necessário. Tamanhos de bloco maiores reduzem chamadas para rotinas de alocação de memória, mas usam mais recursos. O padrão será alocar espaço para 10 elementos por vez.

Consulte a documentação para a classe base [CRBTree](../../atl/reference/crbtree-class.md) para obter informações sobre os métodos disponíveis.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_ATL_Utilities#81](../../atl/codesnippet/cpp/crbmap-class_1.cpp)]

##  <a name="dtor"></a>  CRBMap:: ~ CRBMap

O destruidor.

```
~CRBMap() throw();
```

### <a name="remarks"></a>Comentários

Libera todos os recursos alocados.

Consulte a documentação para a classe base [CRBTree](../../atl/reference/crbtree-class.md) para obter informações sobre os métodos disponíveis.

##  <a name="lookup"></a>  CRBMap::Lookup

Chame esse método para pesquisar as chaves ou valores no `CRBMap` objeto.

```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const throw(...);
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parâmetros

*key*<br/>
Especifica a chave que identifica o elemento a ser pesquisado.

*value*<br/>
Variável que recebe o valor pesquisado.

### <a name="return-value"></a>Valor de retorno

A primeira forma do método retornará true se a chave for encontrada, caso contrário, false. Os formulários de segundo e terceiro retornam um ponteiro para um [CPair](crbtree-class.md#cpair_class).

### <a name="remarks"></a>Comentários

Consulte a documentação para a classe base [CRBTree](../../atl/reference/crbtree-class.md) para obter informações sobre os métodos disponíveis.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_ATL_Utilities#82](../../atl/codesnippet/cpp/crbmap-class_2.cpp)]

##  <a name="removekey"></a>  CRBMap::RemoveKey

Chame esse método para remover um elemento de `CRBMap` objeto, de acordo com a chave.

```
bool RemoveKey(KINARGTYPE key) throw();
```

### <a name="parameters"></a>Parâmetros

*key*<br/>
A chave correspondente para o par de elementos que você deseja remover.

### <a name="return-value"></a>Valor de retorno

Retorna VERDADEIRO se a chave for encontrada e removida, falso em caso de falha.

### <a name="remarks"></a>Comentários

Consulte a documentação para a classe base [CRBTree](../../atl/reference/crbtree-class.md) para obter informações sobre os métodos disponíveis.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_ATL_Utilities#83](../../atl/codesnippet/cpp/crbmap-class_3.cpp)]

##  <a name="setat"></a>  CRBMap::SetAt

Chame esse método para inserir um par de elementos no mapa.

```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value) throw(...);
```

### <a name="parameters"></a>Parâmetros

*key*<br/>
O valor da chave para adicionar ao `CRBMap` objeto.

*value*<br/>
O valor a ser adicionado para o `CRBMap` objeto.

### <a name="return-value"></a>Valor de retorno

Retorna a posição do par chave/valor de elemento no `CRBMap` objeto.

### <a name="remarks"></a>Comentários

`SetAt` substitui um elemento existente, se uma chave correspondente for encontrada. Se a chave não for encontrada, é criado um novo par chave/valor.

Consulte a documentação para a classe base [CRBTree](../../atl/reference/crbtree-class.md) para obter informações sobre os métodos disponíveis.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_ATL_Utilities#84](../../atl/codesnippet/cpp/crbmap-class_4.cpp)]

## <a name="see-also"></a>Consulte também

[Classe CRBTree](../../atl/reference/crbtree-class.md)<br/>
[Classe CAtlMap](../../atl/reference/catlmap-class.md)<br/>
[Classe CRBMultiMap](../../atl/reference/crbmultimap-class.md)<br/>
[Visão geral da classe](../../atl/atl-class-overview.md)
