---
title: Erro do compilador C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: e4d52946126e7be6c6f2aef34b5eb5a93a0babad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187373"
---
# <a name="compiler-error-c3888"></a>Erro do compilador C3888

'name': a expressão const associada a este membro de dados literal não é suportada pelo C++/CLI

O *nome* membro de dados que é declarado com o [literal](../../extensions/literal-cpp-component-extensions.md) palavra-chave é inicializada com um valor que o compilador não oferece suporte. O compilador suporta apenas constante integral, enum ou tipos de cadeia de caracteres. A causa provável para o **C3888** erro é que o membro de dados é inicializado com uma matriz de bytes.

### <a name="to-correct-this-error"></a>Para corrigir este erro

1. Verifique se o membro de dados literal declarado é um tipo com suporte.

## <a name="see-also"></a>Consulte também

[literal](../../extensions/literal-cpp-component-extensions.md)