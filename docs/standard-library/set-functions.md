---
title: Funções &lt;set&gt;
ms.date: 11/04/2016
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
ms.openlocfilehash: a3a63fb86caa3485b1ee14538c3eb1f1ff72923e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246409"
---
# <a name="ltsetgt-functions"></a>Funções &lt;set&gt;

## <a name="swap"></a> swap (mapa)

Troca os elementos de dois conjuntos.

```cpp
template <class Key, class Traits, class Allocator>
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*Certo*\
O conjunto que fornece os elementos a serem trocados ou o conjunto cujos elementos serão trocados com aqueles do set *esquerdo*.

*À esquerda*\
O set cujos elementos são trocados por aqueles do set *certa*.

### <a name="remarks"></a>Comentários

A função de modelo é um algoritmo especializado na classe de contêiner set para executar a função de membro `left.` [permuta](../standard-library/set-class.md#swap)(`right`). Trata-se de uma instância da ordenação parcial de modelos de função pelo compilador. Quando as funções de modelo são sobrecarregadas de forma que a correspondência do modelo com a chamada de função não é exclusiva, o compilador seleciona a versão mais especializada do modelo de função. A versão geral da função de modelo

`template`\< **classT**> **void swap**( **T&** , **T&** )

na classe de algoritmo funciona por atribuição e é uma operação lenta. A versão especializada em cada contêiner é muito mais rápida, uma vez que ela pode funcionar com a representação interna da classe de contêiner.

### <a name="example"></a>Exemplo

Veja o exemplo de código da classe de membro [set::swap](../standard-library/set-class.md#swap) para obter um exemplo que usa a versão de modelo de `swap`.

## <a name="swap_multiset"></a> swap (Multiconjunto)

Troca os elementos de dois multisets.

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*Certo*\
O multiset que fornece os elementos a serem trocados ou o multiset cujos elementos deverão ser trocados com aqueles do multiset *esquerdo*.

*À esquerda*\
O multiset cujos elementos deverão ser trocados com aqueles do multiset *certa*.

### <a name="remarks"></a>Comentários

A função de modelo é um algoritmo especializado na classe de contêiner multiset para executar a função de membro `left.` [permuta](../standard-library/multiset-class.md#swap)(`right`). Trata-se de uma instância da ordenação parcial de modelos de função pelo compilador. Quando as funções de modelo são sobrecarregadas de forma que a correspondência do modelo com a chamada de função não é exclusiva, o compilador seleciona a versão mais especializada do modelo de função. A versão geral da função de modelo

`template`\< **classT**> **void swap**( **T&** , **T&** )

na classe de algoritmo funciona por atribuição e é uma operação lenta. A versão especializada em cada contêiner é muito mais rápida, uma vez que ela pode funcionar com a representação interna da classe de contêiner.

### <a name="example"></a>Exemplo

Veja o exemplo de código da classe de membro [multiset::swap](../standard-library/multiset-class.md#swap) para obter um exemplo que usa a versão de modelo de `swap`.
