---
title: Erro do compilador C2333
ms.date: 11/04/2016
f1_keywords:
- C2333
helpviewer_keywords:
- C2333
ms.assetid: 2636fc1e-d3e7-4e68-8628-3c81a99ba813
ms.openlocfilehash: e9119a8375a276a59cbf3a6db9541f6ccaef5122
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300809"
---
# <a name="compiler-error-c2333"></a>Erro do compilador C2333

'function': erro na declaração de função; Ignorando o corpo da função

Esse erro ocorre após o outro erro, para funções de membro definida dentro de sua classe.

O exemplo a seguir gera C2333:

```
// C2333.cpp
struct s1 {
   s1(s1) {}   // C2333
};
```