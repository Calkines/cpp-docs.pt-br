---
title: Compilador aviso (nível 1) C4508
ms.date: 11/04/2016
f1_keywords:
- C4508
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
ms.openlocfilehash: c96db3d4bd1124c96b22363531b7739d0757b613
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160803"
---
# <a name="compiler-warning-level-1-c4508"></a>Compilador aviso (nível 1) C4508

'function': função deve retornar um valor; supõe-se de tipo de retorno 'void'

A função não tem nenhum tipo de retorno especificado. Nesse caso, também deve ser disparado C4430 e o compilador implementa a correção relatada pelo C4430 (o valor padrão é int).

Para resolver este aviso, declare explicitamente o tipo de retorno de funções.

O exemplo a seguir gera C4508:

```
// C4508.cpp
// compile with: /W1 /c
#pragma warning (disable : 4430)
func() {}   // C4508
void func2() {}   // OK
```