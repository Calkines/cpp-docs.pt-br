---
title: Especialização explícita de modelos de função
ms.date: 11/04/2016
helpviewer_keywords:
- overriding, functions
- function templates, specialization
- explicit specialization of function templates
- declaring functions [C++], specialization of function template
- specialization of function templates
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
ms.openlocfilehash: 3d91383f895f1a8be983efe42f685419ca988823
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184261"
---
# <a name="explicit-specialization-of-function-templates"></a>Especialização explícita de modelos de função

Com um modelo de função, você pode definir o comportamento especial para um tipo específico fornecendo uma especialização explícita (substituição) do modelo da função para esse tipo. Por exemplo:

```cpp
template<> void MySwap(double a, double b);
```

Esta declaração permite que você defina uma função diferente para **duplas** variáveis. Assim como as funções de não template, conversões de tipo padrão (como a promoção de uma variável do tipo **float** à **duplo**) são aplicadas.

## <a name="example"></a>Exemplo

```cpp
// explicit_specialization.cpp
template<class T> void f(T t)
{
};

// Explicit specialization of f with 'char' with the
// template argument explicitly specified:
//
template<> void f<char>(char c)
{
}

// Explicit specialization of f with 'double' with the
// template argument deduced:
//
template<> void f(double d)
{
}
int main()
{
}
```

## <a name="see-also"></a>Consulte também

[Modelos de função](../cpp/function-templates.md)