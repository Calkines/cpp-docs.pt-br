---
title: Funções &lt;hash_map&gt;
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: efaa960d91c69d2157896adb4612c5dd36f00cff
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448740"
---
# <a name="lthashmapgt-functions"></a>Funções &lt;hash_map&gt;

|||
|-|-|
|[swap](#swap)|[swap (hash_map)](#swap_hash_map)|

## <a name="swap_hash_map"></a>  swap (hash_map)

> [!NOTE]
> Esta API está obsoleta. A alternativa é a [Classe unordered_map](../standard-library/unordered-map-class.md).

Troca os elementos de dois hash_maps.

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*Certo*\
O hash_map cujos elementos devem ser trocados por aqueles do mapa *à esquerda*.

*mantida*\
O hash_map cujos elementos devem ser trocados por aqueles do mapa *direito*.

### <a name="remarks"></a>Comentários

A função de modelo é um algoritmo especializado na classe de contêiner hash_map para executar a função membro `left.`[swap](../standard-library/basic-ios-class.md#swap) *(right*). Trata-se de uma instância da ordenação parcial de modelos de função pelo compilador. Quando as funções de modelo são sobrecarregadas de forma que a correspondência do modelo com a chamada de função não é exclusiva, o compilador seleciona a versão mais especializada do modelo de função. A versão geral da função de modelo, **template \<class T> void swap(T&, T&)** , no arquivo de cabeçalho do algoritmo funciona por atribuição e é uma operação lenta. A versão especializada em cada contêiner é muito mais rápida, uma vez que ela pode funcionar com a representação interna da classe de contêiner.

## <a name="swap"></a>  swap

> [!NOTE]
> Esta API está obsoleta. A alternativa é a [Classe unordered_multimap](../standard-library/unordered-multimap-class.md).

Troca os elementos de dois hash_multimaps.

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parâmetros

*Certo*\
O hash_multimap cujos elementos devem ser trocados por aqueles do mapa *à esquerda*.

*mantida*\
O hash_multimap cujos elementos devem ser trocados por aqueles do mapa *direito*.

### <a name="remarks"></a>Comentários

A função de modelo é um algoritmo especializado na classe de contêiner hash_multimap para executar a função de membro `left.`[swap](../standard-library/hash-multimap-class.md#swap) *(right*`)`. Trata-se de uma instância da ordenação parcial de modelos de função pelo compilador. Quando as funções de modelo são sobrecarregadas de forma que a correspondência do modelo com a chamada de função não é exclusiva, o compilador seleciona a versão mais especializada do modelo de função. A versão geral da função de modelo, **template \<class T> void swap(T&, T&)** , no arquivo de cabeçalho do algoritmo funciona por atribuição e é uma operação lenta. A versão especializada em cada contêiner é muito mais rápida, uma vez que ela pode funcionar com a representação interna da classe de contêiner.

## <a name="see-also"></a>Consulte também

[<hash_map>](../standard-library/hash-map.md)
