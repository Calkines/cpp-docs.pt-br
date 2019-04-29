---
title: _mbsnbicmp, _mbsnbicmp_l
ms.date: 11/04/2016
apiname:
- _mbsnbicmp_l
- _mbsnbicmp
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
- _strnicmp
- _wcsnicmp_l
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _tcsnicmp
- _strnicmp_l
- _tcsnicmp_l
- _wcsnicmp
- _mbsnbicmp_l
helpviewer_keywords:
- _tcsnicmp_l function
- _strnicmp function
- mbsnbicmp_l function
- _wcsnicmp_l function
- _mbsnbicmp function
- _mbsnbicmp_l function
- _tcsnicmp function
- _strnicmp_l function
- mbsnbicmp function
- _wcsnicmp function
ms.assetid: ddb44974-8b0c-42f0-90d0-56c9350bae0c
ms.openlocfilehash: 059d0781e465f6491f27fd634bbc4479104bc12f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331292"
---
# <a name="mbsnbicmp-mbsnbicmpl"></a>_mbsnbicmp, _mbsnbicmp_l

Compara **n** bytes de caracteres multibyte duas cadeias de caracteres e diferencia maiusculas e minúsculas.

> [!IMPORTANT]
> Esta API não pode ser usada em aplicativos executados no Tempo de Execução do Windows. Para obter mais informações, confira [Funções do CRT sem suporte em aplicativos da Plataforma Universal do Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxe

```C
int _mbsnbicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>Parâmetros

*string1*, *string2*<br/>
Cadeias de caracteres com terminação nula.

*count*<br/>
Número de bytes a serem comparados.

## <a name="return-value"></a>Valor de retorno

O valor retornado indica a relação entre as subcadeias de caracteres.

|Valor retornado|Descrição|
|------------------|-----------------|
|< 0|*string1* subcadeia de caracteres menor que *string2* subcadeia de caracteres.|
|0|*string1* subcadeia de caracteres idêntica à *string2* subcadeia de caracteres.|
|> 0|*string1* subcadeia de caracteres maior que *string2* subcadeia de caracteres.|

Em um erro **mbsnbicmp** retorna **_NLSCMPERROR**, que é definido em String. h e mbstring.

## <a name="remarks"></a>Comentários

O **mbsnbicmp** função executa uma comparação ordinal de no máximo os primeiros *contagem* bytes de *string1* e *string2*. A comparação é executada convertendo cada caractere em minúsculas; [mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) é uma versão diferencia maiusculas de minúsculas do **mbsnbicmp**. A comparação termina se um caractere nulo de terminação for atingido na cadeia de caracteres antes de *contagem* caracteres serem comparados. Se as cadeias de caracteres são iguais quando um caractere nulo de terminação for atingido na cadeia de caracteres antes de *contagem* caracteres são comparados, a cadeia de caracteres mais curta será menor.

**mbsnbicmp** é semelhante ao [mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md), exceto que ela compara cadeias de caracteres até *contagem* bytes em vez de por caracteres.

Duas cadeias de caracteres que contêm caracteres localizados entre 'Z' e 'a' na tabela ASCII ('[', '\\', ']', '^', '_' e '\`') são comparadas de modo diferente, dependendo das maiúsculas e minúsculas delas. Por exemplo, as duas cadeias de caracteres "ABCDE" e "ABCD ^" comparadas de uma forma se a comparação é minúscula ("abcde" > "abcd ^") e de outra forma ("ABCDE" < "ABCD ^") se ele estiver em maiusculas.

**mbsnbicmp** reconhece sequências de caracteres multibyte de acordo com o [página de código multibyte](../../c-runtime-library/code-pages.md) atualmente em uso. Ela não é afetada pela configuração da localidade atual.

Se qualquer um dos *string1* ou *string2* é um ponteiro nulo, **mbsnbicmp** invocará o manipulador de parâmetro inválido, conforme descrito em [devalidaçãodeparâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, a função retornará **_NLSCMPERROR** e define **errno** para **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico

|Rotina Tchar.h|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**_mbsnbicmp**|\<mbstring.h>|

Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

Veja o exemplo de [_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md).

## <a name="see-also"></a>Consulte também

[Manipulação de cadeias de caracteres](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
