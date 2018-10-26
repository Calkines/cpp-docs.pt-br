---
title: Diretivas de pré-processador | Microsoft Docs
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- directives, preprocessor
- preprocessor, directives
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2976feebf4a17465c2bf2010b4dc608550ce077
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059461"
---
# <a name="preprocessor-directives"></a>Diretivas de pré-processador

Diretivas de pré-processador, como `#define` e `#ifdef`, normalmente são usados para tornar os programas de origem fáceis de alterar e compilar em diferentes ambientes de execução. As políticas no arquivo de origem mandam o pré-processador realizar ações específicas. Por exemplo, o pré-processador pode substituir tokens no texto, inserir o conteúdo de outros arquivos no arquivo de origem ou suprimir a compilação de parte do arquivo removendo seções de texto. As linhas do pré-processador são reconhecidas e executadas antes de expansão macro. Portanto, se uma macro se expandir até algo que se pareça com um comando do pré-processador, esse comando não será reconhecido pelo pré-processador.

As instruções do pré-processador usam o mesmo conjunto de caracteres das instruções de arquivo de origem, com exceção das sequências de escape, que não têm suporte. O conjunto de caracteres usado em instruções do pré-processador é igual ao conjunto de caracteres de execução. O pré-processador também reconhece valores negativos de caracteres.

O pré-processador reconhece as políticas a seguir:

|||||
|-|-|-|-|
|[#define](../preprocessor/hash-define-directive-c-cpp.md)|[#error](../preprocessor/hash-error-directive-c-cpp.md)|[#import](../preprocessor/hash-import-directive-cpp.md)|[#undef](../preprocessor/hash-undef-directive-c-cpp.md)|
|[#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#include](../preprocessor/hash-include-directive-c-cpp.md)|[#using](../preprocessor/hash-using-directive-cpp.md)|
|[#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#line](../preprocessor/hash-line-directive-c-cpp.md)|[#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|
|[#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||

O sinal de número (**#**) deve ser o primeiro caractere diferente de espaço na linha que contém a política; os caracteres de espaço em branco podem aparecer entre o sinal de número e a primeira letra da diretiva. Algumas políticas incluem argumentos ou valores. Qualquer texto que segue uma política (exceto um argumento ou um valor que é parte da diretiva) deve ser precedido pelo delimitador de comentário de linha única (**//**) ou ser incluído em delimitadores de comentário ( __/ \*\*/__). Linhas que contêm diretivas de pré-processador podem ser continuadas, imediatamente, precedendo o marcador de fim de linha com uma barra invertida (**\\**).

As políticas do pré-processador podem aparecer em qualquer lugar do arquivo de origem, mas se aplicam somente ao restante dele.

## <a name="see-also"></a>Consulte também

[Operadores de pré-processador](../preprocessor/preprocessor-operators.md)<br/>
[Macros predefinidas](../preprocessor/predefined-macros.md)<br/>
[Referência de pré-processador do C/C++](../preprocessor/c-cpp-preprocessor-reference.md)
