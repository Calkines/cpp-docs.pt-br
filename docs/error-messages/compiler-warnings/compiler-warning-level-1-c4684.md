---
title: Compilador aviso (nível 1) C4684
ms.date: 11/04/2016
f1_keywords:
- C4684
helpviewer_keywords:
- C4684
ms.assetid: e95f1a83-2784-4b05-ae94-12148e056e26
ms.openlocfilehash: 8ba3d75ecb370ac86c9a6ab47f05dd49fc12ba23
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374398"
---
# <a name="compiler-warning-level-1-c4684"></a>Compilador aviso (nível 1) C4684

'attribute': AVISO!! atributo pode causar a geração de código inválido: use com cuidado

Você usou um atributo que não deve ser usado com frequência.

O exemplo a seguir gera C4684:

```
// C4684.cpp
// compile with: /W1 /LD
[module(name="xx")]; // C4684 expected
[no_injected_text];
```