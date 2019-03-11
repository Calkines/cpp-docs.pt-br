---
title: Erro fatal C1076
ms.date: 03/08/2019
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: 91753a49498548b4e523cd8564ee7a7ca7a3b373
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751668"
---
# <a name="fatal-error-c1076"></a>Erro fatal C1076

> limite do compilador: limite do heap interno atingido; use /Zm para especificar um limite maior

Esse erro pode ser causado por muitos símbolos ou por muitas instanciações do modelo. A partir do Visual Studio 2015, essa mensagem pode resultar de pressão de memória virtual do Windows causado por muitos processos de build paralelo. Nesse caso, a recomendação para usar o **/Zm** opção deve ser ignorada, a menos que você estiver usando um `#pragma hdrstop` diretiva.

Para resolver esse erro:

1. Se o cabeçalho pré-compilado usa um `#pragma hdrstop` diretriz, use o [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) opção para definir o limite de memória do compilador como o valor especificado no [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) mensagem de erro. Para obter mais informações sobre como definir esse valor no Visual Studio, consulte a seção comentários no [/Zm (especificar pré-compilado cabeçalho alocação de limite de memória)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).

1. Considere reduzir o número de processos paralelos especificado usando o **/maxcpucount** opção para MSBUILD. EXE em conjunto com o **/MP** opção para CL. EXE. Para obter mais informações, consulte [problemas de cabeçalho pré-compilado (PCH) e recomendações](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/).

1. Se você estiver usando os compiladores hospedados de 32 bits em um sistema operacional de 64 bits, use os compiladores hospedados de 64 bits. Para obter mais informações, confira [Como: Habilitar um 64-Bit Visual C++ conjunto de ferramentas na linha de comando](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. Elimine arquivos de inclusão desnecessários.

1. Elimine variáveis globais desnecessárias, por exemplo, alocando memória dinamicamente em vez de declarar uma matriz grande.

1. Elimine declarações não usadas.

Se C1076 ocorrer imediatamente após o build é iniciado, o valor especificado para **/Zm** provavelmente é muito alto para o seu programa. Reduzir a **/Zm** valor.