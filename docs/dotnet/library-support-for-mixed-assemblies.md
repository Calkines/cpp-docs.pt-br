---
title: Suporte de biblioteca para Assemblies mistos | Microsoft Docs
ms.custom: ''
ms.date: 09/18/2018
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8c3fec26f3e41c3edd2346ac2e1b9b1f6b98ba33
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069614"
---
# <a name="library-support-for-mixed-assemblies"></a>Suporte de biblioteca para assemblies mistos

Visual C++ oferece suporte ao uso da biblioteca padrão C++, a biblioteca de tempo de execução C (CRT), ATL e MFC para aplicativos compilados com [/clr (compilação de tempo de execução de linguagem comum)](../build/reference/clr-common-language-runtime-compilation.md). Isso permite que os aplicativos existentes que usam essas bibliotecas para usar recursos do .NET Framework também.

> [!IMPORTANT]
> O **/clr: pure** e **/CLR: safe** opções do compilador são preteridas no Visual Studio 2015 e sem suporte no Visual Studio 2017.

Esse suporte inclui as seguintes bibliotecas de importação e de DLL:

- . Lib de Msvcmrt [d] se você compilar com **/clr**. Link de assemblies mistos para essa biblioteca de importação.

Esse suporte fornece que vários benefícios relacionados ao:

- A CRT e a biblioteca padrão C++ estão disponíveis para código misto. A CRT e a biblioteca padrão do C++ fornecidos não são verificáveis; em última análise, suas chamadas ainda são roteadas para o CRT mesmo e a biblioteca padrão C++ conforme a utilização do código nativo.

- Corrija a manipulação de exceção unificada em imagens mistas.

- Inicialização estática de variáveis de C++ em imagens mistas.

- Suporte para variáveis per-AppDomain e por processo em código gerenciado.

- Resolve os problemas de bloqueio do carregador aplicado às DLLs mistas compilados no Visual Studio 2003 e versões anteriores.

Além disso, esse suporte apresenta as seguintes limitações:

- Somente o modelo de DLL do CRT é compatível para o código compilado com **/clr**. Não há nenhuma biblioteca de CRT estática que dão suporte a **/clr** compilações.

## <a name="see-also"></a>Consulte também

- [Assemblies mistos (nativos e gerenciados)](../dotnet/mixed-native-and-managed-assemblies.md)
