---
title: Erro fatal C1352
ms.date: 11/04/2016
f1_keywords:
- C1352
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
ms.openlocfilehash: fbba87cea05d666d6dc3a385ca1fe52e143fdb5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329719"
---
# <a name="fatal-error-c1352"></a>Erro fatal C1352

MSIL inválido ou corrompido na função 'function' do módulo 'file'

Um. netmodule foi passado para o compilador, mas o compilador detectou corrupção no arquivo.  Peça à pessoa que produziu o. netmodule para investigar.

O compilador não verifica os arquivos. netmodule para todos os tipos de corrupção.  No entanto, ele, verifique todos os caminhos de controle em uma função contêm uma instrução return.

Para obter mais informações, consulte [arquivos. netmodule como entrada de vinculador](../../build/reference/netmodule-files-as-linker-input.md).