---
title: Depuração e listagens para assembly embutido
ms.date: 08/30/2018
helpviewer_keywords:
- source level debugger
- __asm keyword [C++], debugging
- inline assembly, listings
- bugs, __asm blocks
- debugging [C++], inline assembly code
- inline assembly, debugging
ms.assetid: 69266930-6f9a-433d-b704-f4f44e7b2583
ms.openlocfilehash: 1b2ec146daf450c4302be9fea8fdd117ec6398da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485162"
---
# <a name="debugging-and-listings-for-inline-assembly"></a>Depuração e listagens para assembly embutido

**Seção específica da Microsoft**

Programas que contém o código de assembly embutido podem ser depurados com um depurador de nível de código-fonte, se você compilar com o [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) opção.

No depurador, você pode definir pontos de interrupção nas linhas de C ou C++ e linguagem de assembly. Se você habilitar o assembly misto e modo de origem, você pode exibir a origem e o formulário desmontado do código do assembly.

Observe que colocar várias instruções de assembly ou instruções de linguagem do código-fonte em uma única linha pode obstruir a depuração. No modo código-fonte, você pode usar o depurador para definir pontos de interrupção em uma única linha, mas não em instruções individuais na mesma linha. O mesmo princípio se aplica a um `__asm` bloco definido como uma macro de C, que se expande para uma única linha lógica.

Se você criar um misto de código-fonte e o assembly listando com o [/FAs](../../build/reference/fa-fa-listing-file.md) opção de compilador, a listagem contém a origem e o assembly de formulários de cada linha da linguagem de assembly. Macros não são expandidas nas listagens, mas eles são expandidos durante a compilação.

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[Usando a linguagem de assembly em blocos __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>