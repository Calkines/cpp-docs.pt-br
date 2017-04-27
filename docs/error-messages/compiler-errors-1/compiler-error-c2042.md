---
title: C2042 de erro do compilador | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2042
dev_langs:
- C++
helpviewer_keywords:
- C2042
ms.assetid: e111788f-41ce-405a-9824-a4c1c26059e6
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 80f030788026b11fa0df615fc75d4e2b67933946
ms.lasthandoff: 02/25/2017

---
# <a name="compiler-error-c2042"></a>C2042 de erro do compilador
palavras-chave signed/unsigned mutuamente exclusivas  
  
 As palavras-chave `signed` e `unsigned` são usados em uma única declaração.  
  
 O exemplo a seguir gera C2042:  
  
```  
// C2042.cpp  
unsigned signed int i;   // C2042  
```  
  
 Resolução possível:  
  
```  
// C2042b.cpp  
// compile with: /c  
unsigned int i;  
signed int ii;  
```