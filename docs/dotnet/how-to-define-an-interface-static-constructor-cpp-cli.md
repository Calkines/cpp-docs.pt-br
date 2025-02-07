---
title: 'Como: Definir um construtor estático de Interface (C++/CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [C++]
- static constructors, interface
- interface static constructor
ms.assetid: 1f031cb2-e94f-43dc-819b-44cf2faaaa49
ms.openlocfilehash: 326b315e1e6c4defbef3ab6e487c78635e0aa50f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378943"
---
# <a name="how-to-define-an-interface-static-constructor-ccli"></a>Como: Definir um construtor estático de Interface (C++/CLI)

Uma interface pode ter um construtor estático, que pode ser usado para inicializar membros de dados estáticos.  Um construtor estático será chamado no máximo uma vez e será chamado antes da primeira vez que um membro de interface estática é acessado.

## <a name="example"></a>Exemplo

```
// mcppv2_interface_class2.cpp
// compile with: /clr
using namespace System;

interface struct MyInterface {
   static int i;
   static void Test() {
      Console::WriteLine(i);
   }

   static MyInterface() {
      Console::WriteLine("in MyInterface static constructor");
      i = 99;
   }
};

ref class MyClass : public MyInterface {};

int main() {
   MyInterface::Test();
   MyClass::MyInterface::Test();

   MyInterface ^ mi = gcnew MyClass;
   mi->Test();
}
```

```Output
in MyInterface static constructor
99
99
99
```

## <a name="see-also"></a>Consulte também

[classe de interface](../extensions/interface-class-cpp-component-extensions.md)
