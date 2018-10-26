---
title: CXX0019 de erro do avaliador de expressão | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0019
dev_langs:
- C++
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f1e78bd88f35240e90332ef9a9139558051cab5
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070121"
---
# <a name="expression-evaluator-error-cxx0019"></a>Erro CXX0019 (avaliador de expressão)

conversão de tipo incorreto

O avaliador de expressão C não é possível executar a conversão como escrito de tipos.

Esse erro é idêntico ao CAN0019.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Para corrigir verificando as possíveis causas a seguir

1. O tipo especificado é desconhecido.

1. Havia muitos níveis de tipos de ponteiro. Por exemplo, a conversão de tipos

    ```
    (char **)h_message
    ```

   não pode ser avaliada pelo avaliador de expressão C.