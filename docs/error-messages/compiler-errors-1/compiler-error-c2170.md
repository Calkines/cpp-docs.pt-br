---
title: Erro do compilador C2170
ms.date: 11/04/2016
f1_keywords:
- C2170
helpviewer_keywords:
- C2170
ms.assetid: d5c663f0-2459-4e11-a8bf-a52b62f3c71d
ms.openlocfilehash: 04d41a50bc0d5e811e47e5f9d146362a543f26f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174673"
---
# <a name="compiler-error-c2170"></a>Erro do compilador C2170

'identifier': não é declarado como uma função, não pode ser intrínseco

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Para corrigir verificando as possíveis causas a seguir

1. Pragma `intrinsic` é usado para um item diferente de uma função.

1. Pragma `intrinsic` é usado para uma função com nenhuma forma intrínseca.