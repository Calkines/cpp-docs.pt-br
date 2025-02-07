---
title: numérico (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/numeric>
- cliext::accumulate
- cliext::adjacent_difference
- cliext::inner_product
- cliext::partial_sum
helpviewer_keywords:
- numeric functions [STL/CLR]
- <cliext/numeric> header [STL/CLR]
- <numeric> header [STL/CLR]
- accumulate function [STL/CLR]
- adjacent_difference function [STL/CLR]
- inner_product function [STL/CLR]
- partial_sum function [STL/CLR]
ms.assetid: 1dc4d9a3-e734-459c-9678-5d9be0ef4c79
ms.openlocfilehash: 0311b36ec1190631e053eeade443939703e69103
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384797"
---
# <a name="numeric-stlclr"></a>numérico (STL/CLR)

Define as funções de modelo do contêiner que executam algoritmos fornecidos para processamento numérico.

## <a name="syntax"></a>Sintaxe

```
#include <cliext/numeric>
```

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<cliext/numeric >

**Namespace:** cliext

## <a name="declarations"></a>Declarações

|Função|Descrição|
|--------------|-----------------|
|[accumulate (STL/CLR)](#accumulate)|Calcula a soma de todos os elementos em um intervalo especificado, incluindo qualquer valor inicial ao calcular somas parciais sucessivas ou calcula o resultado de resultados parciais sucessivos obtidos usando uma operação binária especificada diferente da soma.|
|[adjacent_difference (STL/CLR)](#adjacent_difference)|Calcula as diferenças sucessivas entre cada elemento e seu predecessor em um intervalo de entrada e gera os resultados em um intervalo de destino ou calcula o resultado de um procedimento generalizado, em que a operação de diferença é substituída por outra operação binária especificada.|
|[inner_product (STL/CLR)](#inner_product)|Calcula a soma do produto em relação ao elemento de dois intervalos e a adiciona a um valor inicial especificado ou calcula o resultado de um procedimento generalizado, em que as operações binárias de produto e a soma são substituídas por outras operações binárias especificadas.|
|[partial_sum (STL/CLR)](#partial_sum)|Calcula uma série de somas em um intervalo de entrada do primeiro elemento por meio de `i`º elemento e armazena o resultado de cada soma no `i`-ésimo elemento de um intervalo de destino ou calcula o resultado de um procedimento generalizado, em que a operação de soma é substituída por outra operação binária especificada.|

## <a name="members"></a>Membros

## <a name="accumulate"></a> Acumular (STL/CLR)

Calcula a soma de todos os elementos em um intervalo especificado, incluindo qualquer valor inicial ao calcular somas parciais sucessivas ou calcula o resultado de resultados parciais sucessivos obtidos usando uma operação binária especificada diferente da soma.

### <a name="syntax"></a>Sintaxe

```cpp
template<class _InIt, class _Ty> inline
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);
template<class _InIt, class _Ty, class _Fn2> inline
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);
```

### <a name="remarks"></a>Comentários

Essa função se comporta da mesma que a função de biblioteca padrão C++ numérica `accumulate`. Para obter mais informações, consulte [acumular](../standard-library/numeric-functions.md#accumulate).

## <a name="adjacent_difference"></a> adjacent_difference (STL/CLR)

Calcula as diferenças sucessivas entre cada elemento e seu predecessor em um intervalo de entrada e gera os resultados em um intervalo de destino ou calcula o resultado de um procedimento generalizado, em que a operação de diferença é substituída por outra operação binária especificada.

### <a name="syntax"></a>Sintaxe

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,
        _OutIt _Dest);
template<class _InIt, class _OutIt, class _Fn2> inline
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Comentários

Essa função se comporta da mesma que a função de biblioteca padrão C++ numérica `adjacent_difference`. Para obter mais informações, consulte [adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference).

## <a name="inner_product"></a> inner_product (STL/CLR)

Calcula a soma do produto em relação ao elemento de dois intervalos e a adiciona a um valor inicial especificado ou calcula o resultado de um procedimento generalizado, em que as operações binárias de produto e a soma são substituídas por outras operações binárias especificadas.

### <a name="syntax"></a>Sintaxe

```cpp
template<class _InIt1, class _InIt2, class _Ty> inline
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Ty _Val);
template<class _InIt1, class _InIt2, class _Ty, class _Fn21,
       class _Fn22> inline
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Ty _Val, _Fn21 _Func1, _Fn22 _Func2);
```

### <a name="remarks"></a>Comentários

Essa função se comporta da mesma que a função de biblioteca padrão C++ numérica `inner_product`. Para obter mais informações, consulte [inner_product](../standard-library/numeric-functions.md#inner_product).

## <a name="partial_sum"></a> partial_sum (STL/CLR)

Calcula uma série de somas em um intervalo de entrada do primeiro elemento por meio de `i`º elemento e armazena o resultado de cada soma no `i`-ésimo elemento de um intervalo de destino ou calcula o resultado de um procedimento generalizado, em que a operação de soma é substituída por outra operação binária especificada.

### <a name="syntax"></a>Sintaxe

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);
template<class _InIt, class _OutIt, class _Fn2> inline
    _OutIt partial_sum(_InIt _First, _InIt _Last,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Comentários

Essa função se comporta da mesma que a função de biblioteca padrão C++ numérica `partial_sum`. Para obter mais informações, consulte [partial_sum](../standard-library/numeric-functions.md#partial_sum).