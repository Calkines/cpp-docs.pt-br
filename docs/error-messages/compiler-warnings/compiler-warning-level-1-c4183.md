---
title: Compilador aviso (nível 1) C4183
ms.date: 11/04/2016
f1_keywords:
- C4183
helpviewer_keywords:
- C4183
ms.assetid: dc48312c-4b34-44dd-80ff-eb5f11d5ca47
ms.openlocfilehash: 0d947a0f6d777a5ed3191d6d232a604028be2003
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391615"
---
# <a name="compiler-warning-level-1-c4183"></a>Compilador aviso (nível 1) C4183

'identifier': faltando tipo de retorno; presume-se que uma função membro retornando 'int'

A definição embutida de uma função de membro em uma classe ou uma estrutura não tem um tipo de retorno. Essa função membro é considerada para ter um padrão de tipo de retorno de `int`.

O exemplo a seguir gera C4183:

```
// C4183.cpp
// compile with: /W1 /c
#pragma warning(disable : 4430)
class MyClass1;
class MyClass2 {
   MyClass1() {};   // C4183
};
```