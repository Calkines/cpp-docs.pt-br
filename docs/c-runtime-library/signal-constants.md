---
title: Constantes de sinal
ms.date: 11/04/2016
f1_keywords:
- SIGTERM
- SIGFPE
- SIGABRT
- SIGILL
- SIGINT
- SIGSEGV
helpviewer_keywords:
- SIGTERM constant
- SIGABRT constant
- SIGSEGV constant
- SIGFPE constant
- SIGINT constant
- signal constants
- SIGILL constant
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
ms.openlocfilehash: e9953e967d1c94ae56dfc1063fb0deafa342631c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738721"
---
# <a name="signal-constants"></a>Constantes de sinal

## <a name="syntax"></a>Sintaxe

```
#include <signal.h>
```

## <a name="remarks"></a>Comentários

O argumento `sig` deve ser uma das constantes de manifesto listadas abaixo (definidas no SIGNAL.H).

|||
|-|-|
|SIGABRT|Encerramento anormal. A ação padrão encerra o programa de chamada com o código de saída 3.  |
|SIGABRT_COMPAT|Mesmo que SIGABRT. Para compatibilidade com outras plataformas.  |
|SIGFPE|Erro de ponto flutuante, como estouro, divisão por zero ou operação inválida. A ação padrão encerra o programa de chamada.  |
|SIGILL|Instrução ilegal. A ação padrão encerra o programa de chamada.  |
|SIGINT|Interrupção CTRL+C. A ação padrão encerra o programa de chamada com o código de saída 3.  |
|SIGSEGV|Acesso ao armazenamento inválido. A ação padrão encerra o programa de chamada.  |
|SIGTERM|Solicitação de término enviada para o programa. A ação padrão encerra o programa de chamada com o código de saída 3.  |
|SIG_ERR|Um tipo de retorno de um sinal que indica que um erro ocorreu.  |

## <a name="see-also"></a>Consulte também

[signal](../c-runtime-library/reference/signal.md)<br/>
[raise](../c-runtime-library/reference/raise.md)<br/>
[Constantes globais](../c-runtime-library/global-constants.md)
