---
title: Classe hash_compare
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_compare
helpviewer_keywords:
- hash_compare class
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
ms.openlocfilehash: 399b412c41128f513cf01d1e034bad2bbc5ef79f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448802"
---
# <a name="hashcompare-class"></a>Classe hash_compare

A classe de modelo descreve um objeto que pode ser usado por qualquer um dos contêineres associativos de hash — hash_map, hash_multimap, hash_set ou hash_multiset — como um objeto de parâmetro **Traits** padrão para ordenar e fazer o hash dos elementos que eles contêm.

## <a name="syntax"></a>Sintaxe

class hash_compare { Traits comp; public: const size_t bucket_size = 4; const size_t min_buckets = 8; hash_compare(); hash_compare(Traits pred); size_t operator()(const Key& key) const; bool operator()( const Key& key1, const Key& key2) const; };

## <a name="remarks"></a>Comentários

Cada contêiner associativo de hash armazena um objeto de características de hash `Traits` do tipo (um parâmetro de modelo). Você pode derivar uma classe de uma especialização de hash_compare para substituir seletivamente determinadas funções e objetos ou pode fornecer sua própria versão dessa classe se atender a certos requisitos mínimos. Especificamente, para um objeto hash_comp do tipo `hash_compare<Key, Traits>`, o seguinte comportamento é exigido pelos contêineres acima:

- Para todos os `key` valores do `Key`tipo, a chamada hash_comp`key`() serve como uma função de hash, que produz uma distribuição de valores do `size_t`tipo. A função fornecida por hash_compare retorna `key`.

- Para qualquer valor `key1` do tipo `Key` que precede `key2` na sequência e tenha o mesmo valor de hash (valor retornado pela função de hash), **hash_comp**(`key2`, `key1`) é false. A função deve impor uma ordenação total em valores do `Key`tipo. A função fornecida por hash_compare retorna *comp*(`key2`, `key1`) `,` em que *comp* é um objeto armazenado do `Traits` tipo que você pode especificar ao construir o objeto hash_comp. Para o tipo `Traits` `less<Key>`de parâmetro padrão, as chaves de classificação nunca diminuem em valor.

- A constante `bucket_size` de inteiro especifica o número médio de elementos por "Bucket" (entrada de tabela de hash) que o contêiner deve tentar não exceder. Ela deve ser maior que zero. O valor fornecido por hash_compare é 4.

- A constante `min_buckets` de inteiro especifica o número mínimo de buckets a serem mantidos na tabela de hash. Ela deve ser uma potência de dois e maior que zero. O valor fornecido por hash_compare é 8.

## <a name="example"></a>Exemplo

Veja exemplos de [hash_map::hash_map](../standard-library/hash-map-class.md#hash_map), [hash_multimap::hash_multimap](../standard-library/hash-multimap-class.md#hash_multimap), [hash_set::hash_set](../standard-library/hash-set-class.md#hash_set) e [hash_multiset::hash_multiset](../standard-library/hash-multiset-class.md#hash_multiset), para ver exemplos de como declarar e usar hash_compare.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<hash_map>

**Namespace:** stdext

## <a name="see-also"></a>Consulte também

[Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referência da biblioteca padrão C++](../standard-library/cpp-standard-library-reference.md)
