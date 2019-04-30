---
title: Classe slice_array
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice_array
helpviewer_keywords:
- slice_array class
ms.assetid: a182d5f7-f35c-4e76-86f2-b5ac64ddc846
ms.openlocfilehash: 9577447b2201c1c9e53192b99abad1979f45d15f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412534"
---
# <a name="slicearray-class"></a>Classe slice_array

Uma classe de modelo auxiliar interna, que dá suporte a objetos de fatia fornecendo operações entre matrizes de subconjunto definidas pela fatia de um valarray.

## <a name="syntax"></a>Sintaxe

```cpp
template <class Type>
class slice_array : public slice {
public:
    typedef Type value_type;
    void operator=(const valarray<Type>& x) const;
    void operator=(const Type& x) const;
    void operator*=(const valarray<Type>& x) const;
    void operator/=(const valarray<Type>& x) const;
    void operator%=(const valarray<Type>& x) const;
    void operator+=(const valarray<Type>& x) const;
    void operator-=(const valarray<Type>& x) const;
    void operator^=(const valarray<Type>& x) const;
    void operator&=(const valarray<Type>& x) const;
    void operator|=(const valarray<Type>& x) const;
    void operator<<=(const valarray<Type>& x) const;
    void operator>>=(const valarray<Type>& x) const;
    // The rest is private or implementation defined
}
```

## <a name="remarks"></a>Comentários

A classe descreve um objeto que armazena uma referência a um objeto da classe [valarray](../standard-library/valarray-class.md)**\<Type>**, bem como um objeto da classe [slice](../standard-library/slice-class.md), que descreve a sequência de elementos a serem selecionados do objeto **valarray\<Type>**.

A classe de modelo é criada indiretamente por determinadas operações de valarray e não pode ser usada diretamente no programa. Uma classe de modelo auxiliar interna que é usada pelo operador de subscrito da slice:

`slice_array`\<**Type**> `valarray`< **Type**:: `operator[]` ( `slice`).

Você constrói uma `slice_array<Type>` objeto apenas escrevendo uma expressão do formulário [va&#91;sl&#93;](../standard-library/valarray-class.md#op_at), para uma fatia `sl` de valarray `va`. As funções de membro da classe gslice_array, em seguida, se comportam como as assinaturas de função correspondentes definidas para `valarray<Type>`, exceto que somente a sequência de elementos selecionados ser afetada. A sequência controlada por slice_array é definida pelos três parâmetros do construtor de slice, o índice do primeiro elemento na slice, o número de elementos e a distância entre os elementos. Um slice_array recortado de valarray `va` declarado pelo **va**[ `slice`(2, 5, 3)] seleciona elementos com índices 2, 5, 8, 11 e 14 do `va`. Os índices devem ser válidos para que o procedimento seja válido.

## <a name="example"></a>Exemplo

Veja o exemplo de [slice::slice](../standard-library/slice-class.md#slice) para obter um exemplo de como declarar e usar um slice_array.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<valarray>

**Namespace:** std

## <a name="see-also"></a>Consulte também

[Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
