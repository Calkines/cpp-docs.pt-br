---
title: mbstowcs_s, _mbstowcs_s_l
ms.date: 11/04/2016
apiname:
- _mbstowcs_s_l
- mbstowcs_s
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
- _mbstowcs_s_l
- mbstowcs_s
helpviewer_keywords:
- _mbstowcs_s_l function
- mbstowcs_s function
- mbstowcs_s_l function
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
ms.openlocfilehash: 1caedc7e68bf080a5bad52a19ea6be2259a45264
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646986"
---
# <a name="mbstowcss-mbstowcssl"></a>mbstowcs_s, _mbstowcs_s_l

Converte uma sequência de caracteres multibyte em uma sequência de caracteres largos correspondente. As versões de [mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md) com melhorias de segurança, conforme descrito em [Recursos de Segurança no CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxe

```C
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count
);
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t *wcstr,
   size_t sizeInWords,
   const char *mbstr,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t mbstowcs_s(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbstowcs_s_l(
   size_t *pReturnValue,
   wchar_t (&wcstr)[size],
   const char *mbstr,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parâmetros

*pReturnValue*<br/>
O número de caracteres convertidos.

*wcstr*<br/>
Endereço do buffer para a cadeia de caracteres largos convertida resultante.

*sizeInWords*<br/>
O tamanho do *wcstr* buffer em palavras.

*mbstr*<br/>
O endereço de uma sequência de caracteres multibyte terminadas por nulo.

*count*<br/>
O número máximo de caracteres largos para armazenar na *wcstr* buffer, não incluindo o nulo de terminação, ou [TRUNCATE](../../c-runtime-library/truncate.md).

*locale*<br/>
A localidade a ser usada.

## <a name="return-value"></a>Valor de retorno

Zero se for bem-sucedido ou um código de erro em caso de falha.

|Condição de erro|Valor de retorno e **errno**|
|---------------------|------------------------------|
|*wcstr* está **nulo** e *sizeInWords* > 0|**EINVAL**|
|*mbstr* é **nulo**|**EINVAL**|
|O buffer de destino é muito pequeno para conter a cadeia de caracteres convertida (a menos que *contagem* é **TRUNCATE**; consulte os comentários abaixo)|**ERANGE**|
|*wcstr* não é **nulo** e *sizeInWords* = = 0|**EINVAL**|

Se qualquer uma dessas condições ocorrer, a exceção de parâmetro inválido será invocada, conforme descrito em [Validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, a função retorna um código de erro e definirá **errno** conforme indicado na tabela.

## <a name="remarks"></a>Comentários

O **mbstowcs_s** função converte uma cadeia de caracteres multibyte apontada por *mbstr* em caracteres largos armazenados no buffer apontado por *wcstr*. A conversão continuará para cada caractere até que uma das seguintes condições seja atendida:

- Um caractere nulo multibyte é encontrado

- Um caractere multibyte inválido é encontrado

- O número de caracteres largos armazenados na *wcstr* buffer equals *contagem*.

A cadeia de caracteres de destino sempre é terminada em nulo (mesmo em caso de erro).

Se *contagem* é o valor especial [TRUNCATE](../../c-runtime-library/truncate.md), em seguida, **mbstowcs_s** converterá grande parte da cadeia de caracteres que caberá no buffer de destino ainda deixando espaço para um valor nulo terminador.

Se **mbstowcs_s** converte com êxito a cadeia de caracteres de origem, ele colocará o tamanho em caracteres largos da cadeia de caracteres convertida, incluindo o terminador nulo, em  *&#42;pReturnValue* (fornecido *pReturnValue* não é **nulo**). Isso ocorre mesmo se o *wcstr* argumento é **nulo** e fornece uma maneira de determinar o tamanho do buffer. Observe que, se *wcstr* é **nulo**, *contagem* será ignorado, e *sizeInWords* deve ser 0.

Se **mbstowcs_s** encontrar um caractere multibyte inválido, ele colocará 0 em  *&#42;pReturnValue*, definirá o buffer de destino como uma cadeia de caracteres vazia, definirá **errno** para  **EILSEQ**e retorna **EILSEQ**.

Se as sequências apontadas por *mbstr* e *wcstr* se sobrepõem, o comportamento do **mbstowcs_s** é indefinido.

> [!IMPORTANT]
> Certifique-se de que *wcstr* e *mbstr* não se sobrepõem e que *contagem* reflete corretamente o número de caracteres multibyte a ser convertido.

**mbstowcs_s** usa a localidade atual para qualquer comportamento dependente da localidade. **mbstowcs_s_l** é idêntico, exceto que ele usa a localidade passada em vez disso. Para obter mais informações, consulte [Localidade](../../c-runtime-library/locale.md).

Em C++, o uso dessas funções é simplificado pelas sobrecargas de modelo; as sobrecargas podem inferir o tamanho do buffer automaticamente (eliminando a necessidade de especificar um argumento de tamanho) e podem substituir automaticamente funções mais antigas e não seguras por suas equivalentes mais recentes e seguras. Para obter mais informações, consulte [Sobrecargas de modelo seguro](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**mbstowcs_s**|\<stdlib.h>|
|**_mbstowcs_s_l**|\<stdlib.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte também

[Conversão de Dados](../../c-runtime-library/data-conversion.md)<br/>
[Localidade](../../c-runtime-library/locale.md)<br/>
[MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar)<br/>
[Interpretação de sequências de caracteres multibyte](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
