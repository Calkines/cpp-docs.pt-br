---
title: Erro CXX0030 (avaliador de expressão)
ms.date: 11/04/2016
f1_keywords:
- CXX0030
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
ms.openlocfilehash: 1e52b238905fba5c310a89377b81548a1c6b5784
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359794"
---
# <a name="expression-evaluator-error-cxx0030"></a>Erro CXX0030 (avaliador de expressão)

expressão não evaluatable

O avaliador de expressão do depurador não foi possível obter um valor para a expressão como escrito. Uma causa provável é que a expressão se refere a memória que está fora do espaço de endereço do programa (desreferenciar um ponteiro nulo é um exemplo). Windows não permitem acesso à memória que está fora do espaço de endereço do programa.

Você talvez queira reescrever seu usando parênteses para controlar a ordem de avaliação de expressão.

Esse erro é idêntico ao CAN0030.