---
title: _CrtIsValidHeapPointer
ms.date: 11/04/2016
apiname:
- _CrtIsValidHeapPointer
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
apitype: DLLExport
f1_keywords:
- CrtlsValidHeapPointer
- _CrtIsValidHeapPointer
helpviewer_keywords:
- _CrtIsValidHeapPointer function
- CrtIsValidHeapPointer function
ms.assetid: caf597ce-1b05-4764-9f37-0197a982bec5
ms.openlocfilehash: cdfb02c622cddc4c86a99f614e469abc527d8845
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339384"
---
# <a name="crtisvalidheappointer"></a>_CrtIsValidHeapPointer

Verifica se um ponteiro especificado está em um heap alocado por alguma biblioteca em tempo de execução C, mas não necessariamente pela biblioteca CRT do chamador. Em versões do CRT anteriores ao Visual Studio 2010, isso verifica se o ponteiro especificado está no heap local (somente versão de depuração).

## <a name="syntax"></a>Sintaxe

```C
int _CrtIsValidHeapPointer(
   const void *userData
);
```

### <a name="parameters"></a>Parâmetros

*userData*<br/>
Ponteiro para o início de um bloco de memória alocado.

## <a name="return-value"></a>Valor de retorno

**Crtisvalidheappointer** retornará TRUE se o ponteiro especificado está no heap compartilhado por todas as instâncias da biblioteca CRT. Em versões do CRT anteriores ao Visual Studio 2010, isso retornará TRUE se o ponteiro especificado estiver no heap local. Caso contrário, a função retorna FALSE.

## <a name="remarks"></a>Comentários

Não recomendamos o uso dessa função. A partir da biblioteca CRT no Visual Studio 2010, todas as bibliotecas CRT compartilham um heap do sistema operacional, o *heap de processo*. O **crtisvalidheappointer** função informa se o ponteiro foi alocado em um heap CRT, mas não que ele foi alocado pela biblioteca CRT do chamador. Por exemplo, considere um bloco alocado usando a versão do Visual Studio 2010 da biblioteca CRT. Se o **crtisvalidheappointer** função exportada pela versão do Visual Studio 2012 da biblioteca CRT testa o ponteiro, ela retornará TRUE. Esse não é mais um teste útil. Nas versões da biblioteca CRT anteriores ao Visual Studio 2010, a função é usada para garantir que um endereço de memória específico está no heap local. O heap local refere-se ao heap criado e gerenciado por uma instância específica da biblioteca em tempo de execução C. Se uma DLL (biblioteca de vínculo dinâmico) contiver um link estático para a biblioteca em tempo de execução, ela terá sua própria instância do heap em tempo de execução e, portanto, seu próprio heap, independente do heap local do aplicativo. Quando [Debug](../../c-runtime-library/debug.md) não está definido, as chamadas a **crtisvalidheappointer** são removidas durante o pré-processamento.

Como essa função retorna TRUE ou FALSE, ela pode ser passada para uma das macros [_ASSERT](assert-asserte-assert-expr-macros.md) para criar um mecanismo simples de tratamento de erro de depuração. O seguinte exemplo causa uma falha de asserção se o endereço especificado não está localizado no heap local:

```C
_ASSERTE( _CrtIsValidHeapPointer( userData ) );
```

Para obter mais informações sobre como **crtisvalidheappointer** pode ser usado com outras macros e funções de depuração, consulte [Macros para relatórios](/visualstudio/debugger/macros-for-reporting). Para obter informações sobre como os blocos de memória são alocados, inicializados e gerenciados na versão de depuração do heap de base, consulte [Detalhes do heap de depuração CRT](/visualstudio/debugger/crt-debug-heap-details).

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|**_CrtIsValidHeapPointer**|\<crtdbg.h>|

Para obter mais informações sobre compatibilidade, consulte [Compatibilidade](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Libraries

Somente versões de depuração de [bibliotecas de tempo de execução C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra como testar se a memória é válida quando usada com bibliotecas em tempo de execução C anteriores ao Visual Studio 2010. Esse exemplo é fornecido para usuários do código herdado da biblioteca CRT.

```C
// crt_isvalid.c
// This program allocates a block of memory using _malloc_dbg
// and then tests the validity of this memory by calling
// _CrtIsMemoryBlock,_CrtIsValidPointer, and _CrtIsValidHeapPointer.

#include <stdio.h>
#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

#define  TRUE   1
#define  FALSE  0

int main( void )
{
    char *my_pointer;

    // Call _malloc_dbg to include the filename and line number
    // of our allocation request in the header information
    my_pointer = (char *)_malloc_dbg( sizeof(char) * 10,
        _NORMAL_BLOCK, __FILE__, __LINE__ );

    // Ensure that the memory got allocated correctly
    _CrtIsMemoryBlock((const void *)my_pointer, sizeof(char) * 10,
        NULL, NULL, NULL );

    // Test for read/write accessibility
    if (_CrtIsValidPointer((const void *)my_pointer,
        sizeof(char) * 10, TRUE))
        printf("my_pointer has read and write accessibility.\n");
    else
        printf("my_pointer only has read access.\n");

    // Make sure my_pointer is within the local heap
    if (_CrtIsValidHeapPointer((const void *)my_pointer))
        printf("my_pointer is within the local heap.\n");
    else
        printf("my_pointer is not located within the local"
               " heap.\n");

    free(my_pointer);
}
```

```Output
my_pointer has read and write accessibility.
my_pointer is within the local heap.
```

## <a name="see-also"></a>Consulte também

[Rotinas de depuração](../../c-runtime-library/debug-routines.md)<br/>
