---
title: Expressões de constante C++
ms.date: 11/04/2016
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
ms.openlocfilehash: 97059066adadc3a7897cbd2c4c747e2a673e7201
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576417"
---
# <a name="c-constant-expressions"></a>Expressões de constante C++

Um *constante* valor é um que não é alterada. C++ fornece duas palavras-chave para que você possa expressar a intenção de que um objeto não se destina a ser modificado e para forçar essa intenção.

O C++ requer expressões constantes — expressões que são avaliadas como uma constante — para declarações de:

- Limites de matriz

- Seletores em instruções case

- Especificação de comprimento do campo de bits

- Inicializadores de enumeração

Os únicos operandos que são válidos em expressões constantes são:

- Literais

- Constantes de enumeração

- Valores declarados como const que são inicializados com expressões constantes

- **sizeof** expressões

As constantes não integral devem ser convertidas (explicitamente ou implicitamente) em tipos integrais para serem válidas em uma expressão constante. Portanto, o código a seguir é válido:

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

Conversões explícitas em tipos integrais são válidas em expressões constantes; todos os outros tipos e tipos derivados são inválidos, exceto quando usados como operandos para o **sizeof** operador.

O operador vírgula e os operadores de atribuição não podem ser usados em expressões constantes.

## <a name="see-also"></a>Consulte também

[Tipos de expressões](../cpp/types-of-expressions.md)