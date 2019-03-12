---
title: _heapadd
ms.date: 11/04/2016
apiname:
- _heapadd
apilocation:
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr80.dll
- msvcrt.dll
- msvcr110.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- heapadd
- _heapadd
helpviewer_keywords:
- _heapadd function
- memory, adding to heaps
- heaps, adding memory
- heapadd function
ms.assetid: 4d691fe2-2763-49f4-afb1-62738b7cd3ff
ms.openlocfilehash: 8cfd2a5a112a7a5b578f7b6dfcdcc3998596bc86
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738502"
---
# <a name="heapadd"></a>_heapadd

Adiciona memória ao heap.

> [!IMPORTANT]
>  Essa função é obsoleta. A partir do Visual Studio 2015, ela não está disponível no CRT.

## <a name="syntax"></a>Sintaxe

```
int _heapadd(
   void *memblock,
   size_t size
);
```

#### <a name="parameters"></a>Parâmetros

*memblock*<br/>
Ponteiro para a memória de heap.

*size*<br/>
Tamanho da memória a ser adicionada, em bytes.

## <a name="return-value"></a>Valor de retorno

Se for bem-sucedido, `_heapadd` retornará 0. Caso contrário, a função retornará -1 e definirá `errno` como `ENOSYS`.

Para obter mais informações sobre este e outros códigos retornados, consulte [_doserrno, errno, _sys_errlist e _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentários

Começando com o Visual C++ versão 4.0, a estrutura de heap subjacente foi movida para as bibliotecas de tempo de execução de C para dar suporte a novos recursos de depuração. Como resultado, `_heapadd` não tem mais suporte em nenhuma plataforma baseada na API do Win32.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|Cabeçalho opcional|
|-------------|---------------------|---------------------|
|`_heapadd`|\<malloc.h>|\<errno.h>|

Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../c-runtime-library/compatibility.md) na Introdução.

## <a name="see-also"></a>Consulte também

[Alocação de Memória](../c-runtime-library/memory-allocation.md)<br/>
[free](../c-runtime-library/reference/free.md)<br/>
[_heapchk](../c-runtime-library/reference/heapchk.md)<br/>
[_heapmin](../c-runtime-library/reference/heapmin.md)<br/>
[_heapset](../c-runtime-library/heapset.md)<br/>
[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[malloc](../c-runtime-library/reference/malloc.md)<br/>
[realloc](../c-runtime-library/reference/realloc.md)
