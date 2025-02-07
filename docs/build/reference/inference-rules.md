---
title: Regras de inferência
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
ms.openlocfilehash: 0c1db9150c3b2c36c35e6802bfcd639af45bdc82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291269"
---
# <a name="inference-rules"></a>Regras de inferência

Regras de inferência de fornecem comandos para atualizar destinos e inferir dependentes para destinos. Extensões em uma regra de inferência de tipos correspondem a um único destino e dependente que têm o mesmo nome base. Regras de inferência são definidos pelo usuário ou predefinidas; regras predefinidas podem ser redefinidas.

Se uma dependência desatualizada não tiver nenhum comando e se [. SUFIXOS](dot-directives.md) contém a extensão do dependente, usos NMAKE uma regra cujas extensões correspondem a um existente e o destino de arquivo no diretório atual ou especificado. Se mais de uma regra corresponde a arquivos existentes, o **. SUFIXOS** lista determina qual deles usar; desce de prioridade de lista da esquerda para a direita. Se um arquivo dependente não existe e não estiver listado como um destino em outro bloco de descrição, uma regra de inferência de tipos pode criar o ausente dependente de outro arquivo com o mesmo nome de base. Se o destino de um bloco descrição não tiver dependentes ou comandos, uma regra de inferência de tipos pode atualizar o destino. Regras de inferência podem criar um destino de linha de comando, mesmo se não existe nenhum bloco de descrição. NMAKE pode invocar uma regra para um dependentes inferidos, mesmo se um dependente explícita for especificada.

## <a name="what-do-you-want-to-know-more-about"></a>Que mais você deseja saber?

[Definindo uma regra](defining-a-rule.md)

[Regras de modo de lote](batch-mode-rules.md)

[Regras predefinidas](predefined-rules.md)

[Dependentes inferidos e regras](inferred-dependents-and-rules.md)

[Precedência em regras de inferência](precedence-in-inference-rules.md)

## <a name="see-also"></a>Consulte também

[Referência a NMAKE](nmake-reference.md)