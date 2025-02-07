---
title: Erro do compilador C2626
ms.date: 11/04/2016
f1_keywords:
- C2626
helpviewer_keywords:
- C2626
ms.assetid: 4c283ad0-251b-4571-bc18-468b9836746f
ms.openlocfilehash: 434858991c23345e2a6c174c8f323000d42b9b6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222878"
---
# <a name="compiler-error-c2626"></a>Erro do compilador C2626

'identifier': um membro de dados particular ou protegido não é permitido em um struct anônimo ou uma união

Um membro de um struct anônimo ou de união deve ter acesso público.

O exemplo a seguir gera C2626:

```
// C2626.cpp
int main() {
   union {
   protected:
      int j;     // C2626, j is protected
   private:
      int k;     // C2626, k is private
   };
}
```

Para corrigir esse problema, remova todas as marcas de particulares ou protegidas:

```
// C2626b.cpp
int main() {
   union {
   public:
      int i;   // OK, i is public
   };
}
```