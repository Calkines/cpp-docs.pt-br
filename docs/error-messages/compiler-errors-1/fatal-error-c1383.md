---
title: Erro fatal C1383
ms.date: 11/04/2016
f1_keywords:
- C1383
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
ms.openlocfilehash: 4ab96c0516ee5593a969669c03ae22f0c211ae27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208577"
---
# <a name="fatal-error-c1383"></a>Erro fatal C1383

opção de compilador /GL é incompatível com a versão instalada do common language runtime

C1383 ocorre quando você estiver usando uma versão anterior do common language runtime com um compilador mais recente e, quando você compila com **/clr** e **/GL.**

Para resolver, não use **/GL** com **/clr** ou instale a versão do common language runtime fornecido com o compilador.

Para obter mais informações, consulte [/clr (compilação de tempo de execução de linguagem comum)](../../build/reference/clr-common-language-runtime-compilation.md) e [/GL (otimização de programa inteiro)](../../build/reference/gl-whole-program-optimization.md).