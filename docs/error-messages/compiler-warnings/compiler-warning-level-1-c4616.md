---
title: Compilador aviso (nível 1) C4616
ms.date: 11/04/2016
f1_keywords:
- C4616
helpviewer_keywords:
- C4616
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
ms.openlocfilehash: d63e1abffce617a48ac1a5cd8c61feba941b31ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221346"
---
# <a name="compiler-warning-level-1-c4616"></a>Compilador aviso (nível 1) C4616

\#Aviso de Pragma: número de aviso 'number' não um aviso do compilador válido

O número de aviso especificado na [aviso](../../preprocessor/warning.md) pragma não pode ser reatribuído. O pragma foi ignorado.

O exemplo a seguir gera C4616:

```
// C4616.cpp
// compile with: /W1 /c
#pragma warning( disable : 0 )   // C4616
#pragma warning( disable : 999 )   // OK
#pragma warning( disable : 4998 )   // OK
```