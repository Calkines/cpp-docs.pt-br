---
title: Propriedades gerais (Projeto do Linux C++) | Microsoft Docs
ms.date: 9/26/2017
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: bc4eb39d2d735f8f7f782d2827bf2b938c5c2457
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461328"
---
# <a name="general-properties-linux-c"></a>Propriedades gerais (Linux C++)

Propriedade | Descrição | Opções
--- | ---| ---
Diretório de saída | Especifica um caminho relativo para o diretório de arquivo de saída e pode incluir variáveis de ambiente.
Diretório intermediário | Especifica um caminho relativo para o diretório de arquivo intermediário e pode incluir variáveis de ambiente.
Nome de Destino | Especifica um nome de arquivo que será gerado por este projeto.
Extensão de Destino | Especifica uma extensão de arquivo que será gerada por este projeto. (Exemplo: .a)
Extensões a serem Excluídas na Limpeza | Especificação de curinga delimitado por ponto e vírgula para os arquivos no diretório intermediário que deverão ser excluídos na limpeza ou na recompilação.
Arquivo de log de build | Especifica o arquivo de log de build para gravação quando o registro em log de build está habilitado.
Conjunto de ferramentas da plataforma | Especifica o conjunto de ferramentas utilizado para compilar a configuração atual; se não tiver sido definido, o conjunto de ferramentas padrão é utilizado
Computador de Build Remoto | O computador ou dispositivo de destino a ser usado para build, implantação e depuração remotos.
Diretório Raiz de Build Remoto | Especifica um caminho para um diretório no computador ou dispositivo remoto.
Diretório de Projeto de Build Remoto | Especifica um caminho para um diretório no computador ou dispositivo remoto para o projeto.
Tipo de Configuração | Especifica o tipo de saída gerado por essa configuração. | **Biblioteca dinâmica (.so)** – Biblioteca dinâmica (.so)<br>**Biblioteca estática (.a)** – Biblioteca Estática (.a)<br>**Aplicativo (.out)** – Aplicativo (.out)<br>**Makefile** – Makefile<br>
Uso de STL | Especifica qual Biblioteca Padrão C++ deve ser usada para essa configuração. | **Biblioteca C++ Padrão do GNU Compartilhado**<br>**Biblioteca C++ Padrão do GNU Estático (-static)**<br>
