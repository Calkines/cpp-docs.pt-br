---
title: "NULL instrução | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c10b493284ed4f81b15a1f045a3053743d919cc5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="null-statement"></a>Instrução nula
A "instrução null" é uma instrução de expressão com o *expressão* ausente. É útil quando a sintaxe da linguagem pede por uma instrução, mas nenhuma avaliação de expressão. Consiste em um ponto e vírgula.  
  
 Em geral, as instruções nulas são usadas como espaços reservados em instruções de iteração ou como instruções nas quais são colocados rótulos no final de instruções ou funções compostas.  
  
 O seguinte fragmento de código mostra como copiar uma cadeia de caracteres para outra e incorpora a instrução nula:  
  
```  
// null_statement.cpp  
char *myStrCpy( char *Dest, const char *Source )  
{  
    char *DestStart = Dest;  
  
    // Assign value pointed to by Source to  
    // Dest until the end-of-string 0 is  
    // encountered.  
    while( *Dest++ = *Source++ )  
        ;   // Null statement.  
  
    return DestStart;  
}  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Instrução de expressão](../cpp/expression-statement.md)