---
title: _expand
ms.date: 11/04/2016
apiname:
- _expand
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
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
ms.openlocfilehash: c1606bedbb1264bddb7674c829fe456f506d6584
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665654"
---
# <a name="expand"></a>_expand

Altera o tamanho de um bloco de memória.

## <a name="syntax"></a>Sintaxe

```C
void *_expand(
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

**expandir** retorna um ponteiro nulo para o bloco de memória realocado. **expand**, ao contrário **realloc**, não é possível mover um bloco para alterar seu tamanho. Portanto, se não houver memória suficiente disponível para expandir o bloco sem movê-lo, o *memblock* parâmetro para **expand** é o mesmo que o valor de retorno.

**expand** retorna **nulo** quando um erro é detectado durante sua operação. Por exemplo, se **expand** é usado para reduzir um bloco de memória, ele pode detectar corrupção de heap de bloco pequeno ou um ponteiro de bloco inválido e retornar **nulo**.

Se houver memória insuficiente disponível para expandir o bloco para determinado tamanho sem movê-lo, a função retorna **nulo**. **expandir** nunca retorna um bloco expandido para um tamanho menor que solicitado. Se ocorrer uma falha, **errno** indica a natureza da falha. Para obter mais informações sobre **errno**, consulte [errno, doserrno, sys_errlist e sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

O valor retornado indica um espaço de armazenamento que sempre está sutilmente alinhado para armazenamento de qualquer tipo de objeto. Para verificar o novo tamanho do item, use **msize**. Para obter um ponteiro para um tipo diferente de **void**, use uma conversão no valor de retorno de tipo.

## <a name="remarks"></a>Comentários

O **expand** função altera o tamanho de um bloco de memória alocado anteriormente ao tentar expandir ou recolher o bloco sem mover seu local no heap. O *memblock* parâmetro aponta para o início do bloco. O *tamanho* parâmetro fornece o novo tamanho do bloco, em bytes. O conteúdo do bloco é inalterado até o menor dos tamanhos novos e antigos. *memblock* não deve ser um bloco que foi liberado.

> [!NOTE]
> Em plataformas de 64 bits **expand** não pode reduzir o bloco se o novo tamanho for menor que o tamanho atual, em particular, se o bloco foi menor que 16K em tamanho e, portanto, alocado no Heap de fragmentação baixo, **expand**  deixará o bloco inalterado e retornará *memblock*.

Quando o aplicativo estiver vinculado a uma versão de depuração das bibliotecas de tempo de execução C, **expand** resolve [expand_dbg](expand-dbg.md). Para obter mais informações sobre como o heap é gerenciado durante o processo de depuração, consulte [The CRT Debug Heap](/visualstudio/debugger/crt-debug-heap-details) (O heap de depuração do CRT).

Essa função valida seus parâmetros. Se *memblock* for um ponteiro nulo, essa função invocará um manipulador de parâmetro inválido, conforme descrito em [validação de parâmetro](../../c-runtime-library/parameter-validation.md). Se a execução puder continuar, **errno** é definido como **EINVAL** e a função retornará **nulo**. Se *tamanho* é maior que **heap_maxreq**, **errno** é definido como **ENOMEM** e a função retornará **NULL**.

## <a name="requirements"></a>Requisitos

|Função|Cabeçalho necessário|
|--------------|---------------------|
|**_expand**|\<malloc.h>|

Para obter informações adicionais sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemplo

```C
// crt_expand.c

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   char *bufchar;
   printf( "Allocate a 512 element buffer\n" );
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )
      exit( 1 );
   printf( "Allocated %d bytes at %Fp\n",
         _msize( bufchar ), (void *)bufchar );
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )
      printf( "Can't expand" );
   else
      printf( "Expanded block to %d bytes at %Fp\n",
            _msize( bufchar ), (void *)bufchar );
   // Free memory
   free( bufchar );
   exit( 0 );
}
```

```Output
Allocate a 512 element buffer
Allocated 512 bytes at 002C12BC
Expanded block to 1024 bytes at 002C12BC
```

## <a name="see-also"></a>Consulte também

[Alocação de Memória](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
