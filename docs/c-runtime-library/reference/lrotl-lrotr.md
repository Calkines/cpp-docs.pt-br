---
title: _lrotl, _lrotr | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _lrotl
- _lrotr
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- lrotr
- lrotl
- _lrotr
- _lrotl
dev_langs:
- C++
helpviewer_keywords:
- lrotl function
- bits
- _lrotr function
- lrotr function
- rotating bits
- _lrotl function
- bits, rotating
ms.assetid: d42f295b-35f9-49d2-9ee4-c66896ffe68e
caps.latest.revision: 10
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
ms.openlocfilehash: b4f7d08e41c2510b8de9494aa039320fb9d7a3ac
ms.lasthandoff: 02/25/2017

---
# <a name="lrotl-lrotr"></a>_lrotl, _lrotr
Gira bits para a esquerda (`_lrotl`) ou para a direita (`_lrotr`).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      unsigned long _lrotl(  
   unsigned long value,  
   int shift   
);  
unsigned long _lrotr(  
   unsigned long value,  
   int shift   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *value*  
 O valor a ser girado.  
  
 `shift`  
 O número de bits para deslocar *value*.  
  
## <a name="return-value"></a>Valor de retorno  
 Ambas as funções retornam o valor girado. Nenhum erro é retornado.  
  
## <a name="remarks"></a>Comentários  
 As funções `_lrotl` e `_lrotr` giram *value* por bits `shift`. `_lrotl` gira o valor para a esquerda. `_lrotr` gira o valor para a direita. Ambas as funções encapsulam bits girados de uma extremidade do *value* para a outra.  
  
## <a name="requirements"></a>Requisitos  
  
|Rotina|Cabeçalho necessário|  
|-------------|---------------------|  
|`_lrotl`|\<stdlib.h>|  
|`_lrotr`|\<stdlib.h>|  
  
 Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md) na Introdução.  
  
## <a name="libraries"></a>Libraries  
 Todas as versões das [bibliotecas em tempo de execução C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Exemplo  
  
```  
// crt_lrot.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   unsigned long val = 0x0fac35791;  
  
   printf( "0x%8.8lx rotated left eight times is 0x%8.8lx\n",   
            val, _lrotl( val, 8 ) );  
   printf( "0x%8.8lx rotated right four times is 0x%8.8lx\n",   
            val, _lrotr( val, 4 ) );  
}  
```  
  
## <a name="output"></a>Saída  
  
```  
0xfac35791 rotated left eight times is 0xc35791fa  
0xfac35791 rotated right four times is 0x1fac3579  
```  
  
## <a name="net-framework-equivalent"></a>Equivalente ao .NET Framework  
 Não aplicável. Para chamar a função C padrão, use `PInvoke`. Para obter mais informações, consulte [Exemplos de invocação de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Consulte também  
 [Suporte a ponto flutuante](../../c-runtime-library/floating-point-support.md)   
 [_rotl, _rotl64, _rotr, _rotr64](../../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)