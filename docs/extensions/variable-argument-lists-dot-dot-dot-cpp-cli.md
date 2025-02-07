---
title: Listas de Argumentos Variáveis (...) (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
ms.openlocfilehash: ec1e2cefa33bc9d749d0f05e170c2f2db9b25f02
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515951"
---
# <a name="variable-argument-lists--ccli"></a>Listas de Argumentos Variáveis (...) (C++/CLI)

Este exemplo mostra como você pode usar a sintaxe `...` em C++/CLI para implementar funções que tenham um número variável de argumentos.

> [!NOTE]
> Este tópico refere-se a C++/CLI. Saiba mais sobre como usar `...` no padrão ISO do C++ em [Reticências e modelos variadic](../cpp/ellipses-and-variadic-templates.md) e Reticências e argumentos padrão em [Expressões pós-fixadas](../cpp/postfix-expressions.md).

O parâmetro que usa `...` deve ser o último parâmetro na lista de parâmetros.

## <a name="example"></a>Exemplo

### <a name="code"></a>Código

```cpp
// mcppv2_paramarray.cpp
// compile with: /clr
using namespace System;
double average( ... array<Int32>^ arr ) {
   int i = arr->GetLength(0);
   double answer = 0.0;

   for (int j = 0 ; j < i ; j++)
      answer += arr[j];

   return answer / i;
}

int main() {
   Console::WriteLine("{0}", average( 1, 2, 3, 6 ));
}
```

```Output
3
```

## <a name="code-example"></a>Exemplo de código

O exemplo a seguir mostra como chamar uma função do Visual C++ que leva um número variável de argumentos a partir de C#.

```cpp
// mcppv2_paramarray2.cpp
// compile with: /clr:safe /LD
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};
```

A função `f` pode ser chamada de C# ou Visual Basic, por exemplo, como se fosse uma função que pode receber um número variável de argumentos.

Em C#, um argumento que é passado para um parâmetro `ParamArray` pode ser chamado por um número variável de argumentos. O exemplo de código a seguir está em C#.

```cs
// mcppv2_paramarray3.cs
// compile with: /r:mcppv2_paramarray2.dll
// a C# program

public class X {
   public static void Main() {
      // Visual C# will generate a String array to match the
      // ParamArray attribute
      C myc = new C();
      myc.f("hello", "there", "world");
   }
}
```

Uma chamada para `f` no Visual C++ pode transmitir uma matriz inicializada ou uma matriz de comprimento variável.

```cpp
// mcpp_paramarray4.cpp
// compile with: /clr
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};

int main() {
   C ^ myc = gcnew C();
   myc->f("hello", "world", "!!!");
}
```

## <a name="see-also"></a>Consulte também

[Matrizes](arrays-cpp-component-extensions.md)