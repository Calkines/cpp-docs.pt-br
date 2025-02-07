---
title: memcpy_s, wmemcpy_s
ms.date: 11/04/2016
api_name:
- memcpy_s
- wmemcpy_s
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemcpy_s
- memcpy_s
helpviewer_keywords:
- memcpy_s function
- wmemcpy_s function
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
ms.openlocfilehash: 8078590df6950201ef81356ba6c28173e80572ee
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952794"
---
# <a name="memcpy_s-wmemcpy_s"></a>memcpy_s, wmemcpy_s

Copia bytes entre buffers. Estas são versões de [memcpy, wmemcpy](memcpy-wmemcpy.md) com melhorias de segurança, conforme descrito em [Recursos de Segurança no CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxe

```C
errno_t memcpy_s(
   void *dest,
   size_t destSize,
   const void *src,
   size_t count
);
errno_t wmemcpy_s(
   wchar_t *dest,
   size_t destSize,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Parâmetros

*dest*<br/>
Novo buffer.

*destSize*<br/>
Tamanho do buffer de destino, em bytes para memcpy_s e caracteres largos (wchar_t) para wmemcpy_s.

*src*<br/>
Buffer do qual copiar.

*count*<br/>
O número de caracteres a serem copiados.

## <a name="return-value"></a>Valor de retorno

Zero se for bem-sucedido; um código de erro em caso de falha.

### <a name="error-conditions"></a>Condições de Erro

|*dest*|*destSize*|*src*|*count*|Valor retornado|Conteúdo do *dest*|
|------------|----------------|-----------|---|------------------|------------------------|
|qualquer|qualquer|qualquer|0|0|Não modificado|
|**NULL**|qualquer|qualquer|diferente de zero|**EINVAL**|Não modificado|
|qualquer|qualquer|**NULL**|diferente de zero|**EINVAL**|o *dest* está zerado|
|qualquer|< *contar*|qualquer|diferente de zero|**ERANGE**|o *dest* está zerado|

## <a name="remarks"></a>Comentários

**memcpy_s** copia bytes de *contagem* de *src* para *dest*; o **wmemcpy_s** copia os caracteres largos da *contagem* (dois bytes). Se a origem e o destino se sobrepõem, o comportamento de **memcpy_s** é indefinido. Use **memmove_s** para lidar com regiões sobrepostas.

Essas funções validam seus parâmetros. Se *Count* for diferente de zero e *dest* ou *src* for um ponteiro nulo, ou *destSize* for menor que *Count*, essas funções invocarão o manipulador de parâmetro inválido, conforme descrito em [validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução tiver permissão para continuar, essas funções retornarão **EINVAL** ou **ERANGE** e definirá **errno** como o valor de retorno.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**memcpy_s**|\<memory.h> ou \<string.h>|
|**wmemcpy_s**|\<wchar.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_memcpy_s.c
// Copy memory in a more secure way.

#include <memory.h>
#include <stdio.h>

int main()
{
   int a1[10], a2[100], i;
   errno_t err;

   // Populate a2 with squares of integers
   for (i = 0; i < 100; i++)
   {
      a2[i] = i*i;
   }

   // Tell memcpy_s to copy 10 ints (40 bytes), giving
   // the size of the a1 array (also 40 bytes).
   err = memcpy_s(a1, sizeof(a1), a2, 10 * sizeof (int) );
   if (err)
   {
      printf("Error executing memcpy_s.\n");
   }
   else
   {
     for (i = 0; i < 10; i++)
       printf("%d ", a1[i]);
   }
   printf("\n");
}
```

```Output
0 1 4 9 16 25 36 49 64 81
```

## <a name="see-also"></a>Consulte também

[Manipulação de buffer](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
