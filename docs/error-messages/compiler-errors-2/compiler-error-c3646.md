---
title: Erro do compilador C3646
ms.date: 06/14/2018
f1_keywords:
- C3646
helpviewer_keywords:
- C3646
ms.assetid: 4391ead2-9637-4ca3-aeda-5a991b18d66d
ms.openlocfilehash: 04ff1d026c97c56611f8b786d8a7254db711e4a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385583"
---
# <a name="compiler-error-c3646"></a>Erro do compilador C3646

> 'especificador de ': especificador de substituição desconhecido

## <a name="remarks"></a>Comentários

O compilador não encontrou um token na posição em que ele esperava-se encontrar um especificador de substituição, mas o token não foi reconhecido pelo compilador.

Por exemplo, se o não reconhecido *especificador* é **_NOEXCEPT**, substitua-o com a palavra-chave **noexcept**.

Para obter mais informações, consulte [especificadores de substituição](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Exemplo

O exemplo a seguir gera C3646 e mostra uma maneira de corrigir isso:

```cpp
// C3646.cpp
// compile with: /clr /c
ref class C {
   void f() unknown;   // C3646
   // try the following line instead
   // virtual void f() abstract;
};
```