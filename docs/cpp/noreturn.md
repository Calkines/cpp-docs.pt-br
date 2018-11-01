---
title: noreturn
ms.date: 11/04/2016
f1_keywords:
- noreturn_cpp
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
ms.openlocfilehash: 1d78e8f5116eabf9073205b938156197bf1001a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611855"
---
# <a name="noreturn"></a>noreturn

## <a name="microsoft-specific"></a>Específico da Microsoft

Isso **declspec** atributo diz ao compilador que uma função não retorna. Como consequência, o compilador sabe que o código que segue uma chamada para um **__declspec(noreturn)** função está inacessível.

Se o compilador encontra uma função com um caminho de controle que não retorna um valor, ele gera um aviso (C4715) ou uma mensagem de erro (C2202). Se o caminho de controle não pode ser acessado devido a uma função que nunca retorna, você pode usar **__declspec(noreturn)** para evitar esse aviso ou erro.

> [!NOTE]
>  Adicionando **__declspec(noreturn)** para uma função que deve retornar pode resultar em comportamento indefinido.

## <a name="example"></a>Exemplo

No exemplo a seguir, o **else** cláusula não contém uma instrução return.  Declarando `fatal` como **__declspec(noreturn)** evita uma mensagem de aviso ou erro.

```cpp
// noreturn2.cpp
__declspec(noreturn) extern void fatal () {}

int main() {
   if(1)
     return 1;
   else if(0)
     return 0;
   else
     fatal();
}
```

## <a name="see-also"></a>Consulte também

[__declspec](../cpp/declspec.md)<br/>
[Palavras-chave](../cpp/keywords-cpp.md)