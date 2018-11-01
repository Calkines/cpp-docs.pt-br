---
title: Portabilidade em limites ABI (C++ moderno)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
ms.openlocfilehash: 12f60b92e71c15a94546e5b099c3b49e3685b68b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549949"
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

[Bem-vindo outra vez ao C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referência da linguagem C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca Padrão do C++](../standard-library/cpp-standard-library-reference.md)