---
title: Erro do compilador C3633
ms.date: 11/04/2016
f1_keywords:
- C3633
helpviewer_keywords:
- C3633
ms.assetid: 7d65babf-2191-4d67-a69f-f5c4c2ddf946
ms.openlocfilehash: 2d96a0e4f5f0b34c76f41058316c7f158f1a939d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385700"
---
# <a name="compiler-error-c3633"></a>Erro do compilador C3633

não é possível definir 'member' como um membro de 'tipo' gerenciado

Membros de dados de classe de referência do CLR não podem ser de um tipo não POD C++.  Você só pode instanciar um tipo nativo de POD em um tipo CLR.  Por exemplo, um tipo POD não pode conter um construtor de cópia ou um operador de atribuição.

## <a name="example"></a>Exemplo

O exemplo a seguir gera C3633.

```
// C3633.cpp
// compile with: /clr /c
#pragma warning( disable : 4368 )

class A1 {
public:
   A1() { II = 0; }
   int II;
};

ref class B {
public:
   A1 a1;   // C3633
   A1 * a2;   // OK
   B() : a2( new A1 ) {}
    ~B() { delete a2; }
};
```
