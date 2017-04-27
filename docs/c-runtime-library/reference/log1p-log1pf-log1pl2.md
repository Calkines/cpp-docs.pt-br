---
title: log1p, log1pf, log1pl2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- log1p
- log1pf
- log1pl
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- log1p
- log1pf
- log1pl
- math/log1p
- math/log1pf
- math/log1pl
helpviewer_keywords:
- log1p function
- log1pf function
- log1pl function
ms.assetid: a40d965d-b4f6-42f4-ba27-2395546f7c12
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: e928ac048b65fde5422a8a937779029f94a9e9a1
ms.lasthandoff: 02/25/2017

---
# <a name="log1p-log1pf-log1pl"></a>log1p, log1pf, log1pl
Calcula o logaritmo natural de 1 mais o valor especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
double log1p(  
   double x  
);  
  
float log1p(  
   float x  
); //C++ only  
  
long double log1p(  
   long double x  
); //C++ only  
  
float log1pf(  
   float x  
);  
  
long double log1pl(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `x`  
 O argumento de ponto flutuante.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará o log natural (base e) de (`x`+&1;).  
  
 Caso contrário, pode retornar um dos seguintes valores:  
  
|Entrada|Resultado|Exceção SEH|errno|  
|-----------|------------|-------------------|-----------|  
|+inf|+inf|||  
|Desnormalizado|Igual à entrada|UNDERFLOW||  
|±0|Igual à entrada|||  
|-1|-inf|DIVBYZERO|ERANGE|  
|< -1|nan|INVALID|EDOM|  
|-inf|nan|INVALID|EDOM|  
|±SNaN|Igual à entrada|INVALID||  
|±QNaN, indefinido|Igual à entrada|||  
  
 O `errno` valor será definido como ERANGE se `x` = -1. O `errno` valor será definido como EDOM se `x` < −1.  
  
## <a name="remarks"></a>Comentários  
 As funções `log1p` podem ser mais precisas do que o uso de log(`x`+1) quando x está próximo de 0.  
  
 Uma vez que C++ permite sobrecargas, é possível chamar sobrecargas de `log1p` que utilizam e retornam tipos duplos flutuantes e longos. Em um programa C, `log1p` sempre usa e retorna um duplo.  
  
 Se `x` for um número natural, essa função retornará o logaritmo do fatorial de (`x`-1).  
  
## <a name="requirements"></a>Requisitos  
  
|Função|Cabeçalho C|Cabeçalho C++|  
|--------------|--------------|------------------|  
|`log1p`,                `log1pf`,  `log1pl`|\<math.h>|\<cmath>|  
  
 Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Consulte também  
 [Referência da Função Alfabética](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [log2, log2f, log2l](../../c-runtime-library/reference/log2-log2f-log2l.md)   
 [log, logf, log10, log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)