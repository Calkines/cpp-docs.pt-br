---
title: Erro fatal U1099 (NMAKE)
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: 395f25d8d27bc5e9b6132c87390c8c3bc19b6cc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298237"
---
# <a name="nmake-fatal-error-u1099"></a>Erro fatal U1099 (NMAKE)

estouro de pilha

O makefile que está sendo processado era muito complexo para a alocação de pilha atual em NMAKE. NMAKE tem uma alocação de 0x3000 (12K).

Para aumentar a alocação da pilha do NMAKE, execute as [/stack (editbin)](../../build/reference/stack.md) utilitário com uma maior opção de pilha:

**editbin /STACK:reserve NMAKE. EXE**

em que *reservar* é um número maior que a alocação de pilha atual em NMAKE.