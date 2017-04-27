---
title: feraiseexcept | Microsoft Docs
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
- feraiseexcept
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
apitype: HeaderDef
f1_keywords:
- feraiseexcept
- fenv/feraiseexcept
dev_langs:
- C++
helpviewer_keywords:
- feraiseexcept function
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
caps.latest.revision: 3
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
ms.openlocfilehash: 18b00434990ea71149f179785c61320b08c3c738
ms.lasthandoff: 02/25/2017

---
# <a name="feraiseexcept"></a>feraiseexcept
Gera as exceções de ponto flutuante especificadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
int feraiseexcept(  
   int excepts  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `excepts`  
 As exceções de ponto flutuante que serão geradas.  
  
## <a name="return-value"></a>Valor de retorno  
 Se todas as exceções especificadas forem geradas com êxito, retornará 0.  
  
## <a name="remarks"></a>Comentários  
 A função `feraiseexcept` tenta gerar as exceções de ponto flutuante especificadas por `excepts`.   A função `feraiseexcept` dá suporte a essas macros de exceção, definidas \<fenv.h>:  
  
|Macro de exceção|Descrição|  
|---------------------|-----------------|  
|FE_DIVBYZERO|Ocorreu um erro de polo ou singularidade em uma operação de ponto flutuante anterior. Um valor infinito foi criado.|  
|FE_INEXACT|A função foi forçada a arredondar o resultado armazenado de uma operação de ponto flutuante anterior.|  
|FE_INVALID|Ocorreu um erro de domínio em uma operação de ponto flutuante anterior.|  
|FE_OVERFLOW|Ocorreu um erro de intervalo. O resultado de uma operação de ponto flutuante anterior era muito grande para ser representado.|  
|FE_UNDERFLOW|O resultado de uma operação de ponto flutuante anterior era muito pequeno para ser representado na precisão total. Um valor de denormal foi criado.|  
|FE_ALLEXCEPT|O OR bit a bit de todas as exceções de ponto flutuante com suporte.|  
  
 O argumento `excepts` pode ser zero, um dos valores de macro de exceção ou OR bit a bit de duas ou mais das macros de exceção com suporte. Se uma das macros de exceção especificadas for FE_OVERFLOW ou FE_UNDERFLOW, a exceção FE_INEXACT poderá ser gerada como um efeito colateral.  
  
 Para usar essa função, você deve desligar otimizações de ponto flutuante que poderiam impedir o acesso usando a diretiva `#pragma fenv_access(on)` antes da chamada. Para obter mais informações, consulte [fenv_access](../../preprocessor/fenv-access.md).  
  
 **Seção específica da Microsoft:** as exceções especificadas em `excepts` são geradas na ordem FE_INVALID, FE_DIVBYZERO, FE_OVERFLOW, FE_UNDERFLOW, FE_INEXACT. No entanto, FE_INEXACT pode ser gerada quando FE_OVERFLOW ou FE_UNDERFLOW for gerada, mesmo se não for especificado em `excepts`. **Fim da seção específica da Microsoft**  
  
## <a name="requirements"></a>Requisitos  
  
|Função|Cabeçalho C|Cabeçalho C++|  
|--------------|--------------|------------------|  
|`feraiseexcept`|\<fenv.h>|\<cfenv>|  
  
 Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Consulte também  
 [Referência da Função Alfabética](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fetestexcept](../../c-runtime-library/reference/fetestexcept1.md)   
 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)