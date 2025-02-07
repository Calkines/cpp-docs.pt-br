---
title: Avaliação de tokens
ms.date: 11/04/2016
helpviewer_keywords:
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
ms.openlocfilehash: 15775ca9a7ada46aaf4e53ae952cd67e95bbf8d3
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152541"
---
# <a name="evaluation-of-tokens"></a>Avaliação de tokens

Quando o compilador interpreta tokens, ele inclui o máximo de caracteres possível em um único token antes seguir para o próximo token. Devido a esse comportamento, o compilador pode não interpretar tokens como você gostaria se eles não forem separados corretamente por um espaço em branco. Considere a seguinte expressão:

```
i+++j
```

Neste exemplo, o compilador primeiro cria o operador mais longo possível (`++`) dos três sinais positivos, depois processa o sinal de positivo restante como um operador de adição (`+`). Assim, a expressão é interpretada como `(i++) + (j)`, não `(i) + (++j)`. Nesse e em casos semelhantes, use espaço em branco e parênteses para evitar ambiguidade e assegurar a avaliação apropriada da expressão.

**Seção específica da Microsoft**

O compilador C trata um caractere CTRL+Z como um indicador de fim do arquivo. Ignora qualquer texto após CTRL+Z.

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[Tokens C](../c-language/c-tokens.md)
