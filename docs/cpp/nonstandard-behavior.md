---
title: Comportamento não padrão
ms.date: 05/06/2019
helpviewer_keywords:
- compatibility and compliance, nonstandard behavior
- Microsoft-specific, compiler behavior
- nonstandard behavior, compliance and compatibility
ms.assetid: a57dea27-dc79-4f64-8a83-017e84841773
ms.openlocfilehash: 82c5faae68f9da747017119d76578cc88163d8bb
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222035"
---
# <a name="nonstandard-behavior"></a>Comportamento não padrão

As seções a seguir listam alguns dos locais em que a implementação da Microsoft C++ não é compatível com o C++ padrão. Os números de seção fornecidos abaixo se referem aos números da seção no padrão C++ 11 (ISO/IEC 14882:2011(E)).

A lista de limites do compilador que diferem daqueles definidos no padrão C++ é fornecida em [limites do compilador](../cpp/compiler-limits.md).

## <a name="covariant-return-types"></a>Tipos de retorno covariantes

As classes base virtuais não têm suporte como tipo de retorno covariante quando a função virtual tem um número variável de argumentos. Isso não está em conformidade com a seção 10.3, parágrafo 7 da especificação ISO do C++. O exemplo a seguir não é compilado, dando erro do compilador [C2688](../error-messages/compiler-errors-2/compiler-error-c2688.md)

```cpp
// CovariantReturn.cpp
class A
{
   virtual A* f(int c, ...);   // remove ...
};

class B : virtual A
{
   B* f(int c, ...);   // C2688 remove ...
};
```

## <a name="binding-nondependent-names-in-templates"></a>Associação de nomes não dependentes nos modelos

O Microsoft C++ compilador não oferece suporte a nomes de associação não dependentes ao analisar inicialmente um modelo. Isso não está em conformidade com a seção 14.6.3 da especificação ISO do C++. Isso pode fazer com que sobrecargas declaradas após o modelo (mas antes do modelo ser instanciado) sejam vistas.

```cpp
#include <iostream>
using namespace std;

namespace N {
   void f(int) { cout << "f(int)" << endl;}
}

template <class T> void g(T) {
    N::f('a');   // calls f(char), should call f(int)
}

namespace N {
    void f(char) { cout << "f(char)" << endl;}
}

int main() {
    g('c');
}
// Output: f(char)
```

## <a name="function-exception-specifiers"></a>Especificadores de exceção de função

Os especificadores da exceção de função diferentes de `throw()` são analisados, mas não usados. Isso não está em conformidade com a seção 15.4 da especificação ISO do C++. Por exemplo:

```cpp
void f() throw(int); // parsed but not used
void g() throw();    // parsed and used
```

Para obter mais informações sobre especificações de exceção, consulte [especificações de exceção](../cpp/exception-specifications-throw-cpp.md).

## <a name="chartraitseof"></a>char_traits::eof()

O C++ padrão declara que [char_traits:: EOF](../standard-library/char-traits-struct.md#eof) não deve corresponder a um válido `char_type` valor. O Microsoft C++ compilador impõe essa restrição para o tipo **char**, mas não para o tipo **wchar_t**. Isso não está em conformidade com o requisito da Tabela 62, na seção 12.1.1 da especificação ISO do C++. O exemplo abaixo demonstra isso.

```cpp
#include <iostream>

int main()
{
    using namespace std;

    char_traits<char>::int_type int2 = char_traits<char>::eof();
    cout << "The eof marker for char_traits<char> is: " << int2 << endl;

    char_traits<wchar_t>::int_type int3 = char_traits<wchar_t>::eof();
    cout << "The eof marker for char_traits<wchar_t> is: " << int3 << endl;
}
```

## <a name="storage-location-of-objects"></a>Local de armazenamento de objetos

O padrão C++ (seção 1.8, parágrafo 6) exige que objetos completos do C++ tenham locais exclusivos de armazenamento. No entanto com a Microsoft C++, há casos em que o tipos sem membros de dados compartilharão um local de armazenamento com outros tipos para o tempo de vida do objeto.