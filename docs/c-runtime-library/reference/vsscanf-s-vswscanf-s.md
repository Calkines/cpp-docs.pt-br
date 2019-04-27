---
title: vsscanf_s, vswscanf_s
ms.date: 11/04/2016
apiname:
- vswscanf_s
- vsscanf_s
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
- vsscanf_s
- vswscanf_s
- _vstscanf_s
ms.assetid: 7b732e68-c6f4-4579-8917-122f5a7876e1
ms.openlocfilehash: 3106e3533f5bb65334f8a4f3d38f55d886faef4c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188706"
---
# <a name="vsscanfs-vswscanfs"></a>vsscanf_s, vswscanf_s

Lê dados formatados de uma cadeia de caracteres. Essas versões de [vsscanf, vswscanf](vsscanf-vswscanf.md) têm melhorias de segurança, conforme descrito em [Recursos de segurança no CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxe

```C
int vsscanf_s(
   const char *buffer,
   const char *format,
   va_list argptr
);
int vswscanf_s(
   const wchar_t *buffer,
   const wchar_t *format,
   va_list arglist
);
```

### <a name="parameters"></a>Parâmetros

*buffer*<br/>
Dados armazenados

*format*<br/>
Cadeia de caracteres de controle de formato. Para obter mais informações, consulte [Campos de especificação de formato: funções scanf e wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*arglist*<br/>
Lista de argumentos variáveis.

## <a name="return-value"></a>Valor de retorno

Cada uma dessas funções retorna o número de campos que são convertidos e atribuídos com êxito; o valor retornado não inclui campos que foram lidos, mas não atribuídos. Um valor retornado igual a 0 indica que nenhum campo foi atribuído. O valor retornado será **EOF** para um erro ou se o final da cadeia de caracteres for atingido antes da primeira conversão.

Se *buffer* ou *formato* é um **nulo** ponteiro, o manipulador de parâmetro inválido será invocado, conforme descrito no [validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, essas funções retornarão -1 e defina **errno** à **EINVAL**.

Para obter mais informações sobre esses e outros códigos de erro, consulte [errno, _doserrno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentários

O **vsscanf_s** função lê dados da *buffer* nos locais fornecidos por cada argumento na *arglist* lista de argumentos. Os argumentos na lista de argumentos especificam ponteiros para variáveis que têm um tipo que corresponde a um especificador de tipo em *formato*. Ao contrário da versão menos segura **vsscanf**, um parâmetro de tamanho do buffer é necessário quando você usa os caracteres de campo do tipo **c**, **C**, **s**, **S**, ou conjuntos de controle de cadeia de caracteres que são colocados entre **[]**. O tamanho do buffer em caracteres deve ser fornecido como um parâmetro adicional imediatamente após cada parâmetro de buffer que precisa dele.

O tamanho do buffer inclui o nulo de terminação. Um campo de especificação de largura pode ser usado para garantir que o token lido caiba no buffer. Se nenhum campo de especificação de largura for usado e o token lido for muito grande para caber no buffer, nada será gravado no buffer.

Para obter mais informações, consulte os caracteres de campo do tipo [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) e [scanf](../../c-runtime-library/scanf-type-field-characters.md).

> [!NOTE]
> O parâmetro de tamanho é do tipo **sem sinal**, e não **size_t**.

O *formato* controles de argumento a interpretação da entrada campos e tem o mesmo formato e função que o *formato* argumento para o **scanf_s** função. Se ocorrer cópia entre cadeias de caracteres que se sobrepõem, o comportamento será indefinido.

**vswscanf_s** é uma versão de caractere largo de **vsscanf_s**; os argumentos a serem **vswscanf_s** são cadeias de caracteres largos. **vsscanf_s** não manipula caracteres hexadecimais multibyte. **vswscanf_s** não manipula hexadecimal de largura total Unicode ou caracteres de "zona de compatibilidade". Caso contrário, **vswscanf_s** e **vsscanf_s** se comportam de forma idêntica.

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina TCHAR.H|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vstscanf_s**|**vsscanf_s**|**vsscanf_s**|**vswscanf_s**|

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**vsscanf_s**|\<stdio.h>|
|**vswscanf_s**|\<stdio.h> ou \<wchar.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_vsscanf_s.c
// compile with: /W3
// This program uses vsscanf_s to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>
#include <stdarg.h>
#include <stdlib.h>

int call_vsscanf_s(char *tokenstring, char *format, ...)
{
    int result;
    va_list arglist;
    va_start(arglist, format);
    result = vsscanf_s(tokenstring, format, arglist);
    va_end(arglist);
    return result;
}

int main( void )
{
    char  tokenstring[] = "15 12 14...";
    char  s[81];
    char  c;
    int   i;
    float fp;

    // Input various data from tokenstring:
    // max 80 character string:
    call_vsscanf_s(tokenstring, "%80s", s, _countof(s));
    call_vsscanf_s(tokenstring, "%c", &c, sizeof(char));
    call_vsscanf_s(tokenstring, "%d", &i);
    call_vsscanf_s(tokenstring, "%f", &fp);

    // Output the data read
    printf("String    = %s\n", s);
    printf("Character = %c\n", c);
    printf("Integer:  = %d\n", i);
    printf("Real:     = %f\n", fp);
}
```

```Output
String    = 15
Character = 1
Integer:  = 15
Real:     = 15.000000
```

## <a name="see-also"></a>Consulte também

[E/S de fluxo](../../c-runtime-library/stream-i-o.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[vsscanf, vswscanf](vsscanf-vswscanf.md)<br/>
