---
title: Erro do compilador C2990
ms.date: 11/04/2016
f1_keywords:
- C2990
helpviewer_keywords:
- C2990
ms.assetid: 674e9f6a-6743-4af0-a7ed-cbe11103a2f8
ms.openlocfilehash: 16c111a0fb8608615abaee495680fa38920b6c77
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447351"
---
# <a name="compiler-error-c2990"></a>Erro do compilador C2990

'class': tipo não classe já foi declarado como um tipo de classe

A classe de modelo ou não genérica redefine uma classe genérica ou modelo. Verifique os arquivos de cabeçalho para conflitos.

O exemplo a seguir gera C2990:

```
// C2990.cpp
// compile with: /c
template <class T>
class C{};
class C{};   // C2990
```

C2990 também podem ocorrer ao usar genéricos:

```
// C2990b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC;

ref struct GC {};   // C2990
```

C2990 também pode ocorrer devido a uma alteração significativa no Microsoft C++ compilador do Visual Studio 2005; o compilador agora exige que várias declarações para o mesmo tipo sejam idênticas em relação à especificação de modelo.

O exemplo a seguir gera C2990:

```
// C2990c.cpp
// compile with: /c
template<class T>
class A;

template<class T>
struct A2 {
   friend class A;   // C2990
};

// OK
template<class T>
struct B {
   template<class T>
   friend class A;
};
```