---
title: Erro do compilador C2803
ms.date: 11/04/2016
f1_keywords:
- C2803
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
ms.openlocfilehash: d20b8dde9f4134273adcba0f947f685f7ce7d213
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408518"
---
# <a name="compiler-error-c2803"></a>Erro do compilador C2803

'operator operador' deve ter pelo menos um parâmetro formal do tipo de classe

O operador sobrecarregado não tem um parâmetro de tipo de classe.

Você precisa passar pelo menos um parâmetro por referência (não usando ponteiros, mas as referências) ou por valor para ser capaz de gravar "um < b" (da classe de tipo A e b).

Se ambos os parâmetros forem ponteiros, ela será uma comparação pura de endereços de ponteiro e não usará a conversão definida pelo usuário.

O exemplo a seguir gera C2803:

```
// C2803.cpp
// compile with: /c
class A{};
bool operator< (const A *left, const A *right);   // C2803
// try the following line instead
// bool operator< (const A& left, const A& right);
```