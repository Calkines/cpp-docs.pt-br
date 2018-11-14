---
title: Erro do compilador C2761
ms.date: 11/04/2016
f1_keywords:
- C2761
helpviewer_keywords:
- C2761
ms.assetid: 38c79a05-b56d-485b-820f-95e8c0cb926f
ms.openlocfilehash: 1236cfaf70781b6ca80db1a317a0c1b01b0f2740
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520914"
---
# <a name="compiler-error-c2761"></a>Erro do compilador C2761

'function': redeclaração de função de membro não permitida

Você não é possível redeclarar uma função de membro. Você pode defini-lo, mas não redeclará-lo.

## <a name="example"></a>Exemplo

O exemplo a seguir gera C2761.

```
// C2761.cpp
class a {
   int t;
   void test();
};

void a::a;     // C2761
void a::test;  // C2761
```

## <a name="example"></a>Exemplo

Membros não estáticos de uma classe ou estrutura não podem ser definidos.  O exemplo a seguir gera C2761.

```
// C2761_b.cpp
// compile with: /c
struct C {
   int s;
   static int t;
};

int C::s;   // C2761
int C::t;   // OK
```