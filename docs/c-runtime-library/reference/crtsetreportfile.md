---
title: _CrtSetReportFile
ms.date: 11/04/2016
api_name:
- _CrtSetReportFile
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CrtSetReportFile
- _CrtSetReportFile
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
ms.openlocfilehash: bf88bae40031f6e92d6f936ac8a50f85d6c4e36c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942288"
---
# <a name="_crtsetreportfile"></a>_CrtSetReportFile

Depois de usar [_CrtSetReportMode](crtsetreportmode.md) para especificar **_CRTDBG_MODE_FILE**, você pode especificar o identificador de arquivo para receber o texto da mensagem. **_CrtSetReportFile** também é usado pelo [_CrtDbgReport, _ CrtDbgReportW](crtdbgreport-crtdbgreportw.md) para especificar o destino do texto (somente versão de depuração).

## <a name="syntax"></a>Sintaxe

```C
_HFILE _CrtSetReportFile(
   int reportType,
   _HFILE reportFile
);
```

### <a name="parameters"></a>Parâmetros

*reportType*<br/>
Tipo de relatório: **_CRT_WARN**, **_CRT_ERROR**e **_CRT_ASSERT**.

*reportFile*<br/>
Novo arquivo de relatório para *reportType*.

## <a name="return-value"></a>Valor de retorno

Após a conclusão bem-sucedida, **_CrtSetReportFile** retorna o arquivo de relatório anterior definido para o tipo de relatório especificado em *reportType*. Se um valor inválido for passado para *reportType*, essa função invocará o manipulador de parâmetro inválido, conforme descrito em [validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, **errno** será definido como **EINVAL** e a função retornará **_CRTDBG_HFILE_ERROR**. Para obter mais informações, consulte [errno, _doserrno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentários

**_CrtSetReportFile** é usado com a função [_CrtSetReportMode](crtsetreportmode.md) para definir o destino ou destinos para um tipo de relatório específico gerado pelo **_CrtDbgReport**. Quando **_CrtSetReportMode** tiver sido chamado para atribuir o modo de relatório **_CRTDBG_MODE_FILE** para um tipo de relatório específico, **_CrtSetReportFile** deverá ser chamado para definir o arquivo ou fluxo específico a ser usado como o destino. Quando [_DEBUG](../../c-runtime-library/debug.md) não é definido, as chamadas para **_CrtSetReportFile** são removidas durante o pré-processamento.

A lista a seguir mostra as opções disponíveis para o *REPORTFILE* e o comportamento resultante de **_CrtDbgReport**. Essas opções são definidas como sinalizadores de bits em Crtdbg.h.

- **identificador de arquivo**

   Um identificador para o arquivo que será o destino das mensagens. Nenhuma tentativa é feita para verificar a validade do identificador. É necessário abrir e fechar o identificador do arquivo. Por exemplo:

   ```C
   HANDLE hLogFile;
   hLogFile = CreateFile("c:\\log.txt", GENERIC_WRITE,
      FILE_SHARE_WRITE, NULL, CREATE_ALWAYS,
      FILE_ATTRIBUTE_NORMAL, NULL);
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_WARN, hLogFile);

   _RPT0(_CRT_WARN,"file message\n");
   CloseHandle(hLogFile);
   ```

- **_CRTDBG_FILE_STDERR**

   Grava a mensagem em **stderr**, que pode ser redirecionada da seguinte maneira:

   ```C
   freopen( "c:\\log2.txt", "w", stderr);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);

   _RPT0(_CRT_ERROR,"1st message\n");
   ```

- **_CRTDBG_FILE_STDOUT**

   Grava a mensagem em **stdout**, que você pode redirecionar.

- **_CRTDBG_REPORT_FILE**

   Retorna o modo de relatório atual.

O arquivo de relatório usado por cada tipo de relatório pode ser controlado separadamente. Por exemplo, é possível especificar que um *reportType* de **_CRT_ERROR** seja relatado para **stderr**, enquanto um *reportType* de **_CRT_ASSERT** ser relatado a um identificador de arquivo ou fluxo definido pelo usuário.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|Cabeçalho opcional|
|-------------|---------------------|---------------------|
|**_CrtSetReportFile**|\<crtdbg.h>|\<errno.h>|

Não há suporte para o console em aplicativos Plataforma Universal do Windows (UWP). Os identificadores de fluxo padrão associados ao console, **stdin**, **stdout**e **stderr**devem ser redirecionados antes que as funções de tempo de execução do C possam usá-los em aplicativos UWP. Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

**DLLs** Depurar versões somente de [recursos da biblioteca CRT](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Consulte também

[Rotinas de depuração](../../c-runtime-library/debug-routines.md)<br/>
