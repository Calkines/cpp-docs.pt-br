---
title: Erro fatal C1107
ms.date: 11/04/2016
f1_keywords:
- C1107
helpviewer_keywords:
- C1107
ms.assetid: 541a4d9f-10bc-4dd8-b68e-15e548f3dc0a
ms.openlocfilehash: 135e8da1b49eb1d86f6186e8683ced2f5152a3a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257758"
---
# <a name="fatal-error-c1107"></a>Erro fatal C1107

não foi possível encontrar o assembly 'file': especifique o caminho de pesquisa de assembly usando /AI ou definindo a variável de ambiente LIBPATH

Um arquivo de metadados foi passado para um [#using](../../preprocessor/hash-using-directive-cpp.md) diretiva que o compilador não pôde localizar.

LIBPATH, que é descrito no tópico de `#using`e o [/AI](../../build/reference/ai-specify-metadata-directories.md) opção de compilador permitem que você especifique os diretórios em que o compilador procurará arquivos de metadados referenciados.