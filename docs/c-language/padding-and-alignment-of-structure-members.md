---
title: Preenchimento e alinhamento de membros da estrutura
ms.date: 10/18/2018
helpviewer_keywords:
- structure members, padding and alignment
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
ms.openlocfilehash: 0f9c70ed074a11800b707aa48ec8e0e2f8b4f999
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148108"
---
# <a name="padding-and-alignment-of-structure-members"></a>Preenchimento e alinhamento de membros da estrutura

**ANSI 3.5.2.1** O preenchimento e alinhamento dos membros das estruturas e se um campo de bit pode transpor um limite de unidade de armazenamento

Os membros da estrutura são armazenados em sequência na ordem em que são declarados: o primeiro membro tem o endereço de memória mais baixo e o último membro, o mais alto.

Cada objeto de dados tem um requisito alignment-requirement. O requisito de alinhamento para todos os dados, exceto estruturas, uniões e matrizes, é o tamanho do objeto ou o tamanho do pacote atual (especificado com /Zp ou o pragma `pack`, o que for menor.) Para estruturas, uniões e matrizes, o requisito de alinhamento é o maior requisito de alinhamento de seus membros. Um offset (deslocamento) é alocado para cada objeto de modo que

*offset* **%** *alignment-requirement* **== 0**

Os campos de bits adjacentes serão empacotados na mesma unidade de alocação de 1, 2, ou 4 bytes se os tipos integrais forem do mesmo tamanho e se o campo de bit seguinte se encaixar na unidade de alocação atual sem cruzar o limite imposto pelos requisitos comuns de alinhamento dos campos de bits.

## <a name="see-also"></a>Consulte também

[Estruturas, uniões, enumerações e campos de bit](../c-language/structures-unions-enumerations-and-bit-fields.md)
