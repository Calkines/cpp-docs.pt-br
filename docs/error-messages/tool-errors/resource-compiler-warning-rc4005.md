---
title: Aviso RC4005 (compilador de recurso)
ms.date: 11/04/2016
f1_keywords:
- RC4005
helpviewer_keywords:
- RC4005
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
ms.openlocfilehash: 571c4ac285e9477b017dbc21cf9ff733539759d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62346178"
---
# <a name="resource-compiler-warning-rc4005"></a>Aviso RC4005 (compilador de recurso)

'identifier': redefinição de macro

O identificador está definido duas vezes. O compilador usado a segunda definição de macro.

Esse aviso pode ser causado por definindo uma macro na linha de comando e no código com um `#define` diretiva. Ele também pode ser causado por macros importadas de arquivos de inclusão.

Para eliminar o aviso, remova uma das definições ou use um `#undef` diretiva antes da definição de segundo.