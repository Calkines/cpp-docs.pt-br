---
title: fesetenv
ms.date: 04/05/2018
apiname:
- fesetenv
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
- fesetenv
- fenv/fesetenv
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
ms.openlocfilehash: 8c91bfbb89df964fed0a632d5fb5ebac47ebe948
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436127"
---
# <a name="fesetenv"></a>fesetenv

Define o ambiente atual de ponto flutuante.

## <a name="syntax"></a>Sintaxe

```C
int fesetenv(
   const fenv_t *penv
);
```

### <a name="parameters"></a>Parâmetros

*penv*<br/>
Ponteiro para um **fenv_t** objeto que contém um ambiente de ponto flutuante conforme definido por uma chamada para [fegetenv](fegetenv1.md) ou [feholdexcept](feholdexcept2.md). Você também pode especificar o ambiente de ponto flutuante de inicialização padrão usando o **FE_DFL_ENV** macro.

## <a name="return-value"></a>Valor de retorno

Retorna 0 se o ambiente foi definido com êxito. Caso contrário, retornará um valor diferente de zero.

## <a name="remarks"></a>Comentários

O **fesetenv** função define o ambiente atual de ponto flutuante do valor armazenado na **fenv_t** objeto apontado por *penv*. O ambiente de ponto flutuante é o conjunto de sinalizadores de status e modos de controle que afetam os cálculos de pontos flutuantes. Isso inclui o modo de arredondamento e os sinalizadores de status para exceções de ponto flutuante.  Se *penv* não está **FE_DFL_ENV** ou não apontar para um válido **fenv_t** do objeto, o comportamento subsequente será indefinido.

Uma chamada para essa função define a exceção de sinalizadores de status que estão na *penv* objeto, mas ele não gera essas exceções.

Para usar essa função, você deve desligar otimizações de ponto flutuante que poderiam impedir o acesso usando a diretiva `#pragma fenv_access(on)` antes da chamada. Para obter mais informações, consulte [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Requisitos

|Função|Cabeçalho C|Cabeçalho C++|
|--------------|--------------|------------------|
|**fesetenv**|\<fenv.h>|\<cfenv>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte também

[Referência da Função Alfabética](crt-alphabetical-function-reference.md)<br/>
[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
