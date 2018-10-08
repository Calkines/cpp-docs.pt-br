---
title: C R6019 de erro de tempo de execução | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6019
dev_langs:
- C++
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13653f54551501d5e35bd1285dc3d3f1a74343f1
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861585"
---
# <a name="c-runtime-error-r6019"></a>C R6019 de erro de tempo de execução

não é possível abrir o dispositivo do console

> [!NOTE]
> Se você encontrar esta mensagem de erro durante a execução de um aplicativo, o aplicativo foi encerrado porque ele tentou acessar o console, mas ele não tinha permissão suficiente. Há várias razões possíveis para esse erro, mas é normalmente porque o programa deve ser executado como um administrador, ou há um bug no programa.
>
> Você pode tentar corrigir esse erro com estas etapas:
>
> - Execute o programa como administrador.
> - Use o **aplicativos e recursos** ou **programas e recursos** página o **painel de controle** para reparar ou reinstalar o programa.
> - Verifique **Windows Update** na **painel de controle** para atualizações de software.
> - Verifique se há uma versão atualizada do aplicativo. Se o problema persistir, entre em contato com o fornecedor do aplicativo.

**Informações para programadores**

Esse erro ocorre porque o aplicativo de chamada de função de console, mas o sistema operacional não conceder acesso ao console. Exceto no modo de depuração, console funções geralmente não são permitidas em aplicativos da Microsoft Store. Se seu aplicativo requer privilégios de administrador para ser executado, verifique se que ele é instalado para ser executado como administrador por padrão.