---
title: strcmp, wcscmp, _mbscmp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcscmp
- _mbscmp
- strcmp
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _mbscmp
- wcscmp
- strcmp
- _tcscmp
- _ftcscmp
dev_langs:
- C++
helpviewer_keywords:
- tcscmp function
- strcmp function
- strings [C++], comparing
- mbscmp function
- string comparison [C++]
- _mbscmp function
- wcscmp function
- _tcscmp function
- _ftcscmp function
- ftcscmp function
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
caps.latest.revision: 24
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: a79d387f9d312ee090808c39059166550805768a
ms.lasthandoff: 02/25/2017

---
# <a name="strcmp-wcscmp-mbscmp"></a>strcmp, wcscmp, _mbscmp
Compare cadeias de caracteres.  
  
> [!IMPORTANT]
>  `_mbscmp` não pode ser usado em aplicativos executados no [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]. Para obter mais informações, consulte [Funções de CRT sem suporte com /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
int strcmp(  
   const char *string1,  
   const char *string2   
);  
int wcscmp(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbscmp(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `string1`, `string2`  
 Cadeias de caracteres com terminação nula.  
  
## <a name="return-value"></a>Valor de retorno  
 O valor retornado para cada uma dessas funções indica a relação ordinal de `string1` para `string2`.  
  
|Valor|Relação da string1 com a string2|  
|-----------|----------------------------------------|  
|< 0|`string1` é menor que `string2`|  
|0|`string1` é idêntico a `string2`|  
|> 0|`string1` é maior que `string2`|  
  
 Em um erro de validação de parâmetro, `_mbscmp` retorna `_NLSCMPERROR`, que é definido em \<string.h> e \<mbstring.h>.  
  
## <a name="remarks"></a>Comentários  
 A função `strcmp` realiza uma comparação ordinal de `string1` e `string2` e retorna um valor que indica a relação entre eles. `wcscmp` e `_mbscmp` são, respectivamente, versões de caracteres largos e de caracteres multibyte de `strcmp`. `_mbscmp` reconhece sequências de caracteres multibyte de acordo com a página de código multibyte atual e retorna `_NLSCMPERROR` em um erro. Para obter mais informações, consulte [Páginas de Código](../../c-runtime-library/code-pages.md). Além disso, se `string1` ou `string2` for um ponteiro nulo, `_mbscmp` invocará o manipulador de parâmetro inválido, conforme descrito em [Validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, `_mbscmp` retornará `_NLSCMPERROR` e definirá `errno` como `EINVAL`. `strcmp` e `wcscmp` não validam seus parâmetros. Caso contrário, essas três funções se comportam de forma idêntica.  
  
### <a name="generic-text-routine-mappings"></a>Mapeamentos da rotina de texto genérico  
  
|Rotina TCHAR.H|_UNICODE e _MBCS não definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcscmp`|`strcmp`|`_mbscmp`|`wcscmp`|  
  
 As funções `strcmp` diferem das funções `strcoll` em virtude de que as comparações de `strcmp` são ordinais e não são afetadas pela localidade. `strcoll` compara cadeias de caracteres lexicograficamente usando a categoria `LC_COLLATE` da localidade atual. Para obter mais informações sobre a categoria `LC_COLLATE`, consulte [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
 Na localidade "C", a ordem de caracteres no conjunto de caracteres (conjunto de caracteres ASCII) é a mesma que a ordem lexicográfica de caracteres. No entanto, em outras localidades, a ordem de caracteres no conjunto de caracteres pode ser diferente da ordem lexicográfica. Por exemplo, em algumas localidades europeias, o caractere 'a' (valor 0x61) precede o caractere 'ä' (valor 0xE4) no conjunto de caracteres, mas o caractere 'ä' precede a caractere 'a' lexicograficamente.  
  
 Em localidades para as quais o conjunto de caracteres e a ordem lexicográfica dos caracteres são diferentes, você pode usar `strcoll` em vez de `strcmp` para comparação lexicográfica de cadeias de caracteres. Como alternativa, você pode usar `strxfrm` em cadeias de caracteres originais e então usar `strcmp` nas cadeias de caracteres resultantes.  
  
 As funções `strcmp` diferenciam maiúsculas de minúsculas. `_stricmp`, `_wcsicmp` e `_mbsicmp` comparam cadeias de caracteres pelo primeiro convertê-las em seus formulários em minúsculas. Duas cadeias de caracteres que contêm caracteres que estão localizados entre 'Z' e 'a' na tabela ASCII ('[', '`\`', ']', '`^`', '`_`' e '```') são comparadas de modo diferente, dependendo do caso de cada uma. Por exemplo, as duas cadeias de caracteres `"ABCDE"` e `"ABCD^"` são comparadas de uma forma se a comparação é minúscula (`"abcde"` > `"abcd^"`) e de outra forma (`"ABCDE"` < `"ABCD^"`) se a comparação é em maiúsculas.  
  
## <a name="requirements"></a>Requisitos  
  
|Rotina|Cabeçalho necessário|  
|-------------|---------------------|  
|`strcmp`|<string.h>|  
|`wcscmp`|<string.h> ou <wchar.h>|  
|`_mbscmp`|\<mbstring.h>|  
  
 Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Libraries  
 Todas as versões das [bibliotecas em tempo de execução C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Exemplo  
  
```  
// crt_strcmp.c  
  
#include <string.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
char string1[] = "The quick brown dog jumps over the lazy fox";  
char string2[] = "The QUICK brown dog jumps over the lazy fox";  
  
int main( void )  
{  
   char tmp[20];  
   int result;  
  
   // Case sensitive  
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );  
   result = strcmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof (tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof (tmp), "equal to" );  
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );  
  
   // Case insensitive (could use equivalent _stricmp)  
   result = _stricmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof (tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof (tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof (tmp), "equal to" );  
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );  
}  
```  
  
```Output  
Compare strings:  
   The quick brown dog jumps over the lazy fox  
   The QUICK brown dog jumps over the lazy fox  
  
   strcmp:   String 1 is greater than string 2  
   _stricmp:  String 1 is equal to string 2  
```  
  
## <a name="net-framework-equivalent"></a>Equivalente ao .NET Framework  
 [System::String::CompareOrdinal](https://msdn.microsoft.com/en-us/library/system.string.compareordinal.aspx)  
  
## <a name="see-also"></a>Consulte também  
 [Manipulação de cadeias de caracteres](../../c-runtime-library/string-manipulation-crt.md)   
 [memcmp, wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [_memicmp, _memicmp_l](../../c-runtime-library/reference/memicmp-memicmp-l.md)   
 [Funções strcoll](../../c-runtime-library/strcoll-functions.md)   
 [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn, wcsspn, _mbsspn, _mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)