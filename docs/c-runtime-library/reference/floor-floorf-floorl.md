---
title: floor, floorf, floorl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- floorf
- floorl
- floor
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
- floor
- floorl
- _floorl
- floorf
dev_langs:
- C++
helpviewer_keywords:
- floor function
- floorf function
- calculating floors of values
- floorl function
ms.assetid: e9955f70-d659-414f-8050-132e13c8ff36
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 770e27da602c5f28a82b0effbe7f2576c2c668c9
ms.lasthandoff: 02/25/2017

---
# <a name="floor-floorf-floorl"></a>floor, floorf, floorl
Calcula a base de um valor.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
double floor(  
   double x  
);  
float floor(  
   float x   
); // C++ only  
long double floor(  
   long double x  
); // C++ only  
float floorf(  
   float x  
);  
long double floorl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `x`  
 Valor de ponto flutuante.  
  
## <a name="return-value"></a>Valor de retorno  
 As funções `floor` retornam um valor de ponto flutuante que representa o maior inteiro menor ou igual a `x`. Nenhum erro é retornado.  
  
|Entrada|Exceção SEH|Exceção Matherr|  
|-----------|-------------------|-----------------------|  
|± QNAN,IND|nenhum|_DOMAIN|  
  
 `floor` tem uma implementação que usa SSE2 (Extensões SIMD de Streaming 2). Para obter informações e restrições relativas ao uso da implementação de SSE2, consulte [_set_SSE2_enable](../../c-runtime-library/reference/set-sse2-enable.md).  
  
## <a name="remarks"></a>Comentários  
 O C++ permite sobrecargas, de modo que é possível chamar sobrecargas de `floor` que usam e retornam valores de `float` e `long double`. Em um programa C, `floor` sempre toma e retorna um `double`.  
  
## <a name="requirements"></a>Requisitos  
  
|Função|Cabeçalho necessário|  
|--------------|---------------------|  
|`floor`, `floorf`, `floorl`|\<math.h>|  
  
 Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Exemplo  
  
```  
// crt_floor.c  
// This example displays the largest integers  
// less than or equal to the floating-point values 2.8  
// and -2.8. It then shows the smallest integers greater  
// than or equal to 2.8 and -2.8.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double y;  
  
   y = floor( 2.8 );  
   printf( "The floor of 2.8 is %f\n", y );  
   y = floor( -2.8 );  
   printf( "The floor of -2.8 is %f\n", y );  
  
   y = ceil( 2.8 );  
   printf( "The ceil of 2.8 is %f\n", y );  
   y = ceil( -2.8 );  
   printf( "The ceil of -2.8 is %f\n", y );  
}  
```  
  
```Output  
The floor of 2.8 is 2.000000  
The floor of -2.8 is -3.000000  
The ceil of 2.8 is 3.000000  
The ceil of -2.8 is -2.000000  
```  
  
## <a name="net-framework-equivalent"></a>Equivalente ao .NET Framework  
 [System::Math::Floor](https://msdn.microsoft.com/en-us/library/system.math.floor.aspx)  
  
## <a name="see-also"></a>Consulte também  
 [Suporte a ponto flutuante](../../c-runtime-library/floating-point-support.md)   
 [ceil, ceilf, ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [round, roundf, roundl](../../c-runtime-library/reference/round-roundf-roundl.md)   
 [fmod, fmodf](../../c-runtime-library/reference/fmod-fmodf.md)