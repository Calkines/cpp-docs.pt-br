---
title: Tipos de função
ms.date: 11/04/2016
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
ms.openlocfilehash: 22778f3eaefa6dbcf5f85e54c0940867ef52ab72
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526325"
---
# <a name="function-types"></a>Tipos de função

Existem basicamente dois tipos de funções. Uma função que requer um quadro de pilha é chamada de função do quadro. Uma função que não exige um quadro de pilha é chamada de função de folha.

Uma função de quadro é uma função que aloca espaço em pilha, chama outras funções, salva os registros não voláteis ou usa o tratamento de exceção. Ele também requer uma entrada de tabela de função. Uma função de quadro requer um prólogo e um epílogo. Uma função de quadro pode alocar dinamicamente o espaço de pilha e pode empregar um ponteiro de quadro. Uma função de quadro tem os recursos completos disso de chamada padrão à sua disposição.

Se uma função de quadro não chama outra função, ele não é necessário para alinhar a pilha (mencionada na seção [alocação da pilha](../build/stack-allocation.md)).

Uma função de folha é aquele que não requer uma entrada de tabela de função. Ele não pode fazer alterações para todos os registros não voláteis, incluindo RSP, que significa que ele não é possível chamar quaisquer funções ou alocar o espaço de pilha. Ele tem permissão para deixar a pilha não alinhados enquanto ele é executado.

## <a name="see-also"></a>Consulte também

[Uso da pilha](../build/stack-usage.md)
