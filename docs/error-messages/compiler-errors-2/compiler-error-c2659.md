---
title: Erro do compilador C2659
ms.date: 11/04/2016
f1_keywords:
- C2659
helpviewer_keywords:
- C2659
ms.assetid: b0883600-4d27-4ca7-a931-8ca6bd48654d
ms.openlocfilehash: 1b44ef825626f60e9ae6c6e8600953959fcd7b3a
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449236"
---
# <a name="compiler-error-c2659"></a>Erro do compilador C2659

'operador' : função como operando esquerdo

Uma função estava no lado esquerdo do operador especificado. O motivo mais comum para esse erro é que o compilador analisou o identificador no lado esquerdo do operador como função quando o desenvolvedor pretendia que ele fosse uma variável. Para obter mais informações, consulte Wikipedia artigo [parse mais complicado](https://en.wikipedia.org/wiki/Most_vexing_parse). Este exemplo mostra uma declaração de função e uma definição de variável a são facilmente confundidas:

```
// C2659a.cpp
// Compile using: cl /W4 /EHsc C2659a.cpp
#include <string>
using namespace std;

int main()
{
   string string1(); // string1 is a function returning string
   string string2{}; // string2 is a string initialized to empty

   string1 = "String 1"; // C2659
   string2 = "String 2";
}
```

Para resolver esse problema, altere a declaração do identificador de modo que não ela não seja analisada como uma declaração de função.

O erro C2659 também pode ocorrer quando a função tem um tipo que não pode ser usado na expressão no lado esquerdo do operador especificado. Este exemplo gera C2659 quando o código atribui um ponteiro de função para uma função:

```
// C2659b.cpp
// Compile using: cl /W4 /EHsc C2659b.cpp
int func0(void) { return 42; }
int (*func1)(void);

int main()
{
   func1 = func0;
   func0 = func1; // C2659
}
```