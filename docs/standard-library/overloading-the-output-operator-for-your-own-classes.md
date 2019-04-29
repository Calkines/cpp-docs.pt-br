---
title: Sobrecarregando o operador &lt;&lt; para as suas próprias classes
ms.date: 11/04/2016
helpviewer_keywords:
- operator<<, overloading for your own classes
- operator <<, overloading for your own classes
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
ms.openlocfilehash: 290491f7afb22873d60abb6662b470d8e7abefc1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370678"
---
# <a name="overloading-the-ltlt-operator-for-your-own-classes"></a>Sobrecarregando o operador &lt;&lt; para as suas próprias classes

Fluxos de saída usam o operador de inserção (`<<`) para os tipos padrão. Você também pode sobrecarregar o operador `<<` para suas próprias classes.

## <a name="example"></a>Exemplo

O exemplo de função `write` mostrou o uso de uma estrutura `Date`. Uma data é um candidato ideal para uma classe C++ na qual os membros de dados (mês, dia e ano) ficam ocultos. Um fluxo de saída é o destino lógico para a exibição dessa estrutura. Esse código exibe uma data usando o objeto `cout`:

```cpp
Date dt(1, 2, 92);

cout <<dt;
```

Para obter `cout` para aceitar um objeto `Date` após o operador de inserção, sobrecarregue o operador de inserção para reconhecer um objeto `ostream` à esquerda e um `Date` à direita. A função de operador `<<` sobrecarregada deve ser declarada como um amiga da classe `Date` para que possa acessar os dados privados dentro de um objeto `Date`.

```cpp
// overload_date.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class Date
{
    int mo, da, yr;
public:
    Date(int m, int d, int y)
    {
        mo = m; da = d; yr = y;
    }
    friend ostream& operator<<(ostream& os, const Date& dt);
};

ostream& operator<<(ostream& os, const Date& dt)
{
    os << dt.mo << '/' << dt.da << '/' << dt.yr;
    return os;
}

int main()
{
    Date dt(5, 6, 92);
    cout << dt;
}
```

```Output
5/6/92
```

## <a name="remarks"></a>Comentários

O operador sobrecarregado retorna uma referência ao objeto `ostream` original, o que significa que é possível combinar as inserções:

```cpp
cout <<"The date is" <<dt <<flush;
```

## <a name="see-also"></a>Consulte também

[Fluxos de saída](../standard-library/output-streams.md)<br/>
