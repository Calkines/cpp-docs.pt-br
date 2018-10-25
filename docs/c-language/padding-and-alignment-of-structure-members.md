---
title: Preenchimento e alinhamento de membros da estrutura | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structure members, padding and alignment
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1b301372a9998197c46c1e44c91c9d3456cea8e
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808206"
---
# <a name="padding-and-alignment-of-structure-members"></a>Preenchimento e alinhamento de membros da estrutura

**ANSI 3.5.2.1** O preenchimento e alinhamento dos membros das estruturas e se um campo de bit pode transpor um limite de unidade de armazenamento

Os membros da estrutura são armazenados em sequência na ordem em que são declarados: o primeiro membro tem o endereço de memória mais baixo e o último membro, o mais alto.

Cada objeto de dados tem um requisito alignment-requirement. O requisito de alinhamento para todos os dados, exceto estruturas, uniões e matrizes, é o tamanho do objeto ou o tamanho do pacote atual (especificado com /Zp ou o pragma `pack`, o que for menor.) Para estruturas, uniões e matrizes, o requisito de alinhamento é o maior requisito de alinhamento de seus membros. Um offset (deslocamento) é alocado para cada objeto de modo que

*offset* **%** *alignment-requirement* **== 0**

Os campos de bits adjacentes serão empacotados na mesma unidade de alocação de 1, 2, ou 4 bytes se os tipos integrais forem do mesmo tamanho e se o campo de bit seguinte se encaixar na unidade de alocação atual sem cruzar o limite imposto pelos requisitos comuns de alinhamento dos campos de bits.

## <a name="see-also"></a>Consulte também

[Estruturas, uniões, enumerações e campos de bit](../c-language/structures-unions-enumerations-and-bit-fields.md)