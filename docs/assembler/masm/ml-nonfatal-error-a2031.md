---
title: Erro não fatal A2031 (ML)
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2031
helpviewer_keywords:
- A2031
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
ms.openlocfilehash: 794fb31fbc22bdefddf9f19e6efcb3c34bbc1861
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62177676"
---
# <a name="ml-nonfatal-error-a2031"></a>Erro não fatal A2031 (ML)

**deve ser o índice ou a base de dados de registro**

Foi feita uma tentativa para usar um registro que não era um registro de base ou índice em uma expressão de memória.

Por exemplo, as expressões a seguir causam esse erro:

```asm
[ax]
[bl]
```

## <a name="see-also"></a>Consulte também

[Mensagens de erro de ML](../../assembler/masm/ml-error-messages.md)<br/>