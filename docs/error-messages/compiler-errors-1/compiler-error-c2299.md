---
title: Erro do compilador C2299
ms.date: 11/04/2016
f1_keywords:
- C2299
helpviewer_keywords:
- C2299
ms.assetid: d001c2bc-f6fd-47aa-8e42-0eb824d6441d
ms.openlocfilehash: 39659baebf7dc1859a69021f60ed452964ae61af
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447952"
---
# <a name="compiler-error-c2299"></a>Erro do compilador C2299

'function': alteração de comportamento: uma especialização explícita não pode ser um construtor de cópia ou operador de atribuição de cópia

Esse erro também pode ser gerado como resultado do trabalho de conformidade do compilador que foi feito para o Visual Studio 2005: as versões anteriores do Visual C++ permitidas especializações explícitas para um construtor de cópia ou um operador de atribuição de cópia.

Para resolver C2299, não faça o construtor de cópia ou operador de atribuição de uma função de modelo, mas em vez disso, uma função não são de modelo que usa um tipo de classe. Qualquer código que chama o construtor de cópia ou operador de atribuição especificando explicitamente os argumentos de modelo precisa remover os argumentos do modelo.

O exemplo a seguir gera C2299:

```
// C2299.cpp
// compile with: /c
class C {
   template <class T>
   C (T t);

   template <> C (const C&);   // C2299
   C (const C&);   // OK
};
```