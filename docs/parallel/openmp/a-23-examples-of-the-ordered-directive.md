---
title: Exemplos A.23 da diretiva ordenada | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 83d77bb4f064a7ee69b013b36de919b57486b3e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="a23---examples-of-the-ordered-directive"></a>A.23   Exemplos da diretiva ordered
É possível ter várias seções ordenadas com uma `for` especificado com o `ordered` cláusula. O primeiro exemplo não for compatível, porque a API Especifica o seguinte:  
  
 "Uma iteração de um loop com um `for` construção não deve executar a mesma `ordered` diretiva mais de uma vez e ele não devem executar mais de um `ordered` diretiva." (Consulte [seção 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) na página 22)  
  
 Neste exemplo não compatível, todas as iterações execute 2 seções ordenadas:  
  
```  
#pragma omp for ordered  
for (i=0; i<n; i++)   
{  
    ...  
    #pragma omp ordered  
    { ... }  
    ...  
    #pragma omp ordered  
    { ... }  
    ...  
}  
```  
  
 Mostra o seguinte exemplo compatíveis com um `for` com mais de uma seção de ordenados:  
  
```  
#pragma omp for ordered  
for (i=0; i<n; i++)   
{  
    ...  
    if (i <= 10)   
    {  
        ...  
        #pragma omp ordered  
        { ... }  
    }  
    ...  
    (i > 10)   
    {  
        ...  
        #pragma omp ordered  
        { ... }  
    }  
    ...  
}  
```