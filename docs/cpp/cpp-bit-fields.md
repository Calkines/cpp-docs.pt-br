---
title: Campos de bit C++
ms.date: 11/19/2018
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
ms.openlocfilehash: 747920378472cc091928a080e303a0543e287aaa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154684"
---
# <a name="c-bit-fields"></a>Campos de bit C++

As classes e as estruturas podem conter membros que ocupam menos armazenamento do que um tipo integral. Esses membros são especificados como campos de bits. A sintaxe para o campo de bits *Declarador de membro* especificação segue:

## <a name="syntax"></a>Sintaxe

*declarator* **:** *constant-expression*

## <a name="remarks"></a>Comentários

(Opcional) *declarador* é o nome pelo qual o membro é acessado no programa. Deve ser um tipo integral (incluindo tipos enumerados). O *expressão-constante* Especifica o número de bits, o membro ocupa na estrutura. Campos de bits anônimos - ou seja, membros de campos de bits sem identificador - podem ser usados para preenchimento.

> [!NOTE]
> Um campo de bits não nomeado de largura 0 força o alinhamento do próximo campo de bits para a próxima **tipo** limite, em que **tipo** é o tipo do membro.

O exemplo a seguir declara uma estrutura que contém campos de bits:

```cpp
// bit_fields1.cpp
// compile with: /LD
struct Date {
   unsigned short nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned short nMonthDay : 6;    // 0..31  (6 bits)
   unsigned short nMonth    : 5;    // 0..12  (5 bits)
   unsigned short nYear     : 8;    // 0..100 (8 bits)
};
```

O layout de memória conceitual de um objeto do tipo `Date` é mostrado na figura a seguir.

![Layout de memória de um objeto date](../cpp/media/vc38uq1.png "layout de memória de um objeto de data") <br/>
Layout de memória de um objeto Date

Observe que `nYear` é o comprimento de 8 bits e estouraria o limite de palavra do tipo declarado, **não assinados** **curto**. Portanto, ele começa no início de uma nova **sem sinal** **curto**. Não é necessário que todos os campos de bits caibam em um mesmo objeto do tipo subjacente; novas unidades de armazenamento são alocadas de acordo com o número de bits solicitados na declaração.

**Seção específica da Microsoft**

A ordenação dos dados declarados como campos de bits vai do bit inferior até o superior, como mostra a figura acima.

**Fim da seção específica da Microsoft**

Se a declaração de uma estrutura inclui um campo não nomeado de comprimento 0, como mostrado no exemplo a seguir,

```cpp
// bit_fields2.cpp
// compile with: /LD
struct Date {
   unsigned nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned nMonthDay : 6;    // 0..31  (6 bits)
   unsigned           : 0;    // Force alignment to next boundary.
   unsigned nMonth    : 5;    // 0..12  (5 bits)
   unsigned nYear     : 8;    // 0..100 (8 bits)
};
```

em seguida, o layout de memória é conforme mostrado na figura a seguir:

![Layout do objeto de data com zero de&#45;campo de bits de comprimento](../cpp/media/vc38uq2.png "objeto de Layout de data com zero&#45;campo de bits de comprimento") <br/>
Layout do objeto Date com campo de bits de comprimento zero

O tipo subjacente de um campo de bits deve ser um tipo integral, conforme descrito em [tipos fundamentais](../cpp/fundamental-types-cpp.md).

Se o inicializador para uma referência de tipo `const T&` é um lvalue que se refere a um campo de bits do tipo `T`, a referência não está associada ao campo de bit diretamente. Em vez disso, a referência está associada a um temporário inicializado para conter o valor do campo de bits.

## <a name="restrictions-on-bit-fields"></a>Restrições em campos de bits

A lista a seguir detalha as operações erradas em campos de bits:

- Obtendo o endereço de um campo de bits.

- Inicializando um não -**const** referência com um campo de bits.

## <a name="see-also"></a>Consulte também

[Classes e Structs](../cpp/classes-and-structs-cpp.md)