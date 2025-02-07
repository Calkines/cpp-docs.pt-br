---
title: Operador dynamic_cast
ms.date: 11/19/2018
f1_keywords:
- dynamic_cast_cpp
helpviewer_keywords:
- dynamic_cast keyword [C++]
ms.assetid: f380ada8-6a18-4547-93c9-63407f19856b
ms.openlocfilehash: 3b359885eb72f9272fb1efe14afe9a6cbe6ddb30
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399017"
---
# <a name="dynamiccast-operator"></a>Operador dynamic_cast

Converte o operando `expression` em um objeto do tipo `type-id`.

## <a name="syntax"></a>Sintaxe

```
dynamic_cast < type-id > ( expression )
```

## <a name="remarks"></a>Comentários

`type-id` deve ser um ponteiro ou uma referência a um tipo previamente definido da classe ou a um "ponteiro para nulo". O tipo de `expression` deve ser um ponteiro se `type-id` for um ponteiro, ou um l-value se `type-id` for uma referência.

Ver [static_cast](../cpp/static-cast-operator.md) para obter uma explicação da diferença entre conversões estáticas e dinâmicas, e quando é apropriado usar cada um.

Há duas importantes alterações no comportamento dos **dynamic_cast** em código gerenciado:

- **dynamic_cast** em um ponteiro para o tipo subjacente de uma enum encaixotado falhará no tempo de execução, retornando 0 ao invés do ponteiro convertido.

- **dynamic_cast** não gerará uma exceção quando `type-id` é um ponteiro interior para um tipo de valor, com a conversão que falhará em tempo de execução.  Agora, a conversão retornará ao valor 0 do ponteiro ao invés de gerar.

Se `type-id` for um ponteiro para uma classe base direta ou indireta, inequívoca e acessível de `expression`, um ponteiro para o subobjeto exclusivo do tipo `type-id` é o resultado. Por exemplo:

```cpp
// dynamic_cast_1.cpp
// compile with: /c
class B { };
class C : public B { };
class D : public C { };

void f(D* pd) {
   C* pc = dynamic_cast<C*>(pd);   // ok: C is a direct base class
                                   // pc points to C subobject of pd
   B* pb = dynamic_cast<B*>(pd);   // ok: B is an indirect base class
                                   // pb points to B subobject of pd
}
```

Esse tipo de conversão é chamada de "upcast", pois move um ponteiro para uma hierarquia da classe acima, de uma classe derivada para uma classe de derivação. Um upcast é uma conversão implícita.

Se `type-id` é nulo*, uma verificação de tempo de execução será feita para determinar o tipo real de `expression`. O resultado é um ponteiro para o objeto completo apontado por `expression`. Por exemplo:

```cpp
// dynamic_cast_2.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};

void f() {
   A* pa = new A;
   B* pb = new B;
   void* pv = dynamic_cast<void*>(pa);
   // pv now points to an object of type A

   pv = dynamic_cast<void*>(pb);
   // pv now points to an object of type B
}
```

Se `type-id` não é nulo*, uma verificação de tempo de execução será feita para verificar se o objeto apontado por `expression` pode ser convertido para o tipo apontado por `type-id`.

Se o tipo de `expression` é uma classe base do tipo `type-id`, uma verificação de tempo de execução será feita para verificar se `expression` realmente aponta para um objeto completo do tipo `type-id`. Se isso ocorrer, o resultado é um ponteiro para um objeto completo do tipo `type-id`. Por exemplo:

```cpp
// dynamic_cast_3.cpp
// compile with: /c /GR
class B {virtual void f();};
class D : public B {virtual void f();};

void f() {
   B* pb = new D;   // unclear but ok
   B* pb2 = new B;

   D* pd = dynamic_cast<D*>(pb);   // ok: pb actually points to a D
   D* pd2 = dynamic_cast<D*>(pb2);   // pb2 points to a B not a D
}
```

Esse tipo de conversão é chamada de "downcast", pois move um ponteiro para uma hierarquia da classe abaixo, de uma classe determinada para uma classe derivada dela.

Em casos de herança múltipla, as possibilidades de ambiguidade são introduzidas. Considere a hierarquia da classe mostrada na figura a seguir.

Para tipos CLR **dynamic_cast** resulta em um sem op se a conversão pode ser realizada implicitamente ou um MSIL `isinst` instrução, que executa uma verificação dinâmica e retorna **nullptr** se a a conversão falhará.

O exemplo a seguir usa **dynamic_cast** para determinar se uma classe é uma instância de tipo específico:

```cpp
// dynamic_cast_clr.cpp
// compile with: /clr
using namespace System;

void PrintObjectType( Object^o ) {
   if( dynamic_cast<String^>(o) )
      Console::WriteLine("Object is a String");
   else if( dynamic_cast<int^>(o) )
      Console::WriteLine("Object is an int");
}

int main() {
   Object^o1 = "hello";
   Object^o2 = 10;

   PrintObjectType(o1);
   PrintObjectType(o2);
}
```

![Classe de hierarquia que mostra a herança múltipla](../cpp/media/vc39011.gif "hierarquia que mostra várias heranças de classes") <br/>
Hierarquia de classe que mostra a herança múltipla

Um ponteiro para um objeto do tipo `D` pode seguramente ser gerado em `B` ou `C`. No entanto, se `D` for gerado para apontar para um objeto `A`, qual instância de `A` resultaria? Isso resultará em um erro ambíguo de geração. Para contornar esse problema, você pode executar duas conversões inequívocas. Por exemplo:

```cpp
// dynamic_cast_4.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};
class D : public B {virtual void f();};

void f() {
   D* pd = new D;
   B* pb = dynamic_cast<B*>(pd);   // first cast to B
   A* pa2 = dynamic_cast<A*>(pb);   // ok: unambiguous
}
```

As ambiguidades adicionais podem ser introduzidas quando você usar classes base virtuais. Considere a hierarquia da classe mostrada na figura a seguir.

![Classe de hierarquia que mostra as classes base virtuais](../cpp/media/vc39012.gif "classe hierarquia que mostra as classes base virtuais") <br/>
Hierarquia de classe que mostra as classes base virtuais

Nesta hierarquia, `A` é uma classe base virtual. Dada uma instância da classe `E` e um ponteiro para o `A` subobjeto, um **dynamic_cast** em um ponteiro para `B` falhará devido à ambiguidade. Primeiro você deve converter de volta ao objeto completo `E`, então trabalhar até a hierarquia, de maneira não ambígua, para alcançar o objeto correto `B`.

Considere a hierarquia da classe mostrada na figura a seguir.

![Classe de hierarquia que mostra as classes base duplicadas](../cpp/media/vc39013.gif "classe hierarquia que mostra as classes base duplicadas") <br/>
Hierarquia de classes que mostra as classes base duplicadas

Dado um objeto de tipo `E` e um ponteiro para o subobjeto `D`, para navegar do subobjeto `D` ao subobjeto mais à esquerda `A`, três conversões podem ser feitas. Você pode executar uma **dynamic_cast** conversão da `D` ponteiro para um `E` ponteiro e, em seguida, uma conversão (ambos **dynamic_cast** ou uma conversão implícita) de `E`para `B`e finalmente uma conversão implícita da `B` para `A`. Por exemplo:

```cpp
// dynamic_cast_5.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A { };
class D {virtual void f();};
class E : public B, public C, public D {virtual void f();};

void f(D* pd) {
   E* pe = dynamic_cast<E*>(pd);
   B* pb = pe;   // upcast, implicit conversion
   A* pa = pb;   // upcast, implicit conversion
}
```

O **dynamic_cast** operador também pode ser usado para executar uma "conversão cruzada". Usando a mesma hierarquia da classe, é possível converter um ponteiro, por exemplo, do subobjeto `B` ao para o subobjeto `D`, contanto que o objeto completo seja do tipo `E`.

Considerando as conversões cruzadas, é realmente possível fazer a conversão de um ponteiro para `D` para um ponteiro para o subobjeto mais à esquerda de `A` em apenas duas etapas. Você pode executar uma conversão cruzada de `D` para `B`, e uma conversão implícita de `B` para `A`. Por exemplo:

```cpp
// dynamic_cast_6.cpp
// compile with: /c /GR
class A {virtual void f();};
class B : public A {virtual void f();};
class C : public A { };
class D {virtual void f();};
class E : public B, public C, public D {virtual void f();};

void f(D* pd) {
   B* pb = dynamic_cast<B*>(pd);   // cross cast
   A* pa = pb;   // upcast, implicit conversion
}
```

Um valor de ponteiro nulo é convertido para o valor de ponteiro nulo do tipo de destino pela **dynamic_cast**.

Quando você usa `dynamic_cast < type-id > ( expression )`, se `expression` não puder ser convertido com segurança para o tipo `type-id`, a verificação de tempo de execução fará com que a conversão falhe. Por exemplo:

```cpp
// dynamic_cast_7.cpp
// compile with: /c /GR
class A {virtual void f();};
class B {virtual void f();};

void f() {
   A* pa = new A;
   B* pb = dynamic_cast<B*>(pa);   // fails at runtime, not safe;
   // B not derived from A
}
```

O valor de uma conversão falhada para o tipo de ponteiro é o ponteiro nulo. Uma conversão falhada para o tipo de referencia gera uma [exceção bad_cast](../cpp/bad-cast-exception.md).   Se `expression` apontar para ou fazer referência a um objeto válido, não um `__non_rtti_object` exceção é lançada.

Ver [typeid](../cpp/typeid-operator.md) para obter uma explicação de `__non_rtti_object` exceção.

## <a name="example"></a>Exemplo

O exemplo a seguir cria o ponteiro (struct A) da classe base, para um objeto (struct C).  Isso, além da existência de funções virtuais, permite a polimorfismo de tempo de execução.

O exemplo também chama uma função não virtual na hierarquia.

```cpp
// dynamic_cast_8.cpp
// compile with: /GR /EHsc
#include <stdio.h>
#include <iostream>

struct A {
    virtual void test() {
        printf_s("in A\n");
   }
};

struct B : A {
    virtual void test() {
        printf_s("in B\n");
    }

    void test2() {
        printf_s("test2 in B\n");
    }
};

struct C : B {
    virtual void test() {
        printf_s("in C\n");
    }

    void test2() {
        printf_s("test2 in C\n");
    }
};

void Globaltest(A& a) {
    try {
        C &c = dynamic_cast<C&>(a);
        printf_s("in GlobalTest\n");
    }
    catch(std::bad_cast) {
        printf_s("Can't cast to C\n");
    }
}

int main() {
    A *pa = new C;
    A *pa2 = new B;

    pa->test();

    B * pb = dynamic_cast<B *>(pa);
    if (pb)
        pb->test2();

    C * pc = dynamic_cast<C *>(pa2);
    if (pc)
        pc->test2();

    C ConStack;
    Globaltest(ConStack);

   // will fail because B knows nothing about C
    B BonStack;
    Globaltest(BonStack);
}
```

```Output
in C
test2 in B
in GlobalTest
Can't cast to C
```

## <a name="see-also"></a>Consulte também

[Operadores de conversão](../cpp/casting-operators.md)<br/>
[Palavras-chave](../cpp/keywords-cpp.md)