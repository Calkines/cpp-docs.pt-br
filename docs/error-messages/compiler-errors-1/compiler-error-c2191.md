---
title: Erro do compilador C2191
ms.date: 11/04/2016
f1_keywords:
- C2191
helpviewer_keywords:
- C2191
ms.assetid: 051b8350-e5de-4f51-ab6e-96d32366bcef
ms.openlocfilehash: 23dfe1d95ab75f253fc2a7b4b00dfcd1aaaa3bbf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302963"
---
# <a name="compiler-error-c2191"></a>Erro do compilador C2191

segunda lista de parâmetros mais do que a primeira

Uma função C foi declarada uma segunda vez com uma lista mais longa do parâmetro. C não oferece suporte a funções sobrecarregadas.

## <a name="example"></a>Exemplo

O exemplo a seguir gera C2191:

```
// C2191.c
// compile with: /Za /c
void func( int );
void func( int, float );   // C2191 different parameter list
void func2( int, float );   // OK
```