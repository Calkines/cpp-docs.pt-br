---
title: (Níveis 2 e 4) de aviso do compilador C4200
ms.date: 11/04/2016
f1_keywords:
- C4200
helpviewer_keywords:
- C4200
ms.assetid: e44d6073-937f-42b7-acc1-65e802b475c6
ms.openlocfilehash: 56a2ba641df610519949f64f6feeca18d9a99e93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359950"
---
# <a name="compiler-warning-levels-2-and-4-c4200"></a>(Níveis 2 e 4) de aviso do compilador C4200

extensão não padrão usada: matriz de tamanho zero na estrutura/união

Indica que uma estrutura ou união contém uma matriz de tamanho zero.

A declaração de uma matriz de tamanho zero é uma extensão da Microsoft. Isso causa um aviso de nível 2 quando um arquivo C++ é compilado e um aviso de nível 4 quando um arquivo C é compilado. C++compilação também fornece esse aviso: "Não é possível gerar operador construtor de cópia ou atribuição de cópia quando UDT tiver uma matriz de tamanho zero". Este exemplo gera um aviso C4200:

```cpp
// C4200.cpp
// compile by using: cl /W4 c4200.cpp
struct A {
    int a[0];  // C4200
};
int main() {
}
```

Essa extensão não padrão geralmente é usada para código da interface com estruturas de dados externos que têm um comprimento variável. Se esse cenário se aplicar ao seu código, você pode desabilitar o aviso:

## <a name="example"></a>Exemplo

```cpp
// C4200b.cpp
// compile by using: cl /W4 c4200a.cpp
#pragma warning(disable : 4200)
struct A {
    int a[0];
};
int main() {
}
```