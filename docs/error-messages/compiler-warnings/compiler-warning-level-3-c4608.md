---
title: Aviso do compilador (nível 3) C4608
ms.date: 11/04/2016
f1_keywords:
- C4608
helpviewer_keywords:
- C4608
ms.assetid: 8b8f5f28-8ce9-457e-9d3d-a8c0efce9b6a
ms.openlocfilehash: 4f1bef80b8cddccc036a5151bb4cc4ac01483a36
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401755"
---
# <a name="compiler-warning-level-3-c4608"></a>Aviso do compilador (nível 3) C4608

'union_member' já foi inicializado por outro membro de união na lista de inicializadores, 'union_member'

Dois membros da mesma união foram inicializados em uma lista de inicialização. Você pode acessar somente um membro da união.

O exemplo a seguir gera C4608:

```
// C4608.cpp
// compile with: /W3 /c
class X {
public:
   X(char c) : m_i( c + 1), m_c(c) {}   // C4608
   // try the following line instead
   // X(char c) : m_c(c) {}

private:
   union {
      int m_i;
      char m_c;
   };
};

union Y {
public:
   Y(char * name) : m_number(0.3), m_string( name ) {} // C4608

private:
   double m_number;
   char * m_string;
};
```