---
title: Instrução do-while (C++)
ms.date: 11/04/2016
f1_keywords:
- do_cpp
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
ms.openlocfilehash: d930c1884975288ff11f4d4e5cf2728e717e17d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392252"
---
# <a name="do-while-statement-c"></a>Instrução do-while (C++)

Executa um *instrução* repetidamente até que a condição de término especificada (o *expressão*) é avaliada como zero.

## <a name="syntax"></a>Sintaxe

```
do
   statement
while ( expression ) ;
```

## <a name="remarks"></a>Comentários

O teste da condição de término é realizado após cada execução do loop; Portanto, uma **fazer-enquanto** loop é executado uma ou mais vezes, dependendo do valor da expressão de término. A instrução **do-while** também pode terminar quando uma instrução [break](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md) ou [return](../cpp/return-statement-cpp.md) é executada no corpo da instrução.

A *expressão* deve ter o tipo aritmético ou ponteiro. A execução procede da seguinte maneira:

1. O corpo da instrução é executado.

1. Em seguida, a *expressão* é avaliada. Se a *expressão* for falsa, a instrução **do-while** será finalizada e o controle será passado para a próxima instrução no programa. Se a *expressão* for verdadeira (diferente de zero), o processo será repetido, começando da etapa 1.

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra a **fazer-enquanto** instrução:

```cpp
// do_while_statement.cpp
#include <stdio.h>
int main()
{
    int i = 0;
    do
    {
        printf_s("\n%d",i++);
    } while (i < 3);
}
```

## <a name="see-also"></a>Consulte também

[Instruções de iteração](../cpp/iteration-statements-cpp.md)<br/>
[Palavras-chave](../cpp/keywords-cpp.md)<br/>
[Instrução while (C++)](../cpp/while-statement-cpp.md)<br/>
[Instrução for (C++)](../cpp/for-statement-cpp.md)<br/>
[Instrução for baseada intervalo (C++)](../cpp/range-based-for-statement-cpp.md)