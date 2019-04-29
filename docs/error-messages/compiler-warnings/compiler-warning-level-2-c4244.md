---
title: Compilador aviso (nível 2) C4244
ms.date: 11/04/2016
f1_keywords:
- C4244
helpviewer_keywords:
- C4244
ms.assetid: 2c19d157-21d1-42c2-a6c0-3f30f2ce3813
ms.openlocfilehash: af821d80ff8c4c7717986f2ff4d0f3392cd6fca3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349718"
---
# <a name="compiler-warning-level-2-c4244"></a>Compilador aviso (nível 2) C4244

'argumento': conversão de 'type1' em 'type2', possível perda de dados

Um tipo de ponto flutuante foi convertido em um tipo inteiro.  Uma possível perda de dados pode ter ocorrido.

Se você receber C4244, você deve alterar seu programa usar tipos compatíveis ou adicionar alguma lógica ao seu código, para garantir que o intervalo de valores possíveis sempre será compatível com os tipos que você está usando.

Também pode ser acionado C4244 no nível 3 e 4; ver [aviso do compilador (níveis 3 e 4) C4244](../../error-messages/compiler-warnings/compiler-warning-levels-3-and-4-c4244.md) para obter mais informações.

## <a name="example"></a>Exemplo

O exemplo a seguir gera C4244:

```
// C4244_level2.cpp
// compile with: /W2

int f(int x){ return 0; }
int main() {
   double x = 10.1;
   int i = 10;
   return (f(x));   // C4244
   // try the following line instead
   // return (f(i));
}
```