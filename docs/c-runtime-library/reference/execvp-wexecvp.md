---
title: _execvp, _wexecvp
ms.date: 11/04/2016
apiname:
- _execvp
- _wexecvp
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
- _execvp
- wexecvp
- _wexecvp
helpviewer_keywords:
- _execvp function
- _wexecvp function
- wexecvp function
- execvp function
ms.assetid: a4db15df-b204-4987-be7c-de84c3414380
ms.openlocfilehash: 876ace62ac46b80d42f3ed0a3549757839e0b47a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339085"
---
# <a name="execvp-wexecvp"></a>_execvp, _wexecvp

Carrega e executa novos processos filho.

> [!IMPORTANT]
> Esta API não pode ser usada em aplicativos executados no Tempo de Execução do Windows. Para obter mais informações, confira [Funções do CRT sem suporte em aplicativos da Plataforma Universal do Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxe

```C
intptr_t _execvp(
   const char *cmdname,
   const char *const *argv
);
intptr_t _wexecvp(
   const wchar_t *cmdname,
   const wchar_t *const *argv
);
```

### <a name="parameters"></a>Parâmetros

*cmdname*<br/>
Caminho do arquivo a ser executado.

*argv*<br/>
Matriz de ponteiros para os parâmetros.

## <a name="return-value"></a>Valor de retorno

Se bem-sucedidas, essas funções não retornam ao processo de chamada. Um valor de retorno de -1 indica um erro, caso em que o **errno** variável global é definida.

|**errno** value|Descrição|
|-------------------|-----------------|
|**E2BIG**|O espaço necessário para os argumentos e as configurações de ambiente excede 32 KB.|
|**EACCES**|O arquivo especificado tem uma violação de compartilhamento ou de bloqueio.|
|**EINVAL**|Parâmetro inválido.|
|**EMFILE**|Muitos arquivos abertos (o arquivo especificado deve ser aberto para determinar se ele é executável).|
|**ENOENT**|Arquivo ou caminho não encontrado.|
|**ENOEXEC**|O arquivo especificado não é executável ou tem um formato inválido do arquivo executável.|
|**ENOMEM**|Não há memória suficiente disponível para executar o novo processo. A memória disponível foi corrompida ou há um bloco inválido, indicando que o processo de chamada não foi alocado corretamente.|

Para obter mais informações sobre esses e outros códigos de retorno, consulte [_doserrno, errno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentários

Cada uma dessas funções carrega e executa um novo processo, passando uma matriz de ponteiros para argumentos de linha de comando e usando o **caminho** variável de ambiente para localizar o arquivo a ser executado.

O **execvp** funções validam seus parâmetros. Se o *cmdname* for um ponteiro nulo, ou *argv* for um ponteiro nulo, ponteiro para uma matriz vazia, ou se a matriz contiver uma cadeia de caracteres vazia como o primeiro argumento, essas funções invocarão o manipulador de parâmetro inválido conforme descrito em [validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, essas funções definirão **errno** à **EINVAL** e retornarão -1. Nenhum processo é inicializado.

## <a name="requirements"></a>Requisitos

|Função|Cabeçalho necessário|Cabeçalho opcional|
|--------------|---------------------|---------------------|
|**_execvp**|\<process.h>|\<errno.h>|
|**_wexecvp**|\<process.h> ou \<wchar.h>|\<errno.h>|

Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

Consulte o exemplo nas [ funções _exec, _wexec](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Consulte também

[Controle de processo e de ambiente](../../c-runtime-library/process-and-environment-control.md)<br/>
[Funções _exec, _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[Funções _spawn, _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
