---
title: realloc
ms.date: 11/04/2016
apiname:
- realloc
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _brealloc
- _nrealloc
- realloc
- _frealloc
helpviewer_keywords:
- _brealloc function
- realloc function
- nrealloc function
- frealloc function
- _nrealloc function
- memory blocks, reallocating
- memory, reallocating
- _frealloc function
- reallocate memory blocks
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
ms.openlocfilehash: 0d61746365a8ded8d68072b1f398a18ba6ce7605
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357662"
---
# <a name="realloc"></a>realloc

Realocar blocos de memória.

## <a name="syntax"></a>Sintaxe

```C
void *realloc(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>Parâmetros

*memblock*<br/>
Ponteiro para o bloco de memória alocado anteriormente.

*size*<br/>
Novo tamanho em bytes.

## <a name="return-value"></a>Valor de retorno

**realloc** retorna um **void** ponteiro para o bloco de memória realocado (e possivelmente migrado).

Se não houver memória suficiente disponível para expandir o bloco para determinado tamanho, o bloco original será deixada inalterado e **nulo** é retornado.

Se *tamanho* for zero, o bloco apontado por *memblock* é liberado; o valor retornado será **nulo**, e *memblock* é deixado apontando para um bloco liberado.

O valor retornado indica um espaço de armazenamento que sempre está sutilmente alinhado para armazenamento de qualquer tipo de objeto. Para obter um ponteiro para um tipo diferente de **void**, use uma conversão no valor de retorno de tipo.

## <a name="remarks"></a>Comentários

O **realloc** função altera o tamanho de um bloco de memória alocada. O *memblock* argumento aponta para o início do bloco de memória. Se *memblock* é **nulo**, **realloc** se comporta da mesma maneira que **malloc** e aloca um novo bloco de *tamanho*bytes. Se *memblock* não está **nulo**, ele deve ser um ponteiro retornado por uma chamada anterior a **calloc**, **malloc**, ou **realloc** .

O *tamanho* argumento fornece o novo tamanho do bloco, em bytes. O conteúdo do bloco fica inalterado até o menor dos tamanhos novos e antigos, embora o novo bloco possa estar em um local diferente. Como o novo bloco pode estar em um novo local de memória, o ponteiro retornado por **realloc** não tem garantia de ser passado por meio de *memblock* argumento. **realloc** zero não recentemente a memória alocada no caso de crescimento de buffer.

**realloc** define **errno** à **ENOMEM** se a alocação de memória falhar ou se a quantidade de memória solicitada exceder **heap_maxreq**. Para obter informações sobre esse e outros códigos de erro, consulte [errno, _doserrno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

**realloc** chamadas **malloc** para usar o C++ [set_new_mode](set-new-mode.md) função para definir o novo modo do manipulador. O novo modo do manipulador indica se, em caso de falha, **malloc** é chamar a nova rotina do manipulador conforme definido pela [set_new_handler](set-new-handler.md). Por padrão, **malloc** não chama a nova rotina do manipulador em caso de falha ao alocar memória. Você pode substituir esse comportamento padrão para que, quando **realloc** falhar ao alocar memória, **malloc** chame a nova rotina do manipulador da mesma forma que o **novo** operador faz Quando ele falha pelo mesmo motivo. Para substituir o padrão, chame

```C
_set_new_mode(1);
```

no início do seu programa ou vincule com NEWMODE.OBJ (consulte [Opções de vinculação](../../c-runtime-library/link-options.md)).

Quando o aplicativo estiver vinculado a uma versão de depuração das bibliotecas de tempo de execução C, **realloc** resolve [realloc_dbg](realloc-dbg.md). Para obter mais informações sobre como o heap é gerenciado durante o processo de depuração, consulte [The CRT Debug Heap](/visualstudio/debugger/crt-debug-heap-details) (O heap de depuração do CRT).

**realloc** está marcada `__declspec(noalias)` e `__declspec(restrict)`, que significa que a função não é garantido que modifica variáveis globais e que o ponteiro retornado não é um alias. Para obter mais informações, consulte [noalias](../../cpp/noalias.md) e [restrict](../../cpp/restrict.md).

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**realloc**|\<stdlib.h> e \<malloc.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_realloc.c
// This program allocates a block of memory for
// buffer and then uses _msize to display the size of that
// block. Next, it uses realloc to expand the amount of
// memory used by buffer and then calls _msize again to
// display the new amount of memory allocated to buffer.

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   long *buffer, *oldbuffer;
   size_t size;

   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )
      exit( 1 );

   size = _msize( buffer );
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );

   // Reallocate and show new size:
   oldbuffer = buffer;     // save pointer in case realloc fails
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))
        ==  NULL )
   {
      free( oldbuffer );  // free original block
      exit( 1 );
   }
   size = _msize( buffer );
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",
            size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after malloc of 1000 longs: 4000
Size of block after realloc of 1000 more longs: 8000
```

## <a name="see-also"></a>Consulte também

[Alocação de Memória](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
