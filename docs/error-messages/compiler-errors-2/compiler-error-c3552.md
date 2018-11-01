---
title: Erro do compilador C3552
ms.date: 11/04/2016
f1_keywords:
- C3552
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
ms.openlocfilehash: 27c4707097f43266a3be57ad6dc9591ab6f34e97
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441802"
---
# <a name="compiler-error-c3552"></a>Erro do compilador C3552

'typename': um tipo de retorno especificado tardia não pode conter 'auto'

Se você usar o `auto` palavra-chave como um espaço reservado para o tipo de retorno de uma função, você deve fornecer um tipo de retorno com especificação tardia. No entanto, você não pode usar outro `auto` palavra-chave para especificar o retorno com especificação tardia tipo. Por exemplo, o fragmento de código a seguir produz o erro C3552.

`auto myFunction->auto; // C3552`