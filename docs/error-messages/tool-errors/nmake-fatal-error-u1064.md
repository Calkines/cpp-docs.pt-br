---
title: Erro fatal U1064 (NMAKE)
ms.date: 11/04/2016
f1_keywords:
- U1064
helpviewer_keywords:
- U1064
ms.assetid: 7141e66e-cde6-4173-84df-a391f3ebcdd1
ms.openlocfilehash: 71213391032989e5faf8889761b29194928125a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367402"
---
# <a name="nmake-fatal-error-u1064"></a>Erro fatal U1064 (NMAKE)

MAKEFILE não encontrado e nenhum destino especificado

A linha de comando NMAKE não especificou um makefile ou destino e o diretório atual não contém um arquivo chamado MAKEFILE.

NMAKE exige um makefile ou um destino de linha de comando (ou ambos). Para disponibilizar um makefile para NMAKE, especifique a opção /F ou colocar um arquivo chamado MAKEFILE no diretório atual. NMAKE pode criar um destino de linha de comando usando uma regra de inferência se não for fornecido um makefile.