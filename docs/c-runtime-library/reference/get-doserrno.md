---
title: _get_doserrno
ms.date: 11/04/2016
apiname:
- _get_doserrno
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
- _get_doserrno
- get_doserrno
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
ms.openlocfilehash: 700f710e6d94f48b03697325bb720dbc539fe04e
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331016"
---
# <a name="getdoserrno"></a>_get_doserrno

Obtém o valor de erro retornado pelo sistema operacional antes de ele ser convertido para um **errno** valor.

## <a name="syntax"></a>Sintaxe

```C
errno_t _get_doserrno(
   int * pValue
);
```

### <a name="parameters"></a>Parâmetros

*pValue*<br/>
Um ponteiro para um inteiro a ser preenchido com o valor atual de **doserrno** macro global.

## <a name="return-value"></a>Valor de retorno

Se **get_doserrno** for bem-sucedida, ele retorna zero; se ele falhar, ele retorna um código de erro. Se *pValue* é **nulo**, o manipulador de parâmetro inválido será invocado, conforme descrito na [validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, essa função definirá **errno** à **EINVAL** e retorna **EINVAL**.

## <a name="remarks"></a>Comentários

O **doserrno** macro global é definida como zero durante a inicialização do CRT, antes do processo de execução começa. Ela é definida para o valor de erro do sistema operacional retornado por qualquer chamada de função de nível do sistema que retorne um erro de sistema operacional. Ela nunca é redefinida para zero durante a execução. Ao escrever o código para verificar o valor de erro retornado por uma função, sempre limpe **doserrno** usando [set_doserrno](set-doserrno.md) antes da chamada de função. Porque outra chamada de função pode substituir **doserrno**, verifique o valor usando **get_doserrno** imediatamente após a chamada de função.

É recomendável [get_errno](get-errno.md) em vez de **get_doserrno** para códigos de erro portáteis.

Os valores possíveis da **doserrno** são definidos em \<errno. h >.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|Cabeçalho opcional|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h>, \<cerrno> (C++)|

**get_doserrno** é uma extensão da Microsoft. Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte também

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
