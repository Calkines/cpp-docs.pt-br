---
title: _CrtIsValidPointer
ms.date: 11/04/2016
apiname:
- _CrtIsValidPointer
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
- CrtlsValidPointer
- _CrtIsValidPointer
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
ms.openlocfilehash: 64197d460cdb7dd26d22196c08151be09df48573
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429234"
---
# <a name="crtisvalidpointer"></a>_CrtIsValidPointer

Verifica se um ponteiro não é nulo. Em versões da biblioteca em tempo de execução C anteriores ao Visual Studio 2010, verifica se um intervalo de memória especificado é válido para leitura e gravação (somente versão de depuração).

## <a name="syntax"></a>Sintaxe

```C
int _CrtIsValidPointer(
   const void *address,
   unsigned int size,
   int access
);
```

### <a name="parameters"></a>Parâmetros

*address*<br/>
Aponta para o início do intervalo de memória para testar a validade.

*size*<br/>
Tamanho do intervalo de memória especificado (em bytes).

*access*<br/>
Acessibilidade de leitura/gravação para determinar o intervalo de memória.

## <a name="return-value"></a>Valor de retorno

**Crtisvalidpointer** retornará TRUE se o ponteiro especificado não é nulo. Nas versões da biblioteca CRT anteriores ao Visual Studio 2010, retornará TRUE se o intervalo de memória for válido para as operações especificadas. Caso contrário, a função retorna FALSE.

## <a name="remarks"></a>Comentários

A partir da biblioteca CRT no Visual Studio 2010, o *tamanho* e *access* parâmetros serão ignorados, e **crtisvalidpointer** apenas verifica se a especificado*endereço* não é nulo. Como esse teste é fácil de ser realizado por conta própria, não recomendamos o uso dessa função. Nas versões anteriores do Visual Studio 2010, a função verifica se o intervalo de memória que começa em *endereço* e se estende até *tamanho* bytes é válido para operações de acessibilidade especificadas. Quando *acesso* é definido como TRUE, o intervalo de memória é verificado para leitura e gravação. Quando *acesso* é FALSE, o intervalo de memória é validado somente para leitura. Quando [Debug](../../c-runtime-library/debug.md) não está definido, as chamadas a **crtisvalidpointer** são removidas durante o pré-processamento.

Como essa função retorna TRUE ou FALSE, ela pode ser passada para uma das macros [_ASSERT](assert-asserte-assert-expr-macros.md) para criar um mecanismo simples de tratamento de erro de depuração. O exemplo a seguir causa uma falha de asserção se o intervalo de memória não for válido para as operações de leitura e gravação:

```C
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );
```

Para obter mais informações sobre como **crtisvalidpointer** pode ser usado com outras macros e funções de depuração, consulte [Macros para relatórios](/visualstudio/debugger/macros-for-reporting). Para obter informações sobre como os blocos de memória são alocados, inicializados e gerenciados na versão de depuração do heap de base, consulte [Detalhes do heap de depuração CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**_CrtIsValidPointer**|\<crtdbg.h>|

**Crtisvalidpointer** é uma extensão da Microsoft. Para obter informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Libraries

Somente versões de depuração de [bibliotecas de tempo de execução C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemplo

Consulte o exemplo do tópico [_CrtIsValidHeapPointer](crtisvalidheappointer.md).

## <a name="see-also"></a>Consulte também

[Rotinas de depuração](../../c-runtime-library/debug-routines.md)<br/>
