---
title: feclearexcept1 | Microsoft Docs
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
- feclearexcept
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- feclearexcept
- fenv/feclearexcept
dev_langs:
- C++
helpviewer_keywords:
- feclearexcept function
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
caps.latest.revision: 5
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 5ccfb294bcc92f38b7e5e5f912f85de554a72296
ms.lasthandoff: 02/25/2017

---
# <a name="feclearexcept"></a>feclearexcept
Tenta limpar os sinalizadores de exceção de ponto flutuante especificados pelo argumento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
int feclearexcept(  
   int excepts  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `excepts`  
 Os sinalizadores de status de exceção para limpar.  
  
## <a name="return-value"></a>Valor de retorno  
 Retorna zero se `excepts` for zero ou se todas as exceções especificadas foram limpas com êxito. Caso contrário, retornará um valor diferente de zero.  
  
## <a name="remarks"></a>Comentários  
 A função `feclearexcept` tenta limpar os sinalizadores do status de exceção do ponto flutuante especificado por `excepts`. A função dá suporte a essas macros de exceção, definidas em fenv.h:  
  
|Macro de exceção|Descrição|  
|---------------------|-----------------|  
|FE_DIVBYZERO|Ocorreu um erro de polo ou singularidade em uma operação de ponto flutuante anterior. Um valor infinito foi criado.|  
|FE_INEXACT|A função foi forçada a arredondar o resultado armazenado de uma operação de ponto flutuante anterior.|  
|FE_INVALID|Ocorreu um erro de domínio em uma operação de ponto flutuante anterior.|  
|FE_OVERFLOW|Ocorreu um erro de intervalo. O resultado de uma operação de ponto flutuante anterior era muito grande para ser representado.|  
|FE_UNDERFLOW|O resultado de uma operação de ponto flutuante anterior era muito pequeno para ser representado na precisão total. Um valor de denormal foi criado.|  
|FE_ALLEXCEPT|O OR bit a bit de todas as exceções de ponto flutuante com suporte.|  
  
 O argumento `excepts` pode ser zero ou o OR bit a bit de um ou mais das macros de exceção com suporte. O resultado de qualquer outro valor de argumento é indefinido.  
  
## <a name="requirements"></a>Requisitos  
  
|Função|Cabeçalho C|Cabeçalho C++|  
|--------------|--------------|------------------|  
|`feclearexcept`|\<fenv.h>|\<cfenv>|  
  
 Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Consulte também  
 [Referência da Função Alfabética](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fetestexcept](../../c-runtime-library/reference/fetestexcept1.md)