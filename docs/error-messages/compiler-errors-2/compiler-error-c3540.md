---
title: Erro do compilador C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: 57e4145557272f76a890a356c79982346cd74d7e
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345476"
---
# <a name="compiler-error-c3540"></a>Erro do compilador C3540

'type': sizeof não pode ser aplicado a um tipo que contenha 'auto'

O [sizeof](../../cpp/sizeof-operator.md) operador não pode ser aplicado para o tipo indicado, porque ela contém o `auto` especificador.

## <a name="example"></a>Exemplo

O exemplo a seguir produz C3540.

```
// C3540.cpp
// Compile with /Zc:auto
int main() {
    auto x = 123;
    sizeof(x);    // OK
    sizeof(auto); // C3540
    return 0;
}
```

## <a name="see-also"></a>Consulte também

[Palavra-chave auto](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (deduzir tipo de variável)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[Operador sizeof](../../cpp/sizeof-operator.md)