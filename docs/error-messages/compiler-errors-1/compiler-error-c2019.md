---
title: Erro do compilador C2019
ms.date: 11/04/2016
f1_keywords:
- C2019
helpviewer_keywords:
- C2019
ms.assetid: 4f37b1e1-9eca-418f-a4c3-141e8512d7b6
ms.openlocfilehash: 6e9e5bbca5da13fdfd4727d3b19aa3656689ce96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303704"
---
# <a name="compiler-error-c2019"></a>Erro do compilador C2019

esperada diretiva de pré-processador, encontrado 'character'

O caractere seguido um `#` logon, mas isso não é a primeira letra de uma diretiva de pré-processador.

O exemplo a seguir gera C2019:

```
// C2019.cpp
#!define TRUE 1   // C2019
```

Solução possível:

```
// C2019b.cpp
// compile with: /c
#define TRUE 1
```