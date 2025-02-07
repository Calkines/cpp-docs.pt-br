---
title: Enumerações &lt;limits&gt;
ms.date: 11/04/2016
f1_keywords:
- limits/std::float_denorm_style
- limits/std::float_round_style
ms.assetid: c86680a2-ba97-4ed9-8c20-a448857d7dc5
ms.openlocfilehash: 567e0538f59c40d57f85d652a8919be6e034cf0b
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245350"
---
# <a name="ltlimitsgt-enums"></a>Enumerações &lt;limits&gt;

## <a name="float_denorm_style"></a> float_denorm_style

A enumeração descreve os vários métodos que uma implementação pode escolher para representar um valor de ponto flutuante desnormalizado — um pequeno demais para ser representado como um valor normalizado:

```cpp
enum float_denorm_style {
    denorm_indeterminate = -1,
    denorm_absent = 0,
    denorm_present = 1    };
```

### <a name="return-value"></a>Valor de retorno

A enumeração retornará:

- `denorm_indeterminate` Se a presença ou ausência de formas desnormalizadas não puder ser determinada em tempo de tradução.

- `denorm_absent` Se formas desnormalizadas estiverem ausentes.

- `denorm_present` Se formas desnormalizadas estiverem presentes.

### <a name="example"></a>Exemplo

Consulte [numeric_limits::has_denorm](../standard-library/numeric-limits-class.md#has_denorm) para ver um exemplo em que os valores da enumeração podem ser acessados.

## <a name="float_round_style"></a> float_round_style

A enumeração descreve os vários métodos que uma implementação pode escolher para fazer o arredondamento de um valor de ponto flutuante para um valor inteiro.

```cpp
enum float_round_style {
    round_indeterminate = -1,
    round_toward_zero = 0,
    round_to_nearest = 1,
    round_toward_infinity = 2,
    round_toward_neg_infinity = 3    };
```

### <a name="return-value"></a>Valor de retorno

A enumeração retornará:

- `round_indeterminate` Se o método de arredondamento não puder ser determinado.

- `round_toward_zero` Se o arredondamento em direção a zero.

- `round_to_nearest` Se o arredondamento para o inteiro mais próximo.

- `round_toward_infinity` Se o arredondamento diferente de zero.

- `round_toward_neg_infinity` Se o arredondamento para o inteiro mais negativo.

### <a name="example"></a>Exemplo

Consulte [numeric_limits::round_style](../standard-library/numeric-limits-class.md#round_style) para ver um exemplo em que os valores da enumeração podem ser acessados.
