---
title: sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l
ms.date: 11/04/2016
apiname:
- _swprintf_s_l
- _sprintf_s_l
- swprintf_s
- sprintf_s
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- swprintf_s
- sprintf_s
- stdio/sprintf_s
- stdio/swprintf_s
- stdio/_sprintf_s_l
- stdio/_swprintf_s_l
- _sprintf_s_l
- _swprintf_s_l
helpviewer_keywords:
- stprintf_s function
- stprintf_s_l function
- swprintf_s_l function
- sprintf_s function
- swprintf_s function
- _swprintf_s_l function
- sprintf_s_l function
- _stprintf_s_l function
- _stprintf_s function
- _sprintf_s_l function
- formatted text [C++]
ms.assetid: 424f0a29-22ef-40e8-b565-969f5f57782f
ms.openlocfilehash: 4d4bec339caccf9b0843afada4b56b435243dd11
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210881"
---
# <a name="sprintfs-sprintfsl-swprintfs-swprintfsl"></a>sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l

Grave os dados formatados em uma cadeia de caracteres. Estas são versões de [sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) com aprimoramentos de segurança, conforme descrito em [Recursos de segurança no CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxe

```C
int sprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   ...
);
int _sprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   locale_t locale,
   ...
);
int swprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   ...
);
int _swprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   locale_t locale,
   ...
);
template <size_t size>
int sprintf_s(
   char (&buffer)[size],
   const char *format,
   ...
); // C++ only
template <size_t size>
int swprintf_s(
   wchar_t (&buffer)[size],
   const wchar_t *format,
   ...
); // C++ only
```

### <a name="parameters"></a>Parâmetros

*buffer*<br/>
Local de armazenamento para a saída

*sizeOfBuffer*<br/>
O número máximo de caracteres a ser armazenado.

*format*<br/>
Cadeia de caracteres de controle de formato

*...*<br/>
Argumentos opcionais para serem formatados

*locale*<br/>
A localidade a ser usada.

Para obter mais informações, consulte [Especificações de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Valor de retorno

O número de caracteres gravados ou -1 se ocorreu um erro. Se *buffer* ou *formato* é um ponteiro nulo, **sprintf_s** e **swprintf_s** retornar -1 e definir **errno**para **EINVAL**.

**sprintf_s** retorna o número de bytes armazenados no *buffer*, sem contar o caractere nulo de terminação. **swprintf_s** retorna o número de caracteres largos armazenados no *buffer*, sem contar o caractere largo nulo de terminação.

## <a name="remarks"></a>Comentários

O **sprintf_s** função formata e armazena uma série de caracteres e valores em *buffer*. Cada *argumento* (se houver) é convertido e gerado de acordo com a especificação de formato correspondente em *formato*. O formato consiste em caracteres comuns e tem o mesmo formato e função que o *formato* argumento para [printf](printf-printf-l-wprintf-wprintf-l.md). Um caractere nulo é acrescentado após o último caractere escrito. Se ocorrer cópia entre cadeias de caracteres que se sobrepõem, o comportamento será indefinido.

Uma diferença principal entre **sprintf_s** e [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) é que **sprintf_s** verifica a cadeia de caracteres de formato para caracteres de formatação válidos, enquanto [ sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) apenas verifica se a cadeia de caracteres de formato ou buffer são **nulo** ponteiros. Se uma das verificações falhar, o manipulador de parâmetro inválido será invocado, conforme descrito em [Validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, a função retornará -1 e definirá **errno** à **EINVAL**.

A diferença principal entre **sprintf_s** e [sprintf](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) é que **sprintf_s** assume um parâmetro de comprimento que especifica o tamanho do buffer de saída em caracteres. Se o buffer é muito pequeno para o texto formatado, incluindo o nulo de terminação, em seguida, o buffer será definido como uma cadeia vazia colocando um caractere nulo em *buffer*[0], e o manipulador de parâmetro inválido será invocado. Diferentemente **snprintf**, **sprintf_s** garante que o buffer será finalizado como nulo, a menos que o tamanho do buffer é zero.

**swprintf_s** é uma versão de caractere largo de **sprintf_s**; os argumentos de ponteiro para **swprintf_s** são cadeias de caracteres largos. Detecção de erros de codificação **swprintf_s** pode ser diferente no **sprintf_s**. As versões dessas funções com o **l** sufixo são idênticas, exceto que eles usam o parâmetro de localidade passado em vez da localidade do thread atual.

No C++, o uso dessas funções é simplificado por sobrecargas de modelo. As sobrecargas podem inferir o tamanho do buffer automaticamente, eliminando a necessidade de especificar um argumento de tamanho; além disso, elas podem substituir automaticamente funções mais antigas e não seguras por equivalentes mais novas e seguras. Para obter mais informações, consulte [Sobrecargas de modelo seguro](../../c-runtime-library/secure-template-overloads.md).

Existem versões do **sprintf_s** que oferecem controle adicional sobre o que acontece se o buffer for muito pequeno. Para obter mais informações, consulte [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md).

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina TCHAR.H|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stprintf_s**|**sprintf_s**|**sprintf_s**|**swprintf_s**|
|**_stprintf_s_l**|**_sprintf_s_l**|**_sprintf_s_l**|**_swprintf_s_l**|

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**sprintf_s**, **_sprintf_s_l**|C: \<stdio.h><br /><br /> C++: \<cstdio> ou \<stdio.h>|
|**swprintf_s**, **_swprintf_s_l**|C: \<stdio.h> ou \<wchar.h><br /><br /> C++: \<cstdio>, \<cwchar>, \<stdio.h> ou \<wchar.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_sprintf_s.c
// This program uses sprintf_s to format various
// data and place them in the string named buffer.
//

#include <stdio.h>

int main( void )
{
   char  buffer[200], s[] = "computer", c = 'l';
   int   i = 35, j;
   float fp = 1.7320534f;

   // Format and print various data:
   j  = sprintf_s( buffer, 200,     "   String:    %s\n", s );
   j += sprintf_s( buffer + j, 200 - j, "   Character: %c\n", c );
   j += sprintf_s( buffer + j, 200 - j, "   Integer:   %d\n", i );
   j += sprintf_s( buffer + j, 200 - j, "   Real:      %f\n", fp );

   printf_s( "Output:\n%s\ncharacter count = %d\n", buffer, j );
}
```

```Output
Output:
   String:    computer
   Character: l
   Integer:   35
   Real:      1.732053

character count = 79
```

## <a name="example"></a>Exemplo

```C
// crt_swprintf_s.c
// wide character example
// also demonstrates swprintf_s returning error code
#include <stdio.h>

int main( void )
{
   wchar_t buf[100];
   int len = swprintf_s( buf, 100, L"%s", L"Hello world" );
   printf( "wrote %d characters\n", len );
   len = swprintf_s( buf, 100, L"%s", L"Hello\xffff world" );
   // swprintf_s fails because string contains WEOF (\xffff)
   printf( "wrote %d characters\n", len );
}
```

```Output
wrote 11 characters
wrote -1 characters
```

## <a name="see-also"></a>Consulte também

[E/S de fluxo](../../c-runtime-library/stream-i-o.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, __swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[Funções vprintf](../../c-runtime-library/vprintf-functions.md)<br/>
