---
title: _heapchk
ms.date: 11/04/2016
api_name:
- _heapchk
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _heapchk
- heapchk
helpviewer_keywords:
- debugging [CRT], heap-related problems
- consistency checking of heaps
- heapchk function
- heaps, checking consistency
- _heapchk function
ms.assetid: 859619a5-1e35-4f02-9e09-11d9fa266ec0
ms.openlocfilehash: 857feb66d89d5dc406042478156483ecb86a2474
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954817"
---
# <a name="_heapchk"></a>_heapchk

Executa verificações de consistência no heap.

## <a name="syntax"></a>Sintaxe

```C
int _heapchk( void );
```

## <a name="return-value"></a>Valor de retorno

**_heapchk** retorna uma das seguintes constantes de manifesto de inteiro definidas em malloc. h.

|Valor retornado|Condição|
|-|-|
| **_HEAPBADBEGIN** | As informações de cabeçalho iniciais são inválidas ou não foram encontradas. |
| **_HEAPBADNODE** | Um nó inválido foi encontrado ou o heap está danificado. |
| **_HEAPBADPTR** | O ponteiro para o heap não é válido. |
| **_HEAPEMPTY** | O heap não foi inicializado. |
| **_HEAPOK** | O heap parece ser consistente. |

Além disso, se ocorrer um erro, **_heapchk** definirá **errno** como **ENOSYS**.

## <a name="remarks"></a>Comentários

A função **_heapchk** ajuda a depurar problemas relacionados a heap verificando a consistência mínima do heap. Se o sistema operacional não oferecer suporte a **_heapchk**(por exemplo, Windows 98), a função retornará **_HEAPOK** e definirá **errno** como **ENOSYS**.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|Cabeçalho opcional|
|-------------|---------------------|---------------------|
|**_heapchk**|\<malloc.h>|\<errno.h>|

Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_heapchk.c
// This program checks the heap for
// consistency and prints an appropriate message.

#include <malloc.h>
#include <stdio.h>

int main( void )
{
   int  heapstatus;
   char *buffer;

   // Allocate and deallocate some memory
   if( (buffer = (char *)malloc( 100 )) != NULL )
      free( buffer );

   // Check heap status
   heapstatus = _heapchk();
   switch( heapstatus )
   {
   case _HEAPOK:
      printf(" OK - heap is fine\n" );
      break;
   case _HEAPEMPTY:
      printf(" OK - heap is empty\n" );
      break;
   case _HEAPBADBEGIN:
      printf( "ERROR - bad start of heap\n" );
      break;
   case _HEAPBADNODE:
      printf( "ERROR - bad node in heap\n" );
      break;
   }
}
```

```Output
OK - heap is fine
```

## <a name="see-also"></a>Consulte também

[Alocação de Memória](../../c-runtime-library/memory-allocation.md)<br/>
[_heapadd](../../c-runtime-library/heapadd.md)<br/>
[_heapmin](heapmin.md)<br/>
[_heapset](../../c-runtime-library/heapset.md)<br/>
[_heapwalk](heapwalk.md)<br/>
