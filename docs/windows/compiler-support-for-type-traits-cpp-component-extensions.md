---
title: Suporte a compilador para características de tipo (C + + c++ /CLI e c++ /CLI CX) | Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- __is_simple_value_class
- __has_trivial_destructor
- __has_assign
- __is_union
- __is_class
- __is_abstract
- __has_trivial_assign
- __has_virtual_destructor
- __is_ref_array
- __is_base_of
- __has_copy
- __is_polymorphic
- __has_nothrow_constructor
- __is_ref_class
- __is_delegate
- __is_convertible_to
- __is_value_class
- __is_interface_class
- __has_nothrow_copy
- __is_sealed
- __has_trivial_constructor
- __has_trivial_copy
- __is_enum
- __has_nothrow_assign
- __has_finalizer
- __is_empty
- __is_pod
- __has_user_destructor
dev_langs:
- C++
helpviewer_keywords:
- __is_class keyword [C++]
- __is_pod keyword [C++]
- __is_delegate keyword [C++]
- __is_value_class keyword [C++]
- __has_copy keyword [C++]
- __has_nothrow_copy keyword [C++]
- __is_interface_class keyword [C++]
- __is_sealed keyword [C++]
- __is_convertible_to keyword [C++]
- __is_ref_class keyword [C++]
- __has_trivial_copy keyword [C++]
- __has_user_destructor keyword [C++]
- __is_abstract keyword [C++]
- __is_empty keyword [C++]
- __has_trivial_assign keyword [C++]
- __has_nothrow_constructor keyword [C++]
- __is_ref_array keyword [C++]
- __is_base_of keyword [C++]
- __has_nothrow_assign keyword [C++]
- __has_virtual_destructor keyword [C++]
- __has_finalizer keyword [C++]
- __is_union keyword [C++]
- __has_assign keyword [C++]
- __has_trivial_destructor keyword [C++]
- __is_polymorphic keyword [C++]
- __is_enum keyword [C++]
- __is_simple_value_class keyword [C++]
- __has_trivial_constructor keyword [C++]
ms.assetid: cd440630-0394-48c0-a16b-1580b6ef5844
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bef92e7315418e13b660f655a54f20e8696c7590
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066585"
---
# <a name="compiler-support-for-type-traits-ccli-and-ccx"></a>Suporte a compilador para características de tipo (C + + c++ /CLI e c++ /CLI CX)

O compilador de Microsoft C++ oferece suporte ao *características de tipo* para C + + c++ CLI e C + + c++ /CLI extensões CX, que indicam várias características de um tipo em tempo de compilação.

## <a name="all-runtimes"></a>Todos os Tempos de Execução

### <a name="remarks"></a>Comentários

Características de tipo são especialmente úteis para programadores que escrevem bibliotecas.

A lista a seguir contém as características de tipo que são suportadas pelo compilador. Todos os tipo de retorno de características **falsos** se a condição especificada pelo nome da característica de tipo não for atendida.

(Na lista a seguir, exemplos de código são gravados somente no C + + / CLI. Mas também há suporte para a característica de tipo correspondente no C + + c++ /CX, a menos que indicado de outra forma. O termo "tipo de plataforma" refere-se a tipos de tempo de execução do Windows ou tipos common language runtime.)

- `__has_assign(` *Tipo* `)`

   Retorna **verdadeira** se a plataforma ou tipo nativo tem um operador de atribuição de cópia.

    ```cpp
    ref struct R {
    void operator=(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_assign(R));
    }
    ```

- `__has_copy(` *Tipo* `)`

   Retorna **verdadeira** se a plataforma ou tipo nativo tem um construtor de cópia.

    ```cpp
    ref struct R {
    R(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_copy(R));
    }
    ```

- `__has_finalizer(` *Tipo* `)`

   (Não há suportada no C + + c++ /CLI CX.) Retorna **verdadeira** se o tipo CLR tem um finalizador. Ver [destruidores e finalizadores em como: definir e consumir classes e estruturas (C + + c++ CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) para obter mais informações.

    ```cpp
    using namespace System;
    ref struct R {
    ~R() {}
    protected:
    !R() {}
    };

    int main() {
    Console::WriteLine(__has_finalizer(R));
    }
    ```

- `__has_nothrow_assign(` *Tipo* `)`

   Retorna **verdadeira** se um operador de atribuição de cópia tem uma especificação de exceção vazio.

    ```cpp
    #include <stdio.h>
    struct S {
    void operator=(S& r) throw() {}
    };

    int main() {
    __has_nothrow_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_nothrow_constructor(` *Tipo* `)`

   Retorna **verdadeira** se o construtor padrão tem uma especificação de exceção vazio.

    ```cpp
    #include <stdio.h>
    struct S {
    S() throw() {}
    };

    int main() {
    __has_nothrow_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_nothrow_copy(` *Tipo* `)`

   Retorna **verdadeira** se o construtor de cópia tem uma especificação de exceção vazio.

    ```cpp
    #include <stdio.h>
    struct S {
    S(S& r) throw() {}
    };

    int main() {
    __has_nothrow_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_assign(` *Tipo* `)`

   Retorna **verdadeira** se o tipo tem um operador de atribuição trivial, gerado pelo compilador.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_constructor(` *Tipo* `)`

   Retorna **verdadeira** se o tipo tem um construtor trivial, gerado pelo compilador.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_copy(` *Tipo* `)`

   Retorna **verdadeira** se o tipo tem um construtor de cópia trivial, gerado pelo compilador.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_destructor(` *Tipo* `)`

   Retorna **verdadeira** se o tipo tem um destruidor trivial, gerado pelo compilador.

    ``` cpp
    // has_trivial_destructor.cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_user_destructor(` *Tipo* `)`

   Retorna **verdadeira** se a plataforma ou tipo nativo tem um destruidor declarado pelo usuário.

    ```cpp
    // has_user_destructor.cpp

    using namespace System;
    ref class R {
    ~R() {}
    };

    int main() {
    Console::WriteLine(__has_user_destructor(R));
    }
    ```

- `__has_virtual_destructor(` *Tipo* `)`

   Retorna **verdadeira** se o tipo tem um destruidor virtual.

   `__has_virtual_destructor` também funciona em tipos de plataforma e qualquer destruidor definido pelo usuário em um tipo de plataforma é um destruidor virtual.

    ```cpp
    // has_virtual_destructor.cpp
    #include <stdio.h>
    struct S {
    virtual ~S() {}
    };

    int main() {
    __has_virtual_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_abstract(` *Tipo* `)`

   Retorna **verdadeira** se o tipo for um tipo abstrato. Para obter mais informações sobre tipos abstratos nativos, consulte [Classes abstratas](../cpp/abstract-classes-cpp.md).

   `__is_abstract` também funciona para tipos de plataforma. Uma interface com pelo menos um membro é um tipo abstrato, assim como um tipo de referência pelo menos um membro abstrato. Para obter mais informações sobre tipos de plataforma abstratas, consulte [abstrata](../windows/abstract-cpp-component-extensions.md).

    ```cpp
    // is_abstract.cpp
    #include <stdio.h>
    struct S {
    virtual void Test() = 0;
    };

    int main() {
    __is_abstract(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_base_of(``base``,``derived``)`

   Retorna **verdadeira** se o primeiro tipo é uma classe base do segundo tipo, se ambos os tipos são iguais.

   `__is_base_of` também funciona em tipos de plataforma. Por exemplo, ele retornará **verdadeira** se o primeiro tipo é um [classe de interface](../windows/interface-class-cpp-component-extensions.md) e o segundo tipo implementa a interface.

    ```cpp
    // is_base_of.cpp
    #include <stdio.h>
    struct S {};
    struct T : public S {};

    int main() {
    __is_base_of(S, T) == true ?
    printf("true\n") : printf("false\n");

    __is_base_of(S, S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_class(` *Tipo* `)`

   Retorna **verdadeira** se o tipo é uma classe nativa ou estrutura.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_class(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_convertible_to(` `from` `,`  `to` `)`

   Retorna **verdadeira** se o primeiro tipo pode ser convertido para o segundo tipo.

    ```cpp
    #include <stdio.h>
    struct S {};
    struct T : public S {};

    int main() {
    S * s = new S;
    T * t = new T;
    s = t;
    __is_convertible_to(T, S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_delegate(` *Tipo* `)`

   Retorna **verdadeira** se `type` é um delegado. Para obter mais informações, consulte [delegar (C + + c++ /CLI e c++ /CLI CX)](../windows/delegate-cpp-component-extensions.md).

    ```cpp
    delegate void MyDel();
    int main() {
    System::Console::WriteLine(__is_delegate(MyDel));
    }
    ```

- `__is_empty(` *Tipo* `)`

   Retorna **verdadeira** se o tipo não tiver nenhum membro de dados de instância.

    ```cpp
    #include <stdio.h>
    struct S {
    int Test() {}
    static int i;
    };
    int main() {
    __is_empty(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_enum(` *Tipo* `)`

   Retorna **verdadeira** se o tipo é uma enumeração nativa.

    ```cpp
    // is_enum.cpp
    #include <stdio.h>
    enum E { a, b };

    struct S {
    enum E2 { c, d };
    };

    int main() {
    __is_enum(E) == true ?
    printf("true\n") : printf("false\n");

    __is_enum(S::E2) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_interface_class(` *Tipo* `)`

   Retorna **verdadeira** se passado a uma interface de plataforma. Para obter mais informações, consulte [classe de interface](../windows/interface-class-cpp-component-extensions.md).

    ```cpp
    // is_interface_class.cpp

    using namespace System;
    interface class I {};
    int main() {
    Console::WriteLine(__is_interface_class(I));
    }
    ```

- `__is_pod(` *Tipo* `)`

   Retorna **verdadeira** se o tipo é uma classe ou união com nenhum construtor ou os membros não estáticos privados ou protegidos, sem classes base e sem funções virtuais. Consulte o C++ standard, seções 8.5.1/1, 9/4 e 3.9/10 para obter mais informações sobre PODs.

   `__is_pod` retornará false sobre tipos fundamentais.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_pod(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_polymorphic(` *Tipo* `)`

   Retorna **verdadeira** se um tipo nativo tem funções virtuais.

    ```cpp
    #include <stdio.h>
    struct S {
    virtual void Test(){}
    };

    int main() {
    __is_polymorphic(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_ref_array(` *Tipo* `)`

   Retorna **verdadeira** se passado a uma matriz de plataforma. Para obter mais informações, consulte [matrizes](../windows/arrays-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    int main() {
    array<int>^ x = gcnew array<int>(10);
    Console::WriteLine(__is_ref_array(array<int>));
    }
    ```

- `__is_ref_class(` *Tipo* `)`

   Retorna **verdadeira** se passado a uma classe de referência. Para obter mais informações sobre tipos de referência definidos pelo usuário, consulte [Classes e Structs](../windows/classes-and-structs-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    ref class R {};
    int main() {
    Console::WriteLine(__is_ref_class(Buffer));
    Console::WriteLine(__is_ref_class(R));
    }
    ```

- `__is_sealed(` *Tipo* `)`

   Retorna **verdadeira** se passado a uma plataforma ou tipo nativo marcado como sealed. Para obter mais informações, consulte [lacrado](../windows/sealed-cpp-component-extensions.md).

    ```cpp
    ref class R sealed{};
    int main() {
    System::Console::WriteLine(__is_sealed(R));
    }
    ```

- `__is_simple_value_class(` *Tipo* `)`

   Retorna **verdadeira** se passado a um tipo de valor que não contém nenhuma referência para o heap coletado como lixo. Para obter mais informações sobre tipos de valor definidos pelo usuário, consulte [Classes e Structs](../windows/classes-and-structs-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    ref class R {};
    value struct V {};
    value struct V2 {
    R ^ r;   // not a simnple value type
    };

    int main() {
    Console::WriteLine(__is_simple_value_class(V));
    Console::WriteLine(__is_simple_value_class(V2));
    }
    ```

- `__is_union(` *Tipo* `)`

   Retorna **verdadeira** se um tipo é uma união.

    ```cpp
    #include <stdio.h>
    union A {
    int i;
    float f;
    };

    int main() {
    __is_union(A) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_value_class(` *Tipo* `)`

   Retorna **verdadeira** se passado a um tipo de valor. Para obter mais informações sobre tipos de valor definidos pelo usuário, consulte [Classes e Structs](../windows/classes-and-structs-cpp-component-extensions.md).

    ```cpp
    value struct V {};

    int main() {
    System::Console::WriteLine(__is_value_class(V));
    }
    ```

## <a name="windows-runtime"></a>Tempo de Execução do Windows

### <a name="remarks"></a>Comentários

O `__has_finalizer(` *tipo* `)` característica de tipo não tem suporte porque esta plataforma não dá suporte para os finalizadores.

### <a name="requirements"></a>Requisitos

Opção do compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Comentários

(Não há nenhum comentário específico da plataforma para esse recurso.)

### <a name="requirements"></a>Requisitos

Opção do compilador: `/clr`

### <a name="examples"></a>Exemplos

**Exemplo**

O exemplo de código a seguir mostra como usar um modelo de classe para expor uma característica de tipo de compilador para um `/clr` compilação. Para obter mais informações, consulte [tempo de execução do Windows e modelos gerenciados](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md).

```cpp
// compiler_type_traits.cpp
// compile with: /clr
using namespace System;

template <class T>
ref struct is_class {
   literal bool value = __is_ref_class(T);
};

ref class R {};

int main () {
   if (is_class<R>::value)
      Console::WriteLine("R is a ref class");
   else
      Console::WriteLine("R is not a ref class");
}
```

```Output
R is a ref class
```

## <a name="see-also"></a>Consulte também

[Extensões de componentes para .NET e UWP](../windows/component-extensions-for-runtime-platforms.md)