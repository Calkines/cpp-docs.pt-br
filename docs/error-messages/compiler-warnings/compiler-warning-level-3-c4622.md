---
title: Compilador aviso (nível 3) C4622
ms.date: 11/04/2016
f1_keywords:
- C4622
helpviewer_keywords:
- C4622
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
ms.openlocfilehash: 88a41c7f9edb1d2a9f6d4547336a77bd5e362882
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401742"
---
# <a name="compiler-warning-level-3-c4622"></a>Compilador aviso (nível 3) C4622

substituindo informação de depuração formada durante a criação de cabeçalho pré-compilado no arquivo de objeto: 'file'

Informações de CodeView no arquivo especificado foram perdidas quando ele foi compilado com o [/Yu](../../build/reference/yu-use-precompiled-header-file.md) opção (usar cabeçalho pré-compilado).

Renomeie o arquivo de objeto (usando [/Fo](../../build/reference/fo-object-file-name.md)) ao criar ou usando o cabeçalho pré-compilado do arquivo e fornecer um link usando o novo arquivo de objeto.