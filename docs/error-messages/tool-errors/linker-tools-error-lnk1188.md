---
title: Erro das Ferramentas de Vinculador LNK1188
ms.date: 11/04/2016
f1_keywords:
- LNK1188
helpviewer_keywords:
- LNK1188
ms.assetid: 4af574b0-5b41-4580-9a37-52a634add995
ms.openlocfilehash: 69ac20522aebb7391319c0de210e06b305f3fd0d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226472"
---
# <a name="linker-tools-error-lnk1188"></a>Erro das Ferramentas de Vinculador LNK1188

BADFIXUPSECTION:: alvo de conserto inválido 'symbol'; possíveis seção de comprimento de zero

Durante um link de VxD, o destino de uma realocação não tinha uma seção. Com LINK386 (uma versão mais antiga), um registro de grupo OMF (gerado por uma diretiva de grupo (MASM)) pode ter sido usado para combinar a seção de tamanho zero com outra seção de comprimento diferente de zero. Formato COFF não oferece suporte a diretiva de grupo e a seções de comprimento zero. Quando o LINK converte automaticamente esse tipo de objeto OMF para COFF, esse erro pode ocorrer.