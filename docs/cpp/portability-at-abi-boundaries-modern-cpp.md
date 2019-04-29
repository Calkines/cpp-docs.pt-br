---
title: Portabilidade em limites ABI (C++ moderno)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
ms.openlocfilehash: 3f72bc32e436c2f7a2f76ed6bbb9553b5e5be6b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267670"
---
# <a name="portability-at-abi-boundaries-modern-c"></a>Portabilidade em limites ABI (C++ moderno)

Use tipos suficientemente portáteis e convenções nos limites da interface binária. Um "tipo portátil" é um tipo interno de C ou um struct que contém apenas os tipos internos de C. Tipos de classe só podem ser usados quando o chamador e o receptor concordarem sobre layout, convenção de chamada etc. Isso é possível apenas quando ambas são compiladas com o mesmo compilador e as configurações do compilador.

## <a name="how-to-flatten-a-class-for-c-portability"></a>Como mesclar uma classe para fins de portabilidade de C

Quando os chamadores podem ser compilados com outro compilador/idioma, em seguida, "mesclar" para um **extern "C"** API com uma convenção de chamada específica:

```cpp
// class widget {
//   widget();
//   ~widget();
//   double method( int, gadget& );
// };
extern "C" {        // functions using explicit "this"
   struct widget;   // opaque type (forward declaration only)
   widget* STDCALL widget_create();      // constructor creates new "this"
   void STDCALL widget_destroy(widget*); // destructor consumes "this"
   double STDCALL widget_method(widget*, int, gadget*); // method uses "this"
}
```

## <a name="see-also"></a>Consulte também

[Bem-vindo ao C++ (C++ moderno)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referência da linguagem C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca Padrão do C++](../standard-library/cpp-standard-library-reference.md)
