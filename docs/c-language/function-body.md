---
title: Corpo da função
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
ms.openlocfilehash: 064e630d5ca74476c79522e39130e75f741d8946
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463681"
---
# <a name="function-body"></a>Corpo da função

Um *corpo da função* é uma instrução composta que contém as instruções que especificam o que a função faz.

## <a name="syntax"></a>Sintaxe

*function-definition*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\* *attribute-seq* é Específico da Microsoft \*/

*compound-statement*: /\* O corpo da função \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *declaration-list*<sub>opt</sub> *statement-list*<sub>opt</sub> **}**

Variáveis declaradas em um corpo da função, conhecidas como *variáveis locais*, têm a classe de armazenamento **auto**, a menos que especificado o contrário. Quando a função for chamada, o armazenamento é criado para as variáveis locais e as inicializações de local são executadas. O controle de execução passa para a primeira instrução em *compound-statement* e continua até que uma instrução **return** seja executada ou o final do corpo da função seja encontrado. O controle então retorna para o ponto no qual a função foi chamada.

Uma instrução **return** que contenha uma expressão deverá ser executada se a função tiver que retornar um valor. O valor de retorno de uma função será indefinido se nenhuma instrução **return** for executada ou se a instrução **return** não incluir uma expressão.

## <a name="see-also"></a>Consulte também

[Definições de função C](../c-language/c-function-definitions.md)