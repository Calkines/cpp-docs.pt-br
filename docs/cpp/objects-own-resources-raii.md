---
title: Recursos de objetos próprios (RAII)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f86b484e-5a27-4c3b-a92a-dfaa5dd6d93a
ms.openlocfilehash: 5705fc1996343141b13e37d1267b2e8c981c1eba
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220420"
---
# <a name="objects-own-resources-raii"></a>Recursos de objetos próprios (RAII)

Certifique-se de que os objetos próprios recursos. Esse princípio é também conhecido como "aquisição de recurso é inicialização" ou "RAII".

## <a name="example"></a>Exemplo

Passe todos os objetos "novo" como um argumento de construtor para outro objeto nomeado que o possui (quase sempre unique_ptr).

```cpp
void f() {
    unique_ptr<widget> p( new widget() );
    my_class x( new widget() );
    // ...
} // automatic destruction and deallocation for both widget objects
  // automatic exception safety, as if "finally { p->dispose(); x.w.dispose(); }"
```

Ocorrem sempre imediatamente passe qualquer novo recurso para outro objeto que ele pertence.

```cpp
void g() {
    other_class y( OpenFile() );
    // ...
} // automatic closing and release for file resource
  // automatic exception safety, as if "finally { y.file.dispose(); }"
```

## <a name="see-also"></a>Consulte também

[Bem-vindo ao C++ (C++ moderno)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referência da linguagem C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca Padrão do C++](../standard-library/cpp-standard-library-reference.md)
