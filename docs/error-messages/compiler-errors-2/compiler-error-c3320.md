---
title: Erro do compilador C3320
ms.date: 11/04/2016
f1_keywords:
- C3320
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
ms.openlocfilehash: 622e7366dda4cd6693d9b6128855fa0966e07952
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222473"
---
# <a name="compiler-error-c3320"></a>Erro do compilador C3320

'type': tipo não pode ter o mesmo nome que a propriedade de 'name' do módulo

Um exportado-tipo definido pelo usuário (UDT), que pode ser um struct, classe, enum ou união, não pode ter o mesmo nome como o parâmetro passado para o [módulo](../../windows/module-cpp.md) propriedade de nome do atributo.

## <a name="example"></a>Exemplo

O exemplo a seguir gera uma C3320:

```cpp
// C3320.cpp
#include "unknwn.h"
[module(name="xx")];

[export] struct xx {   // C3320
// Try the following line instead
// [export] struct yy {
   int i;
};
```