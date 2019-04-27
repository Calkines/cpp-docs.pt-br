---
title: Usando matrizes (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C++]
ms.assetid: 7818a7fe-7e82-4881-a3d1-7d25162b7fc7
ms.openlocfilehash: 7f7a987a2b4c18e59dd058ccfc4375c304188398
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152731"
---
# <a name="using-arrays-c"></a>Usando matrizes (C++)

Você pode acessar elementos individuais de uma matriz usando o operador de subscrito de matriz (`[ ]`). Se uma matriz unidimensional for usada em uma expressão que não tenha subscritos, o nome da matriz será avaliado como um ponteiro para o primeiro elemento da matriz.

```cpp
// using_arrays.cpp
int main() {
   char chArray[10];
   char *pch = chArray;   // Evaluates to a pointer to the first element.
   char   ch = chArray[0];   // Evaluates to the value of the first element.
   ch = chArray[3];   // Evaluates to the value of the fourth element.
}
```

Ao usar matrizes multidimensionais, você pode usar diversas combinações em expressões.

```cpp
// using_arrays_2.cpp
// compile with: /EHsc /W1
#include <iostream>
using namespace std;
int main() {
   double multi[4][4][3];   // Declare the array.
   double (*p2multi)[3];
   double (*p1multi);

   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.
   p2multi = multi[3];               // Make p2multi point to
                                     // fourth "plane" of multi.
   p1multi = multi[3][2];            // Make p1multi point to
                                     // fourth plane, third row
                                     // of multi.
}
```

No código anterior, `multi` é uma matriz tridimensional do tipo **duplo**. O `p2multi` ponteiro aponta para uma matriz do tipo **duplo** de tamanho três. Nesse exemplo, a matriz é usada com um, dois e três subscritos. Embora seja mais comum especificar todos os subscritos, como na instrução `cout`, às vezes, é útil selecionar um subconjunto específico de elementos da matriz, como mostrado nas instruções que se seguem a `cout`.

## <a name="see-also"></a>Consulte também

[Matrizes](../cpp/arrays-cpp.md)