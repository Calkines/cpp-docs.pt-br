---
title: _cexit, _c_exit
ms.date: 11/04/2016
apiname:
- _c_exit
- _cexit
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
- _cexit
- c_exit
- _c_exit
- cexit
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
ms.openlocfilehash: a075e8a8e965a195765b86ffa21fed0915dbf5ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335484"
---
# <a name="cexit-cexit"></a>_cexit, _c_exit

Executa operações de limpeza e retorna sem encerrar o processo.

## <a name="syntax"></a>Sintaxe

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Comentários

O **cexit** chamadas de função, no último a entrar, primeiro a sair (UEPS) ordem, as funções registradas por **atexit** e **OnExit**. Em seguida **cexit** libera todos os buffers de e/s e fecha todos os fluxos abertos antes de retornar. **c_exit** é o mesmo que **exit** , mas retorna para o processo de chamada sem processamento **atexit** ou **OnExit** ou liberar buffers de fluxo. O comportamento de **saia**, **exit**, **cexit**, e **c_exit** é mostrado na tabela a seguir.

|Função|Comportamento|
|--------------|--------------|
|**exit**|Executa procedimentos completos de encerramento de biblioteca C, encerra o processo e sai com código de status fornecido.|
|**_exit**|Executa procedimentos rápidos de encerramento de biblioteca C, encerra o processo e sai com código de status fornecido.|
|**_cexit**|Executa procedimentos completos de encerramento de biblioteca C e retorna ao chamador, mas não encerra o processo.|
|**_c_exit**|Executa procedimentos rápidos de encerramento de biblioteca C e retorna ao chamador, mas não encerra o processo.|

Quando você chama o **cexit** ou **c_exit** funções, os destruidores de quaisquer objetos temporários ou automáticos que existem no momento da chamada não são chamados. Um objeto automático é um objeto definido em uma função na qual o objeto não é declarado como estático. Um objeto temporário é um objeto criado pelo compilador. Para destruir um objeto automático antes de chamar **cexit** ou **c_exit**explicitamente chamar o destruidor do objeto, da seguinte maneira:

```cpp
myObject.myClass::~myClass( );
```

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**_cexit**|\<process.h>|
|**_c_exit**|\<process.h>|

Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte também

[Controle de processo e de ambiente](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[Funções _exec, _wexec](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[Funções _spawn, _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
