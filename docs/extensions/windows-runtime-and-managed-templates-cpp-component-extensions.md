---
title: Windows Runtime e modelos gerenciados (C++/CLI e C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- templates, with CLR types
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
ms.openlocfilehash: a8cc429763d042ba262d5543f4a2d85bbf8aa29a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515961"
---
# <a name="windows-runtime-and-managed-templates-ccli-and-ccx"></a>Windows Runtime e modelos gerenciados (C++/CLI e C++/CX)

Os modelos possibilitam definir um protótipo de um tipo do Windows Runtime ou do Common Language Runtime e, em seguida, criar instâncias de variações desse tipo usando parâmetros de tipo de modelo diferentes.

## <a name="all-runtimes"></a>Todos os Tempos de Execução

Você pode criar modelos a partir de valores ou tipos de referência.  Saiba mais sobre como criar tipos de valor ou de referência em [Classes e structs](classes-and-structs-cpp-component-extensions.md).

Saiba mais sobre modelos de classe padrão do C++ em [Modelos de classe](../cpp/class-templates.md).

## <a name="windows-runtime"></a>Tempo de Execução do Windows

(Não há comentários para esse recurso de linguagem que se apliquem somente ao Windows Runtime.)

### <a name="requirements"></a>Requisitos

Opção do compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Existem algumas limitações na criação de modelos de classes a partir de tipos gerenciados, que são demonstradas nos exemplos de código a seguir.

### <a name="requirements"></a>Requisitos

Opção do compilador: `/clr`

### <a name="examples"></a>Exemplos

É possível criar uma instância de um tipo genérico com um parâmetro de modelo de tipo gerenciado, mas não é possível criar uma instância de um modelo gerenciado com um parâmetro de modelo de tipo genérico. Isso ocorre porque os tipos genéricos são resolvidos no tempo de execução. Saiba mais em [Genéricos e modelos (C++/CLI)](generics-and-templates-visual-cpp.md).

```cpp
// managed_templates.cpp
// compile with: /clr /c

generic<class T>
ref class R;

template<class T>
ref class Z {
   // Instantiate a generic with a template parameter.
   R<T>^ r;    // OK
};

generic<class T>
ref class R {
   // Cannot instantiate a template with a generic parameter.
   Z<T>^ z;   // C3231
};
```

Um tipo genérico ou função não poder ser aninhado em um modelo gerenciado.

```cpp
// managed_templates_2.cpp
// compile with: /clr /c

template<class T> public ref class R {
   generic<class T> ref class W {};   // C2959
};
```

Você não pode acessar modelos definidos em um assembly referenciado com a sintaxe da linguagem C++/CLI, mas pode usar o reflexo. Se um modelo não for instanciado, não será emitido nos metadados. Se um modelo for instanciado, somente as funções de membro referenciadas aparecerão nos metadados.

```cpp
// managed_templates_3.cpp
// compile with: /clr

// Will not appear in metadata.
template<class T> public ref class A {};

// Will appear in metadata as a specialized type.
template<class T> public ref class R {
public:
   // Test is referenced, will appear in metadata
   void Test() {}

   // Test2 is not referenced, will not appear in metadata
   void Test2() {}
};

// Will appear in metadata.
generic<class T> public ref class G { };

public ref class S { };

int main() {
   R<int>^ r = gcnew R<int>;
   r->Test();
}
```

Você pode alterar o modificador gerenciado de uma classe em uma especialização parcial ou especialização explícita de um modelo de classe.

```cpp
// managed_templates_4.cpp
// compile with: /clr /c

// class template
// ref class
template <class T>
ref class A {};

// partial template specialization
// value type
template <class T>
value class A <T *> {};

// partial template specialization
// interface
template <class T>
interface class A<T%> {};

// explicit template specialization
// native class
template <>
class A <int> {};
```

## <a name="see-also"></a>Consulte também

[Extensões de componentes para .NET e UWP](component-extensions-for-runtime-platforms.md)