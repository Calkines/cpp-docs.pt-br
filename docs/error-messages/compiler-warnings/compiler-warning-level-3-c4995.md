---
title: Compilador aviso (nível 3) C4995
ms.date: 11/04/2016
f1_keywords:
- C4995
helpviewer_keywords:
- C4995
ms.assetid: c6b61755-4730-4947-ad4d-d1c2bc82585a
ms.openlocfilehash: 54bc8931b5eaa3bbb5053e5c21aa2aaaa73126fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401508"
---
# <a name="compiler-warning-level-3-c4995"></a>Compilador aviso (nível 3) C4995

'function': nome foi marcado como #pragma preterido

O compilador encontrou uma função que foi marcada com o pragma [preterido](../../preprocessor/deprecated-c-cpp.md). A função pode não ter mais suporte em uma versão futura. Você pode desativar esse aviso com a [aviso](../../preprocessor/warning.md) pragma (exemplo abaixo).

## <a name="example"></a>Exemplo

O exemplo a seguir gera C4995:

```
// C4995.cpp
// compile with: /W3
#include <stdio.h>

// #pragma warning(disable : 4995)
void func1(void)
{
    printf("\nIn func1");
}

int main()
{
    func1();
    #pragma deprecated(func1)
    func1();   // C4995
}
```