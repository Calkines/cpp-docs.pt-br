---
title: Classe is_literal_type
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_literal_type
helpviewer_keywords:
- is_literal_type
ms.assetid: a03a4ebb-ee66-48d6-91bb-41cf72b2401f
ms.openlocfilehash: 450c32d050a18f64e71992bd7a30412ebafe93de
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456222"
---
# <a name="isliteraltype-class"></a>Classe is_literal_type

Testa se um tipo pode ser usado como uma variável `constexpr` ou pode ser construído, usado ou retornado de funções `constexpr`.

## <a name="syntax"></a>Sintaxe

```cpp
template <class T>
struct is_literal_type;
```

### <a name="parameters"></a>Parâmetros

*T*\
O tipo a ser consultado.

## <a name="remarks"></a>Comentários

Uma instância do predicado de tipo se manterá true se o tipo *T* for um *tipo literal*, caso contrário, será false. Um tipo literal é **void**, um tipo escalar, um tipo de referência, uma matriz de tipo literal ou um tipo de classe literal. Um tipo de classe literal é um tipo de classe que tem um destruidor trivial, é um tipo agregado ou tem pelo menos construtor `constexpr` que não é de movimentação e não é de cópia, e todas as suas classes base e membros de dados não estáticos são tipos literais não voláteis. Embora o tipo de um literal sempre seja um tipo literal, o conceito de um tipo literal inclui tudo que o compilador puder avaliar como `constexpr` em tempo de compilação.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<type_traits>

**Namespace:** std

## <a name="see-also"></a>Consulte também

[<type_traits>](../standard-library/type-traits.md)
