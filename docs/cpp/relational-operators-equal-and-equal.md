---
title: 'Operadores relacionais: &lt;, &gt;, &lt;=, e &gt;='
ms.date: 11/04/2016
f1_keywords:
- <
- '>'
helpviewer_keywords:
- '> operator'
- less than operator
- relational operators [C++], syntax
- '>= operator'
- greater than or equal to operators [C++]
- greater than operators [C++]
- < operator
- less than or equal to operator
- <= operator
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
ms.openlocfilehash: 52a3c10e6da42f6c181d3f93de13168e22141bec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458949"
---
# <a name="relational-operators-lt-gt-lt-and-gt"></a>Operadores relacionais: &lt;, &gt;, &lt;=, e &gt;=

## <a name="syntax"></a>Sintaxe

```
expression < expression
expression > expression
expression <= expression
expression >= expression
```

## <a name="remarks"></a>Comentários

Os operadores relacionais binários determinam as seguintes relações:

- Menor que (**\<**)

- Maior que (**>**)

- Menor ou igual a (**\<=**)

- Maior que ou igual a (**>=**)

Esses operadores relacionais possuem associatividade da esquerda para a direita. Ambos os operandos de operadores relacionais devem ser do tipo aritmético ou de ponteiro. Eles resultam em valores do tipo **bool**. O valor retornado será **falsos** (0) se a relação na expressão for false; caso contrário, o valor retornado é **verdadeiro** (1).

## <a name="example"></a>Exemplo

```cpp
// expre_Relational_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << "The true expression 3 > 2 yields: "
         << (3 > 2) << endl
         << "The false expression 20 < 10 yields: "
         << (20 < 10) << endl;
}
```

As expressões no exemplo anterior devem ser incluídas em parênteses porque o operador de inserção de fluxo (**<<**) tem precedência maior do que os operadores relacionais. Portanto, a primeira expressão sem parênteses seria avaliada como:

```cpp
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");
```

As conversões aritméticas usuais abordadas [conversões padrão](standard-conversions.md) são aplicadas aos operandos de tipos aritméticos.

## <a name="comparing-pointers"></a>Comparando ponteiros

Quando dois ponteiros para objetos do mesmo tipo são comparados, o resultado é determinado pelo local dos objetos apontados no espaço de endereço do programa. Ponteiros também podem ser comparados a uma expressão constante que é avaliada como 0 ou um ponteiro de tipo `void *`. Se uma comparação de ponteiros é feita em relação a um ponteiro de tipo `void *`, o outro ponteiro é implicitamente convertido para o tipo `void *`. Então, a comparação será feita.

Dois ponteiros de tipos diferentes não podem ser comparados, a menos que:

- Um tipo é um tipo de classe derivado de outro tipo.

- Pelo menos um dos ponteiros é convertido explicitamente (conversão) no tipo `void *`. (O outro ponteiro é implicitamente convertido para o tipo `void *` para a conversão.)

Dois ponteiros do mesmo tipo que apontam para o mesmo objeto são obrigatoriamente comparados como iguais. Se dois ponteiros para membros não estáticos de um objeto são comparados, as seguintes regras se aplicam:

- Se o tipo de classe não é um **união**, e se os dois membros não são separados por uma *especificador de acesso*, como **público**, **protegido**, ou **privada**, o ponteiro para o membro declarado por último será comparado maior que o ponteiro para o membro declarado anteriormente.

- Se os dois membros são separados por um *especificador de acesso*, os resultados são indefinidos.

- Se o tipo de classe for um **união**, ponteiros para membros de dados diferentes em que **união** comparados igualmente.

Se dois ponteiros apontarem para elementos da mesma matriz ou para o elemento além do final da matriz, o ponteiro para o objeto com o subscrito mais alto será comparado como superior. A comparação dos ponteiros é garantida como válida somente quando os ponteiros se referem a objetos na mesma matriz ou ao local após o término da matriz.

## <a name="see-also"></a>Consulte também

[Expressões com operadores binários](../cpp/expressions-with-binary-operators.md)<br/>
[Operadores internos, precedência e associatividade C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores relacionais e de igualdade C](../c-language/c-relational-and-equality-operators.md)