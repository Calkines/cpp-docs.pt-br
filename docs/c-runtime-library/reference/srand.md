---
title: srand
ms.date: 1/02/2018
apiname:
- srand
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
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- srand
helpviewer_keywords:
- random starting point
- random starting point, setting
- random numbers, generating
- srand function
- numbers, pseudorandom
- numbers, random
- pseudorandom numbers
- starting points, setting random
- starting points
ms.openlocfilehash: 6545d4eba6c17fd55bb2b8cf23fb0319d1c96bee
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57209815"
---
# <a name="srand"></a>srand

Define o valor de semente inicial para o gerador de números pseudoaleatório usado pelas **rand** função.

## <a name="syntax"></a>Sintaxe

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>Parâmetros

*seed*<br/>
Semente para geração de números pseudoaleatórios

## <a name="remarks"></a>Comentários

O **srand** função define o ponto de partida para gerar uma série de inteiros pseudoaleatórios no thread atual. Para reinicializar o gerador para criar a mesma sequência de resultados, chame o **srand** funcionar e usar o mesmo *semente* argumento novamente. Qualquer outro valor para *semente* define o gerador para um ponto de partida diferente na sequência de números pseudoaleatório. **RAND** recupera os números pseudoaleatórios que são gerados. Chamando **rand** antes de qualquer chamada para **srand** gera a mesma sequência que chamar **srand** com *semente* passado como 1.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

Veja o exemplo de [rand](rand.md).

## <a name="see-also"></a>Consulte também

[Suporte a ponto flutuante](../../c-runtime-library/floating-point-support.md)<br/>
[rand](rand.md)<br/>
