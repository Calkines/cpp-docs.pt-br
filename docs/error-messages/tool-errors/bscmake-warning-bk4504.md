---
title: Aviso BK4504 (BSCMAKE)
ms.date: 11/04/2016
f1_keywords:
- BK4504
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
ms.openlocfilehash: 7ffcb7c2e6ae512006ccd29c87b05c53fdfcaef5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279277"
---
# <a name="bscmake-warning-bk4504"></a>Aviso BK4504 (BSCMAKE)

arquivo contém muitas referências; Ignorando referência posterior desta fonte

O arquivo. cpp contém mais de 64.000 referências de símbolo. Quando BSCMAKE encontrou 64.000 referências em um arquivo, ele ignora todas as referências adicionais.

Para corrigir o problema, em Dividir o arquivo em dois ou mais arquivos, cada um deles tem menos de 64.000 referências de símbolo, ou usarem o `#pragma component(browser)` diretiva de pré-processador para símbolos de limite que são gerados para referências específicas. Para obter mais informações, consulte [componente](../../preprocessor/component.md).