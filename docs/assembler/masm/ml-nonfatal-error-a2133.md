---
title: Erro não fatal A2133 (ML)
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2133
helpviewer_keywords:
- A2133
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
ms.openlocfilehash: 9e13dd48c77b9574229023e3cfc4cc2f2221d153
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62201204"
---
# <a name="ml-nonfatal-error-a2133"></a>Erro não fatal A2133 (ML)

**Registre-se o valor substituído por INVOKE**

Um registro foi passado como um argumento para um procedimento, mas o código gerado pelo [INVOKE](../../assembler/masm/invoke.md) passar outros argumentos destruídos o conteúdo do registro.

Os registros do AX, AL, AH, EAX, DX, DL, DH e EDX podem ser usados pelo assembler para realizar a conversão de dados.

Use um registro diferente.

## <a name="see-also"></a>Consulte também

[Mensagens de erro de ML](../../assembler/masm/ml-error-messages.md)<br/>