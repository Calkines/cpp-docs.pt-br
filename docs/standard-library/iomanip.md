---
title: '&lt;iomanip&gt;'
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
ms.openlocfilehash: b9da0de64bbb0ef48a6a9741ff941e6abda0e705
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449206"
---
# <a name="ltiomanipgt"></a>&lt;iomanip&gt;

Inclua o `iostreams` cabeçalho \<padrão iomanip > para definir vários manipuladores que usam um único argumento.

## <a name="syntax"></a>Sintaxe

```cpp
#include <iomanip>
```

## <a name="remarks"></a>Comentários

Cada um desses manipuladores retorna um tipo não especificado, chamado `T1` por `T10`meio \<de, que sobrecarrega o `basic_istream`operador **elem**, **TR**>`::`[> >](../standard-library/istream-operators.md#op_gt_gt) e `basic_ostream` **Elem,** [operador](../standard-library/ostream-operators.md#op_lt_lt) **TR**<<.> \<`::`

### <a name="manipulators"></a>Manipuladores

|||
|-|-|
|[get_money](../standard-library/iomanip-functions.md#iomanip_get_money)|Obtém um valor monetário, que pode estar no formato internacional.|
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|Obtém uma hora em uma estrutura de horas usando um formato especificado.|
|[put_money](../standard-library/iomanip-functions.md#iomanip_put_money)|Fornece um valor monetário, que pode estar no formato internacional.|
|[put_time](../standard-library/iomanip-functions.md#iomanip_put_time)|Fornece uma hora em uma estrutura de horas e uma cadeia de caracteres de formato para ser usada.|
|[quoted](../standard-library/iomanip-functions.md#quoted)|Permite o ciclo conveniente de cadeias de caracteres, com operadores de inserção e extração.|
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|Limpa os sinalizadores especificados.|
|[setbase](../standard-library/iomanip-functions.md#setbase)|Define a base para inteiros.|
|[setfill](../standard-library/iomanip-functions.md#setfill)|Define o caractere que será usado para preencher espaços em uma exibição justificada à direita.|
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|Define os sinalizadores especificados.|
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|Define a precisão dos valores de ponto flutuante.|
|[setw](../standard-library/iomanip-functions.md#setw)|Especifica a largura do campo de exibição.|

## <a name="see-also"></a>Consulte também

[Referência de Arquivos de Cabeçalho](../standard-library/cpp-standard-library-header-files.md)\
[Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programação de iostream](../standard-library/iostream-programming.md)\
[Convenções de iostreams](../standard-library/iostreams-conventions.md)
