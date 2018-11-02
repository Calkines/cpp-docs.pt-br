---
title: friend (C++)
ms.date: 07/02/2018
f1_keywords:
- friend_cpp
helpviewer_keywords:
- member access, from friend functions
- friend classes [C++]
- friend keyword [C++]
ms.assetid: 8fe9ee55-d56f-40cd-9075-d9fb1375aff4
ms.openlocfilehash: 46027692bfa4a7245418ab032168b5b3c107e839
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480516"
---
# <a name="friend-c"></a>friend (C++)

Em algumas circunstâncias, é mais conveniente conceder acesso no nível do membro para as funções que não são membros de uma classe ou a todos os membros em uma classe separada. Somente o implementador de classe pode declarar quem são seus amigos. Uma classe ou função não pode declarar em si como um amigo de qualquer classe. Em uma definição de classe, use o **amigo** palavra-chave e o nome de uma função de membro não ou outra classe para conceder acesso aos membros particulares e protegidos da sua classe. Em uma definição de modelo, um parâmetro de tipo pode ser declarado como um amigo.

## <a name="syntax"></a>Sintaxe

```
class friend F
friend F;
```

## <a name="friend-declarations"></a>Declarações de amigo

Se você declarar uma função de amigo que não foi declarada anteriormente, essa função é exportada para o escopo de envolvimento sem classe.

As funções declaradas em uma declaração de amigo são tratadas como se tivessem sido declaradas usando o **extern** palavra-chave. Para obter mais informações, consulte [extern](extern-cpp.md).

Ainda que as funções com escopo global possam ser declaradas como amigos antes dos protótipos, as funções de membro não podem ser declaradas como amigos antes da aparência de sua declaração completa da classe. O exemplo de código a seguir mostra porque isso falha:

```cpp
class ForwardDeclared;   // Class name is known.
class HasFriends
{
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected
};
```

O exemplo anterior insere o nome da classe `ForwardDeclared` no escopo, mas a declaração completa — especificamente, a parte que declara a função `IsAFriend` — não é conhecida. Portanto, o **amigo** declaração de classe `HasFriends` gera um erro.

Começando no C++ 11, há duas formas de declarações de amigo para uma classe:

```cpp
friend class F;
friend F;
```

O primeiro formulário introduz uma nova classe F se nenhuma classe existente com esse nome foi encontrado no namespace mais interno. **C++11**: O segundo formulário não introduz uma nova classe; ele pode ser usado quando a classe já foi declarada e deve ser usada ao declarar um typedef como um amigo ou um parâmetro de tipo de modelo.

Use `class friend F` quando o tipo referenciado não ainda foi declarado:

```cpp
namespace NS
{
    class M
    {
        class friend F;  // Introduces F but doesn't define it
    };
}
```

```cpp
namespace NS
{
    class M
    {
        friend F; // error C2433: 'NS::F': 'friend' not permitted on data declarations
    };
}
```

No exemplo a seguir `friend F` refere-se ao `F` classe é declarada fora do escopo de NS.

```cpp
class F {};
namespace NS
{
    class M
    {
        friend F;  // OK
    };
}
```

Use `friend F` para declarar um parâmetro de modelo como um amigo:

```cpp
template <typename T>
class my_class
{
    friend T;
    //...
};
```

Use `friend F` para declarar um typedef como amigo:

```cpp
class Foo {};
typedef Foo F;

class G
{
    friend F; // OK
    friend class F // Error C2371 -- redefinition
};
```

Para declarar duas classes que são amigas da outro, a segunda classe inteira deve ser especificada como amiga de primeira classe. A razão para essa restrição é que o compilador tem informações suficientes para declarar funções individuais de amigo somente no ponto onde a segunda classe é declarada.

> [!NOTE]
>  Embora a segunda classe inteira deve ser amiga da primeira classe, você pode selecionar quais funções na primeira classe serão amigas da segunda classe.

## <a name="friend-functions"></a>funções friend

Um **amigo** é uma função que não é um membro de uma classe, mas tem acesso a membros particulares e protegidos da classe. As funções friend não são consideradas membros de classe; elas são funções externas normais que recebem privilégios de acesso especiais. Friends não estão no escopo da classe, e eles não são chamados usando os operadores de seleção de membro (**.** e -**>**), a menos que eles são membros de outra classe. Um **amigo** função é declarada pela classe que está concedendo acesso. O **amigo** declaração pode ser colocada em qualquer lugar na declaração da classe. Ela não é afetada pelas palavras-chave de controle de acesso.

O exemplo a seguir mostra uma classe `Point` e uma função friend, `ChangePrivate`. O **amigo** função tem acesso ao membro de dados privados de `Point` ele recebe como um parâmetro de objeto.

```cpp
// friend_functions.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class Point
{
    friend void ChangePrivate( Point & );
public:
    Point( void ) : m_i(0) {}
    void PrintPrivate( void ){cout << m_i << endl; }

private:
    int m_i;
};

void ChangePrivate ( Point &i ) { i.m_i++; }

int main()
{
   Point sPoint;
   sPoint.PrintPrivate();
   ChangePrivate(sPoint);
   sPoint.PrintPrivate();
// Output: 0
           1
}
```

## <a name="class-members-as-friends"></a>Membros de classes como amigos

As funções de membro da classe podem ser declaradas como amigos em outras classes. Considere o exemplo a seguir:

```cpp
// classes_as_friends1.cpp
// compile with: /c
class B;

class A {
public:
   int Func1( B& b );

private:
   int Func2( B& b );
};

class B {
private:
   int _b;

   // A::Func1 is a friend function to class B
   // so A::Func1 has access to all members of B
   friend int A::Func1( B& );
};

int A::Func1( B& b ) { return b._b; }   // OK
int A::Func2( B& b ) { return b._b; }   // C2248
```

No exemplo anterior, somente a função `A::Func1( B& )` tem acesso de amigo para classificar `B`. Portanto, o acesso ao membro particular `_b` está correto na `Func1` da classe `A` , mas não no `Func2`.

Uma classe `friend` é uma classe cujas funções membro são as funções amigas de uma classe, ou seja, cujas funções membro tenham acesso aos outros membros particulares e protegidos da classe. Suponha que a declaração `friend` na classe `B` fosse:

```cpp
friend class A;
```

Nesse caso, todas as funções membro na classe `A` receberão acesso de amigo para classificar `B`. O código a seguir é um exemplo de uma classe de amigo:

```cpp
// classes_as_friends2.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class YourClass {
friend class YourOtherClass;  // Declare a friend class
public:
   YourClass() : topSecret(0){}
   void printMember() { cout << topSecret << endl; }
private:
   int topSecret;
};

class YourOtherClass {
public:
   void change( YourClass& yc, int x ){yc.topSecret = x;}
};

int main() {
   YourClass yc1;
   YourOtherClass yoc1;
   yc1.printMember();
   yoc1.change( yc1, 5 );
   yc1.printMember();
}
```

A amizade não é mútua a menos que explicitamente especificada como tal. No exemplo anterior, as funções membro de `YourClass` não podem acessar os membros privados de `YourOtherClass`.

Um tipo gerenciado não pode ter nenhuma função de amigo, classes de amigo ou interfaces de amigo.

A amizade não é herdada, o que significa que as classes derivadas de `YourOtherClass` não podem acessar os membros privados de `YourClass`. A amizade não é transitiva, assim as classes que são amigos de `YourOtherClass` não podem acessar membros privados de `YourClass`.

A figura a seguir mostra quatro declarações de classe: `Base`, `Derived`, `aFriend` e `anotherFriend`. Somente a classe `aFriend` tem acesso direto aos membros privados de `Base` (e a todos os membros que `Base` pode ter herdado).

![Implicações da relação de amigo](../cpp/media/vc38v41.gif "vc38V41") implicações da relação de amigo

## <a name="inline-friend-definitions"></a>Definições de amigo embutida

As funções friend podem ser definidas nas declarações de classe. Essas funções são funções embutidas, e como funções membro embutidas, se comportam como se fossem definidas imediatamente após todos os membros de classe terem sido vistos, mas antes que o escopo de classe seja fechado (o final da declaração de classe).

As funções friend definidas dentro de declarações de classe não são consideradas no escopo da classe delimitadora; elas estão no escopo do arquivo.

## <a name="see-also"></a>Consulte também

[Palavras-chave](../cpp/keywords-cpp.md)