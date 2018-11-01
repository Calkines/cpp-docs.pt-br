---
title: Atribuição
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], assignment
- assignment operators [C++], overloaded
ms.assetid: d87e4f89-f8f5-42c1-9d3c-184bca9d0e15
ms.openlocfilehash: 1e6d715011cfaab7e250e23a9a31bb3f0c83f36a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603419"
---
# <a name="assignment"></a>Atribuição

O operador de atribuição (**=**) é, estritamente falando, um operador binário. Sua declaração é idêntica a qualquer outro operador binário, com as seguintes exceções:

- Ele deve ser uma função de membro não estático. Não **operador =** pode ser declarado como uma função não membro.
- Ele não é herdado por classes derivadas.
- Um padrão **operador =** função pode ser gerada pelo compilador para tipos de classe, se não houver nenhum.

O exemplo a seguir ilustra como declarar um operador de atribuição:

```cpp
class Point
{
public:
    int _x, _y;

    // Right side of copy assignment is the argument.
    Point& operator=(const Point&);
};

// Define copy assignment operator.
Point& Point::operator=(const Point& otherPoint)
{
    _x = otherPoint._x;
    _y = otherPoint._y;

    // Assignment operator returns left side of assignment.
    return *this;
}

int main()
{
    Point pt1, pt2;
    pt1 = pt2;
}
```

O argumento fornecido é o lado direito da expressão. O operador retorna o objeto para preservar o comportamento do operador de atribuição, que retorna o valor do lado esquerdo após a conclusão da atribuição. Isso permite que o encadeamento de atribuições, tais como:

```cpp
pt1 = pt2 = pt3;
```

É o operador de atribuição de cópia não deve ser confundido com o construtor de cópia. O último é chamado durante a construção de um novo objeto de uma já existente:

```cpp
// Copy constructor is called--not overloaded copy assignment operator!
Point pt3 = pt1;

// The previous initialization is similar to the following:
Point pt4(pt1); // Copy constructor call.
```

> [!NOTE]
> É recomendável seguir a [regra de três](https://en.wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming)) que uma classe que define um operador de atribuição de cópia deve definir explicitamente o construtor de cópia, destruidor e, começando com o c++11, atribuição de movimentação de construtor e mover operador.

## <a name="see-also"></a>Consulte também

- [Sobrecarga de Operador](../cpp/operator-overloading.md)
- [Operadores de construtores de cópia e de atribuição de cópia (C++)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)