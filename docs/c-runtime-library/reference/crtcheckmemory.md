---
title: _CrtCheckMemory | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtCheckMemory
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
apitype: DLLExport
f1_keywords:
- CrtCheckMemory
- _CrtCheckMemory
dev_langs:
- C++
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
caps.latest.revision: 12
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 5563d618b0056de285f66cf428cbcfc6a717ce55
ms.lasthandoff: 02/25/2017

---
# <a name="crtcheckmemory"></a>_CrtCheckMemory
Confirma a integridade dos blocos de memória alocados no heap de depuração (somente versão de depuração).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
int _CrtCheckMemory( void );  
```  
  
## <a name="return-value"></a>Valor de retorno  
 Se tiver êxito, `_CrtCheckMemory` retornará TRUE; caso contrário, a função retornará FALSE.  
  
## <a name="remarks"></a>Comentários  
 A função `_CrtCheckMemory` valida a memória alocada pelo gerenciador de heap de depuração verificando o heap base subjacente e inspecionando todos os blocos de memória. Se for encontrado um erro ou uma inconsistência de memória no heap base subjacente, nas informações de cabeçalho de depuração ou nos buffers de substituição, `_CrtCheckMemory` gerará um relatório de depuração com informações que descrevem a condição de erro. Quando [_DEBUG](../../c-runtime-library/debug.md) não está definido, as chamadas a `_CrtCheckMemory` são removidas durante o pré-processamento.  
  
 O comportamento de `_CrtCheckMemory` pode ser controlado configurando os campos de bits do sinalizador [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) usando a função [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md). A ativação do campo de bits **_CRTDBG_CHECK_ALWAYS_DF** resulta na chamada a `_CrtCheckMemory` sempre que uma operação de alocação de memória é solicitada. Embora esse método reduza a velocidade de execução, ele é útil para capturar erros rapidamente. A desativação do campo de bits **_CRTDBG_ALLOC_MEM_DF** faz com que `_CrtCheckMemory` não verifique o heap e retorne **TRUE** imediatamente.  
  
 Como essa função retorna **TRUE** ou **FALSE**, ela pode ser passada para uma das macros [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) para criar um mecanismo simples de tratamento de erro de depuração. O seguinte exemplo causa uma falha de asserção se o dano é detectado no heap:  
  
```  
_ASSERTE( _CrtCheckMemory( ) );  
```  
  
 Para obter mais informações sobre como `_CrtCheckMemory` pode ser usado com outras funções de depuração, consulte [Funções de relatório de estado de heap](/visualstudio/debugger/crt-debug-heap-details). Para obter uma visão geral do gerenciamento de memória e do heap de depuração, consulte [Detalhes do heap de depuração do CRT](/visualstudio/debugger/crt-debug-heap-details).  
  
## <a name="requirements"></a>Requisitos  
  
|Rotina|Cabeçalho necessário|  
|-------------|---------------------|  
|`_CrtCheckMemory`|\<crtdbg.h>|  
  
 Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md) na Introdução.  
  
## <a name="libraries"></a>Libraries  
 Somente versões de depuração de [bibliotecas de tempo de execução C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Exemplo  
 Para obter uma amostra de como usar `_CrtCheckMemory`, consulte [crt_dbg1](http://msdn.microsoft.com/en-us/17b4b20c-e849-48f5-8eb5-dca6509cbaf9).  
  
## <a name="net-framework-equivalent"></a>Equivalente ao .NET Framework  
 [System::Diagnostics::PerformanceCounter](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)  
  
## <a name="see-also"></a>Consulte também  
 [Rotinas de depuração](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)   
 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md)