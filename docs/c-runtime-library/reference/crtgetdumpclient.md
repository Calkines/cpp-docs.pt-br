---
title: _CrtGetDumpClient
ms.date: 11/04/2016
apiname:
- _CrtGetDumpClient
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
- CrtGetDumpClient
- _CrtGetDumpClient
helpviewer_keywords:
- _CrtGetDumpClient function
- CrtGetDumpClient function
ms.assetid: 9051867f-341b-493b-b53d-45d2b454a3ad
ms.openlocfilehash: e4700bd936bec97014508c4a971f6e6c278c6a11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550729"
---
# <a name="crtgetdumpclient"></a>_CrtGetDumpClient

Recupera a função definida pelo aplicativo atual para despejar os **client_block** blocos de memória (somente versão de depuração) do tipo.

## <a name="syntax"></a>Sintaxe

```C
_CRT_DUMP_CLIENT _CrtGetDumpClient( void );
```

## <a name="return-value"></a>Valor de retorno

Retorna a rotina de despejo atual.

## <a name="remarks"></a>Comentários

O **crtgetdumpclient** função recupera a função de gancho atual para despejar objetos armazenados na **client_block** processo de despejo de memória de depuração de blocos de memória para o tempo de execução C.

Para obter mais informações sobre como usar outras funções em tempo de execução compatíveis com gancho e escrever suas próprias funções de gancho definidas pelo cliente, consulte [Gravação da função de gancho de depuração](/visualstudio/debugger/debug-hook-function-writing).

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**_CrtGetDumpClient**|\<crtdbg.h>|

Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Libraries

Somente versões de depuração de [bibliotecas de tempo de execução C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Consulte também

[Rotinas de depuração](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtSetDumpClient](crtsetdumpclient.md)<br/>
