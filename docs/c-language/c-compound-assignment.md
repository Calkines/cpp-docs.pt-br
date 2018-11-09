---
title: Atribuição composta C
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
ms.openlocfilehash: 102f53378430074a59636eb18488a7ab51289731
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50445130"
---
# <a name="c-compound-assignment"></a>Atribuição composta C

Os operadores de atribuição composta combinam o operador de atribuição simples com outro operador binário. Os operadores de atribuição composta executam a operação especificada pelo operador adicional e, em seguida, atribuem o resultado ao operando esquerdo. Por exemplo, uma expressão de atribuição composta, como

> *expression1* **+=** *expression2*

pode ser entendida como

> *expression1* **=** *expression1* **+** *expression2*

No entanto, a expressão de atribuição composta não é equivalente à versão expandida porque a expressão de atribuição composta avalia *expression1* apenas uma vez, enquanto a versão expandida avalia *expression1* duas vezes: na operação de adição e na operação de atribuição.

Os operandos de um operador de atribuição composta devem ser do tipo integral ou flutuação. Cada operador de atribuição composta executa as conversões que o operador binário correspondente executa e restringe os tipos de seus operandos de acordo. Os operadores de atribuição de adição (`+=`) e de subtração (**-=**) também podem ter um operando esquerdo do tipo ponteiro. Nesse caso, o operando direito deve ser do tipo integral. O resultado de uma operação de atribuição composta tem o valor e o tipo do operando esquerdo.

```C
#define MASK 0xff00

n &= MASK;
```

Neste exemplo, a operação AND inclusivo bit a bit é executada em `n` e em `MASK`, e o resultado é atribuído a `n`. A constante de manifesto `MASK` é definida com uma diretiva do pré-processador [#define](../preprocessor/hash-define-directive-c-cpp.md).

## <a name="see-also"></a>Consulte também

[Operadores de atribuição C](../c-language/c-assignment-operators.md)