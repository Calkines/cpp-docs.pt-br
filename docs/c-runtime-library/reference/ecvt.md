---
title: _ecvt
ms.date: 04/05/2018
apiname:
- _ecvt
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ecvt
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
ms.openlocfilehash: 36c9cb2e8cd9eb4dd67bb91e9e4dbd36d8d1fc8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605719"
---
# <a name="ecvt"></a>_ecvt

Converte um **duplas** número em uma cadeia de caracteres. Uma versão mais segura dessa função está disponível. Consulte [_ecvt_s](ecvt-s.md).

## <a name="syntax"></a>Sintaxe

```C
char *_ecvt(
   double value,
   int count,
   int *dec,
   int *sign
);
```

### <a name="parameters"></a>Parâmetros

*value*<br/>
Número a ser convertido.

*count*<br/>
Número de dígitos armazenados.

*dec*<br/>
Posição do ponto decimal armazenada.

*sign*<br/>
Sinal do número convertido.

## <a name="return-value"></a>Valor de retorno

**ecvt** retorna um ponteiro para a cadeia de caracteres de dois dígitos. **Nulo** se ocorreu um erro.

## <a name="remarks"></a>Comentários

O **ecvt** função converte um número de ponto flutuante em uma cadeia de caracteres. O *valor* parâmetro é o número de ponto flutuante a ser convertido. Essa função armazena até *contagem* dígitos do *valor* como uma cadeia de caracteres e acrescenta um caractere nulo ('\0'). Se o número de dígitos na *valor* excede *contagem*, os dígitos de ordem inferior será arredondado. Se houver menos de *contagem* dígitos, a cadeia de caracteres será preenchida com zeros.

O número total de dígitos retornados por **ecvt** não excederá **_CVTBUFSIZE**.

Somente dígitos são armazenados na cadeia de caracteres. A posição do ponto decimal e o sinal de *valor* pode ser obtido *dec* e *entrada* após a chamada. O *dec* parâmetro aponta para um valor inteiro dando a posição do ponto decimal em relação ao início da cadeia de caracteres. Um valor inteiro de 0 ou negativo indica que o ponto decimal se encontra à esquerda do primeiro dígito. O *sinal* parâmetro aponta para um inteiro que indica o sinal do número convertido. Se o valor inteiro for 0, o número será positivo. Caso contrário, o resultado será negativo.

A diferença entre **ecvt** e **fcvt** está na interpretação do *contagem* parâmetro. **ecvt** interpreta *contagem* como o número total de dígitos na cadeia de saída, enquanto **fcvt** interpreta *contagem* como o número de dígitos após o ponto decimal.

**ecvt** e **fcvt** usam um único buffer alocado estaticamente para a conversão. Cada chamada a uma dessas rotinas destrói o resultado da chamada anterior.

Essa função valida seus parâmetros. Se *dec* ou *sinal* está **nulo**, ou *contagem* for 0, o manipulador de parâmetro inválido será invocado, conforme descrito em [parâmetro Validação](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, **errno** é definido como **EINVAL** e **nulo** é retornado.

## <a name="requirements"></a>Requisitos

|Função|Cabeçalho necessário|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_ecvt.c
// compile with: /W3
// This program uses _ecvt to convert a
// floating-point number to a character string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int     decimal,   sign;
   char    *buffer;
   int     precision = 10;
   double  source = 3.1415926535;

   buffer = _ecvt( source, precision, &decimal, &sign ); // C4996
   // Note: _ecvt is deprecated; consider using _ecvt_s instead
   printf( "source: %2.10f   buffer: '%s'  decimal: %d  sign: %d\n",
           source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '3141592654'  decimal: 1  sign: 0
```

## <a name="see-also"></a>Consulte também

[Conversão de Dados](../../c-runtime-library/data-conversion.md)<br/>
[Suporte a ponto flutuante](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
