---
title: fscanf, _fscanf_l, fwscanf, _fwscanf_l
ms.date: 11/04/2016
api_name:
- fscanf
- _fwscanf_l
- _fscanf_l
- fwscanf
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
- fscanf
- fwscanf
- _ftscanf_l
- _fwscanf_l
- _ftscanf
- _fscanf_l
helpviewer_keywords:
- fscanf function
- fwscanf function
- formatted data [C++], reading from streams
- ftscanf_l function
- _ftscanf_l function
- _fwscanf_l function
- data [CRT], reading from streams
- _fscanf_l function
- ftscanf function
- fscanf_l function
- streams [C++], reading formatted data from
- _ftscanf function
- fwscanf_l function
ms.assetid: 9004e978-6c5f-4bb2-98fd-51e5948933f2
ms.openlocfilehash: 1c143cbc1bf642e7efc6f10b9615fdaca8a236d1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956627"
---
# <a name="fscanf-_fscanf_l-fwscanf-_fwscanf_l"></a>fscanf, _fscanf_l, fwscanf, _fwscanf_l

Leia dados formatados de um fluxo. Versões mais seguras dessas funções estão disponíveis; consulte [fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md).

## <a name="syntax"></a>Sintaxe

```C
int fscanf(
   FILE *stream,
   const char *format [,
   argument ]...
);
int _fscanf_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument ]...
);
int fwscanf(
   FILE *stream,
   const wchar_t *format [,
   argument ]...
);
int _fwscanf_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument ]...
);
```

### <a name="parameters"></a>Parâmetros

*stream*<br/>
Ponteiro para a estrutura **FILE**.

*format*<br/>
Cadeia de caracteres de controle de formato.

*argument*<br/>
Argumentos opcionais.

*locale*<br/>
A localidade a ser usada.

## <a name="return-value"></a>Valor de retorno

Cada uma dessas funções retorna o número de campos convertidos e atribuídos com êxito; o valor retornado não inclui campos que foram lidos, mas não atribuídos. Um valor retornado igual a 0 indica que nenhum campo foi atribuído. Se ocorrer um erro ou se o final do fluxo de arquivos for atingido antes da primeira conversão, o valor de retorno será **EOF** para **fscanf** e **fwscanf**.

Essas funções validam seus parâmetros. Se *Stream* ou *Format* for um ponteiro NULL, o manipulador de parâmetro inválido será invocado, conforme descrito em [validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução tiver permissão para continuar, essas funções retornam **EOF** e definem **errno** como **EINVAL**.

## <a name="remarks"></a>Comentários

A função **fscanf** lê dados da posição atual do *fluxo* para os locais fornecidos pelo *argumento* (se houver). Cada *argumento* deve ser um ponteiro para uma variável de um tipo que corresponde a um especificador de tipo no *formato*. o *formato* controla a interpretação dos campos de entrada e tem a mesma forma e função que o argumento de *formato* para **scanf**; consulte [scanf](scanf-scanf-l-wscanf-wscanf-l.md) para obter uma descrição do *formato*.

**fwscanf** é uma versão de caractere largo do **fscanf**; o argumento format para **fwscanf** é uma cadeia de caracteres largos. Essas funções terão comportamento idêntico se o fluxo for aberto no modo ANSI. Atualmente, o **fscanf** não dá suporte à entrada de um fluxo Unicode.

As versões dessas funções com o sufixo **_L** são idênticas, exceto pelo fato de que usam o parâmetro de localidade passado em vez da localidade do thread atual.

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina TCHAR.H|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftscanf**|**fscanf**|**fscanf**|**fwscanf**|
|**_ftscanf_l**|**_fscanf_l**|**_fscanf_l**|**_fwscanf_l**|

Para obter mais informações, consulte [Format Specification Fields-scanf Functions and wscanf Functions](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Requisitos

|Função|Cabeçalho necessário|
|--------------|---------------------|
|**fscanf**, **_fscanf_l**|\<stdio.h>|
|**fwscanf**, **_fwscanf_l**|\<stdio.h> ou \<wchar.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_fscanf.c
// compile with: /W3
// This program writes formatted
// data to a file. It then uses fscanf to
// read the various data back from the file.

#include <stdio.h>

FILE *stream;

int main( void )
{
   long l;
   float fp;
   char s[81];
   char c;

   if( fopen_s( &stream, "fscanf.out", "w+" ) != 0 )
      printf( "The file fscanf.out was not opened\n" );
   else
   {
      fprintf( stream, "%s %ld %f%c", "a-string",
               65000, 3.14159, 'x' );
      // Security caution!
      // Beware loading data from a file without confirming its size,
      // as it may lead to a buffer overrun situation.

      // Set pointer to beginning of file:
      fseek( stream, 0L, SEEK_SET );

      // Read data back from file:
      fscanf( stream, "%s", s );   // C4996
      fscanf( stream, "%ld", &l ); // C4996

      fscanf( stream, "%f", &fp ); // C4996
      fscanf( stream, "%c", &c );  // C4996
      // Note: fscanf is deprecated; consider using fscanf_s instead

      // Output data read:
      printf( "%s\n", s );
      printf( "%ld\n", l );
      printf( "%f\n", fp );
      printf( "%c\n", c );

      fclose( stream );
   }
}
```

```Output
a-string
65000
3.141590
x
```

## <a name="see-also"></a>Consulte também

[E/S de fluxo](../../c-runtime-library/stream-i-o.md)<br/>
[_cscanf, _cscanf_l, _cwscanf, _cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>
