---
title: Compilador aviso (nível 1) C4659
ms.date: 11/04/2016
f1_keywords:
- C4659
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
ms.openlocfilehash: 2aef25e922d8f38ac7103b1b12ccb31c282f0403
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374645"
---
# <a name="compiler-warning-level-1-c4659"></a>Compilador aviso (nível 1) C4659

\#pragma 'pragma': uso de segmento reservado 'segmento' possui comportamento indefinido, use #pragma comment (linker,...)

A opção .drectve foi usada para passar uma opção para o vinculador. Em vez disso, usar o pragma [comentário](../../preprocessor/comment-c-cpp.md) para passar uma opção de vinculador.

```
// C4659.cpp
// compile with: /W1 /LD
#pragma code_seg(".drectve")   // C4659
```