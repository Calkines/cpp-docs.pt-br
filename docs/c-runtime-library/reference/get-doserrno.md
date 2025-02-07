---
title: _get_doserrno
ms.date: 11/04/2016
api_name:
- _get_doserrno
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_doserrno
- get_doserrno
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
ms.openlocfilehash: 2810ead8bdd7d6c77cb2b55f4f97371bfc9751e6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956035"
---
# <a name="_get_doserrno"></a>_get_doserrno

Obtém o valor de erro retornado pelo sistema operacional antes que ele seja convertido em um valor **errno** .

## <a name="syntax"></a>Sintaxe

```C
errno_t _get_doserrno(
   int * pValue
);
```

### <a name="parameters"></a>Parâmetros

*pValue*<br/>
Um ponteiro para um inteiro a ser preenchido com o valor atual da macro global **_doserrno** .

## <a name="return-value"></a>Valor de retorno

Se **_get_doserrno** tiver sucesso, retornará zero; Se falhar, ele retornará um código de erro. Se a or for **NULL**, o manipulador de parâmetro *inválido será* invocado, conforme descrito em [validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução tiver permissão para continuar, essa função definirá **errno** como **EINVAL** e retornará **EINVAL**.

## <a name="remarks"></a>Comentários

A macro global **_doserrno** é definida como zero durante a inicialização do CRT, antes do início da execução do processo. Ela é definida para o valor de erro do sistema operacional retornado por qualquer chamada de função de nível do sistema que retorne um erro de sistema operacional. Ela nunca é redefinida para zero durante a execução. Quando você escreve o código para verificar o valor de erro retornado por uma função, sempre limpe **_doserrno** usando [_set_doserrno](set-doserrno.md) antes da chamada de função. Como outra chamada de função pode substituir **_doserrno**, verifique o valor usando **_get_doserrno** imediatamente após a chamada de função.

Recomendamos [_get_errno](get-errno.md) em vez de **_get_doserrno** para códigos de erro portáteis.

Os valores possíveis de **_doserrno** são definidos \<em errno. h >.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|Cabeçalho opcional|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h>, \<cerrno> (C++)|

**_get_doserrno** é uma extensão da Microsoft. Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte também

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
