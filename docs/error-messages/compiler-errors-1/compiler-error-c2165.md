---
title: Erro do compilador C2165
ms.date: 11/04/2016
f1_keywords:
- C2165
helpviewer_keywords:
- C2165
ms.assetid: b108313b-b8cb-4dce-b2ec-f2b31c9cdc87
ms.openlocfilehash: 1dadc56dafca056db9b4a14ab39127306b797f8a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174751"
---
# <a name="compiler-error-c2165"></a>Erro do compilador C2165

'palavra-chave': não é possível modificar ponteiros para os dados

O `__stdcall`, `__cdecl`, ou `__fastcall` palavra-chave tenta modificar um ponteiro para dados.

O exemplo a seguir gera C2165:

```
// C2165.cpp
// compile with: /c
char __cdecl *p;   // C2165
char *p;   // OK
```