---
title: Erro do compilador C3457
ms.date: 11/04/2016
f1_keywords:
- C3457
helpviewer_keywords:
- C3457
ms.assetid: 5c1e366a-fa75-4cca-b9a3-86d4ebe4090e
ms.openlocfilehash: 813b1c085cb0464880cb400b6200f9574220bd71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363720"
---
# <a name="compiler-error-c3457"></a>Erro do compilador C3457

'attribute': atributo não suporta argumentos sem nome

Atributos de anotação de origem, ao contrário de atributo personalizados de CLR ou atributos de compilador, só há suporte para argumentos nomeados.

## <a name="example"></a>Exemplo

O exemplo a seguir gera C3457.

```
#include "SourceAnnotations.h"
[vc_attributes::Post( 1 )] int f();   // C3457
[vc_attributes::Post( Valid=vc_attributes::Yes )] int f2();   // OK
```