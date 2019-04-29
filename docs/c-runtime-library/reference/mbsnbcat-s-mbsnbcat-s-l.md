---
title: _mbsnbcat_s, _mbsnbcat_s_l
ms.date: 11/04/2016
apiname:
- _mbsnbcat_s_l
- _mbsnbcat_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbsnbcat_s
- mbsnbcat_s
- _mbsnbcat_s_l
- mbsnbcat_s_l
helpviewer_keywords:
- _tcsncat function
- mbsnbcat_s function
- _mbsnbcat_s function
- _mbsnbcat_s_l function
- _tcsncat_s_l function
- tcsncat_s_l function
- mbsnbcat_s_l function
- tcsncat function
ms.assetid: 2c9e9be7-d979-4a54-8ada-23428b6648a9
ms.openlocfilehash: d7e7a9d121336486e590ca3bd9e3967b02a2df08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331513"
---
# <a name="mbsnbcats-mbsnbcatsl"></a>_mbsnbcat_s, _mbsnbcat_s_l

Acrescenta a cadeia de caracteres multibyte, no máximo, os primeiros **n** bytes de outra cadeia de caracteres multibyte. Essas são versões de [_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md), mas têm melhorias de segurança, conforme descrito em [Recursos de segurança no CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Esta API não pode ser usada em aplicativos executados no Tempo de Execução do Windows. Para obter mais informações, confira [Funções do CRT sem suporte em aplicativos da Plataforma Universal do Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxe

```C
errno_t _mbsnbcat_s(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count
);
errno_t _mbsnbcat_s_l(
   unsigned char *dest,
   size_t sizeInBytes,
   const unsigned char *src,
   size_t count,
   _locale_t locale
);
template <size_t size>
errno_t _mbsnbcat_s(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count
); // C++ only
template <size_t size>
errno_t _mbsnbcat_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   size_t count,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Parâmetros

*dest*<br/>
Cadeia de caracteres de destino de caractere multibyte terminada em nulo.

*sizeInBytes*<br/>
Tamanho do *dest* buffer em bytes.

*src*<br/>
Cadeia de caracteres de origem de caractere multibyte terminada em nulo.

*count*<br/>
Número de bytes do *src* para acrescentar ao *dest*.

*locale*<br/>
Localidade a usar.

## <a name="return-value"></a>Valor de retorno

Zero se for bem-sucedido, caso contrário, um código de erro.

### <a name="error-conditions"></a>Condições de Erro

|**Dest**|*sizeInBytes*|*src*|Valor retornado|
|------------|-------------------|-----------|------------------|
|**NULL**|qualquer|qualquer|**EINVAL**|
|Qualquer|<= 0|qualquer|**EINVAL**|
|Qualquer|qualquer|**NULL**|**EINVAL**|

Se qualquer uma das condições de erro ocorrer, a função gerará um erro de parâmetro inválido, conforme descrito em [Validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se o erro for tratado, a função retornará **EINVAL** e define **errno** para **EINVAL**.

## <a name="remarks"></a>Comentários

O **mbsnbcat_s** função acrescenta à *dest*, no máximo, o primeiro *contagem* bytes de *src*. Se o byte imediatamente antes do caractere nulo em *dest* é um byte inicial, ele será substituído pelo byte inicial de *src*. Caso contrário, o byte inicial de *src* substitui o caractere nulo de terminação de *dest*. Se aparecer um byte nulo no *src* antes de *contagem* bytes serem acrescentados, **mbsnbcat_s** acrescentará todos os bytes de *src*, até o nulo caractere. Se *contagem* é maior que o comprimento de *src*, o comprimento da *src* é usado no lugar de *contagem*. A cadeia de caracteres resultante é terminada por um caractere nulo. Se ocorrer cópia entre cadeias de caracteres que se sobrepõem, o comportamento será indefinido.

O valor de saída é afetado pela configuração da **LC_CTYPE** configuração da categoria da localidade; consulte [setlocale, wsetlocale](setlocale-wsetlocale.md) para obter mais informações. As versões dessas funções são idênticas, exceto que aquelas que não têm o **l** sufixo usam a localidade atual e aqueles que têm o **l** sufixo, em vez disso, use o parâmetro de localidade que passado. Para obter mais informações, consulte [Localidade](../../c-runtime-library/locale.md).

No C++, o uso dessas funções é simplificado por sobrecargas de modelo, as sobrecargas podem inferir o tamanho do buffer automaticamente, eliminando a necessidade de especificar um argumento de tamanho e podem usar automaticamente suas funções mais novas e mais seguras para substituir funções mais antigas e menos seguras. Para obter mais informações, consulte [Sobrecargas de modelo seguro](../../c-runtime-library/secure-template-overloads.md).

As versões de depuração dessas funções preenchem primeiro o buffer com 0xFD. Para desabilitar esse comportamento, use [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina Tchar.h|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsncat**|[strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|**_mbsnbcat_s**|[wcsncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|
|**_tcsncat_s_l**|**_strncat_s_l**|**_mbsnbcat_s_l**|**_wcsncat_s_l**|

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**_mbsnbcat_s**|\<mbstring.h>|
|**_mbsnbcat_s_l**|\<mbstring.h>|

Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte também

[Manipulação de cadeias de caracteres](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_strncnt, _wcsncnt, _mbsnbcnt, _mbsnbcnt_l, _mbsnccnt, _mbsnccnt_l](strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)<br/>
[_mbsnbcpy, _mbsnbcpy_l](mbsnbcpy-mbsnbcpy-l.md)<br/>
[_mbsnbcpy_s, _mbsnbcpy_s_l](mbsnbcpy-s-mbsnbcpy-s-l.md)<br/>
[_mbsnbset, _mbsnbset_l](mbsnbset-mbsnbset-l.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncat_s, _strncat_s_l, wcsncat_s, _wcsncat_s_l, _mbsncat_s, _mbsncat_s_l](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)<br/>
