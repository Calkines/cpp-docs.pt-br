---
title: Compilador aviso (nível 1) C4076
ms.date: 11/04/2016
f1_keywords:
- C4076
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
ms.openlocfilehash: 3a56e58d9bec1034a55f4e588dbddd0dba03f348
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208013"
---
# <a name="compiler-warning-level-1-c4076"></a>Compilador aviso (nível 1) C4076

> '*modificador de tipo*': não pode ser usado com o tipo '*typename*'

## <a name="remarks"></a>Comentários

Um modificador de tipo, seja **assinados** ou **unsigned**, não pode ser usado com um tipo não inteiro. *modificador de tipo* será ignorado.

## <a name="example"></a>Exemplo

O exemplo a seguir gera C4076; para corrigi-lo, remova os **sem sinal** modificador de tipo:

```cpp
// C4076.cpp
// compile with: /W1 /LD
unsigned double x;   // C4076
```