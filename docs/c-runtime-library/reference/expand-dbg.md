---
title: _expand_dbg
ms.date: 11/04/2016
api_name:
- _expand_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- expand_dbg
- _expand_dbg
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
ms.openlocfilehash: 836b9cffcf0367f248a14469b30c1a355e2bdec2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941585"
---
# <a name="_expand_dbg"></a>_expand_dbg

Redimensiona um bloco especificado de memória no heap pela expansão ou contração do bloco (somente versão de depuração).

## <a name="syntax"></a>Sintaxe

```C
void *_expand_dbg(
   void *userData,
   size_t newSize,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parâmetros

*userData*<br/>
Ponteiro para o bloco de memória alocado anteriormente.

*newSize*<br/>
Solicitou o novo tamanho do bloco (em bytes).

*blockType*<br/>
Tipo solicitado para bloco redimensionado: **_CLIENT_BLOCK** ou **_NORMAL_BLOCK**.

*filename*<br/>
Ponteiro para o nome do arquivo de origem que solicitou a operação de expansão ou **nulo**.

*linenumber*<br/>
Número de linha no arquivo de origem em que a operação de expansão foi solicitada ou **nula**.

Os parâmetros *filename* e *LineNumber* só estão disponíveis quando **_expand_dbg** foi chamado explicitamente ou a constante de pré-processador [_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md) foi definida.

## <a name="return-value"></a>Valor de retorno

Após a conclusão bem-sucedida, **_expand_dbg** retorna um ponteiro para o bloco de memória redimensionado. Como a memória não é movida, o endereço é o mesmo que userData. Se ocorreu um erro ou o bloco não pôde ser expandido para o tamanho solicitado, ele retorna **nulo**. Se ocorrer uma falha, **errno** será com informações do sistema operacional sobre a natureza da falha. Para obter mais informações sobre **errno**, consulte [errno, _doserrno, _sys_errlist e _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentários

A função **_expand_dbg** é uma versão de depuração da função _[Expand](expand.md) . Quando [_DEBUG](../../c-runtime-library/debug.md) não é definido, cada chamada para **_expand_dbg** é reduzida para uma chamada para **_expand**. **_Expand** e **_expand_dbg** redimensionam um bloco de memória no heap base, mas o **_expand_dbg** acomoda vários recursos de depuração: buffers em ambos os lados da parte do usuário do bloco para testar os vazamentos, um parâmetro de tipo de bloco para rastrear tipos de alocação específicos e informações de *nome de arquivo*/*LineNumber* para determinar a origem das solicitações de alocação.

**_expand_dbg** redimensiona o bloco de memória especificado com um pouco mais de espaço do que o *newSize*solicitado. *newSize* pode ser maior ou menor que o tamanho do bloco de memória alocado originalmente. O espaço adicional é usado pelo gerenciador de heaps de depuração para vincular os blocos de memória de depuração e fornecer informações do cabeçalho de depuração ao aplicativo e substituir buffers. O redimensionamento é realizado pela expansão ou contração do bloco de memória original. **_expand_dbg** não move o bloco de memória, assim como a função [_realloc_dbg](realloc-dbg.md) .

Quando *newSize* é maior que o tamanho do bloco original, o bloco de memória é expandido. Durante uma expansão, se o bloco de memória não puder ser expandido para acomodar o tamanho solicitado, **NULL** será retornado. Quando *newSize* é menor que o tamanho do bloco original, o bloco de memória é contratado até que o novo tamanho seja obtido.

Para obter informações sobre como os blocos de memória são alocados, inicializados e gerenciados na versão de depuração do heap de base, consulte [Detalhes do heap de depuração CRT](/visualstudio/debugger/crt-debug-heap-details). Para obter informações sobre os tipos de blocos de alocação e como eles são usados, consulte [Types of blocks on the debug heap](/visualstudio/debugger/crt-debug-heap-details) (Tipos de blocos no heap de depuração). Para obter informações sobre as diferenças entre chamar uma função de heap padrão e sua versão de depuração em um build de depuração de um aplicativo, consulte [Versões de depuração das funções de alocação de heap](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

Essa função valida seus parâmetros. Se *memblock* for um ponteiro nulo ou se o tamanho for maior que **_HEAP_MAXREQ**, essa função invocará um manipulador de parâmetro inválido, conforme descrito em [validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, **errno** será definido como **EINVAL** e a função retornará **NULL**.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**_expand_dbg**|\<crtdbg.h>|

Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Libraries

Somente versões de depuração de [bibliotecas de tempo de execução C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemplo

```C
// crt_expand_dbg.c
//
// This program allocates a block of memory using _malloc_dbg
// and then calls _msize_dbg to display the size of that block.
// Next, it uses _expand_dbg to expand the amount of
// memory used by the buffer and then calls _msize_dbg again to
// display the new amount of memory allocated to the buffer.
//

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>
#include <crtdbg.h>

int main( void )
{
   long *buffer;
   size_t size;

   // Call _malloc_dbg to include the filename and line number
   // of our allocation request in the header
   buffer = (long *)_malloc_dbg( 40 * sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );
   if( buffer == NULL )
      exit( 1 );

   // Get the size of the buffer by calling _msize_dbg
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );

   // Expand the buffer using _expand_dbg and show the new size
   buffer = (long *)_expand_dbg( buffer, size + sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );

   if( buffer == NULL )
      exit( 1 );
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _expand_dbg of 1 more long: %u\n",
           size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after _malloc_dbg of 40 longs: 160
Size of block after _expand_dbg of 1 more long: 164
```

## <a name="comment"></a>Comentário

A saída desse programa depende da capacidade do seu computador de expandir todas as seções. Se todas as seções estiverem expandidas, a saída será refletida na seção de saída.

## <a name="see-also"></a>Consulte também

[Rotinas de depuração](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
