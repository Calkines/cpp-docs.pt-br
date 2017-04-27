---
title: _execlpe, _wexeclpe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _execlpe
- _wexeclpe
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
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wexeclpe
- execlpe
- wexeclpe
- _execlpe
dev_langs:
- C++
helpviewer_keywords:
- wexeclpe function
- _wexeclpe function
- _execlpe function
- execlpe function
ms.assetid: 07b861da-3e7e-4f1d-bb80-ad69b55e5162
caps.latest.revision: 21
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
ms.openlocfilehash: f5019c9d07fbe1a944bb7bde63cf725585e5fd15
ms.lasthandoff: 02/25/2017

---
# <a name="execlpe-wexeclpe"></a>_execlpe, _wexeclpe
Carrega e executa novos processos filho.  
  
> [!IMPORTANT]
>  Esta API não pode ser usada em aplicativos executados no Tempo de Execução do Windows. Para obter mais informações, consulte [Funções de CRT sem suporte com /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
intptr_t _execlpe(   
   const char *cmdname,  
   const char *arg0,  
   ... const char *argn,  
   NULL,  
   const char *const *envp   
);  
intptr_t _wexeclpe(   
   const wchar_t *cmdname,  
   const wchar_t *arg0,  
   ... const wchar_t *argn,  
   NULL,  
   const wchar_t *const *envp   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cmdname`  
 Caminho do arquivo a ser executado.  
  
 `arg0`, `...``argn`  
 Lista de ponteiros para os parâmetros.  
  
 `envp`  
 Matriz de ponteiros para as configurações de ambiente.  
  
## <a name="return-value"></a>Valor de retorno  
 Se bem-sucedidas, essas funções não retornam ao processo de chamada. Um valor retornado de –1 indica um erro e, nesse caso, a variável global `errno` é definida.  
  
|Valor `errno`|Descrição|  
|-------------------|-----------------|  
|`E2BIG`|O espaço necessário para os argumentos e as configurações de ambiente excede 32 KB.|  
|`EACCES`|O arquivo especificado tem uma violação de compartilhamento ou de bloqueio.|  
|`EINVAL`|Parâmetro inválido.|  
|`EMFILE`|Muitos arquivos abertos (o arquivo especificado deve ser aberto para determinar se ele é executável).|  
|`ENOENT`|Arquivo ou caminho não encontrado.|  
|`ENOEXEC`|O arquivo especificado não é executável ou tem um formato inválido do arquivo executável.|  
|`ENOMEM`|Não há memória suficiente disponível para executar o novo processo. A memória disponível foi corrompida ou há um bloco inválido, indicando que o processo de chamada não foi alocado corretamente.|  
  
 Para obter mais informações sobre esses e outros códigos de retorno, consulte [_doserrno, errno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentários  
 Cada uma dessas funções carrega e executa um novo processo, passando cada argumento de linha de comando como um parâmetro separado e também passando uma matriz de ponteiros para as configurações de ambiente. Essas funções usam a variável de ambiente `PATH` para localizar o arquivo a ser executado.  
  
 As funções `_execlpe` validam seus parâmetros. Se `cmdname` ou `arg0` for um ponteiro nulo ou uma cadeia de caracteres vazia, essas funções invocarão o manipulador de parâmetro inválido, conforme descrito em [Validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, essas funções definirão `errno` como `EINVAL` e retornarão -1. Nenhum processo novo é inicializado.  
  
## <a name="requirements"></a>Requisitos  
  
|Função|Cabeçalho necessário|Cabeçalho opcional|  
|--------------|---------------------|---------------------|  
|`_execlpe`|\<process.h>|\<errno.h>|  
|`_wexeclpe`|\<process.h> ou \<wchar.h>|\<errno.h>|  
  
 Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Exemplo  
 Consulte o exemplo nas [ funções _exec, _wexec](../../c-runtime-library/exec-wexec-functions.md).  
  
## <a name="net-framework-equivalent"></a>Equivalente ao .NET Framework  
  
-   [Classe System::Diagnostics::Process](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)  
  
-   [Classe System::Diagnostics::ProcessStartInfo](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)  
  
## <a name="see-also"></a>Consulte também  
 [Controle de processo e de ambiente](../../c-runtime-library/process-and-environment-control.md)   
 [Funções _exec, _wexec](../../c-runtime-library/exec-wexec-functions.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [exit, _Exit, _exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit, _onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [Funções _spawn, _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system, _wsystem](../../c-runtime-library/reference/system-wsystem.md)