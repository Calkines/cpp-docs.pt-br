---
title: Funções (OpenMP)
ms.date: 03/20/2019
f1_keywords:
- OpenMP functions
- omp_destroy_lock
- omp_destroy_nest_lock
- omp_get_dynamic
- omp_get_max_threads
- omp_get_nested
- omp_get_num_procs
- omp_get_num_threads
- omp_get_thread_num
- omp_get_wtick
- omp_get_wtime
- omp_in_parallel
- omp_init_lock
- omp_init_nest_lock
- omp_set_dynamic
- omp_set_lock
- omp_set_nest_lock
- omp_set_nested
- omp_set_num_threads
- omp_test_lock
- omp_test_nest_lock
- omp_unset_lock
- omp_unset_nest_lock
helpviewer_keywords:
- OpenMP functions
- omp_destroy_lock OpenMP function
- omp_destroy_nest_lock OpenMP function
- omp_get_dynamic OpenMP function
- omp_get_max_threads OpenMP function
- omp_get_nested OpenMP function
- omp_get_num_procs OpenMP function
- omp_get_num_threads OpenMP function
- omp_get_thread_num OpenMP function
- omp_get_wtick OpenMP function
- omp_get_wtime OpenMP function
- omp_in_parallel OpenMP function
- omp_init_lock OpenMP function
- omp_init_nest_lock OpenMP function
- omp_set_dynamic OpenMP function
- omp_set_lock OpenMP function
- omp_set_nest_lock OpenMP function
- omp_set_nested OpenMP function
- omp_set_num_threads OpenMP function
- omp_test_lock OpenMP function
- omp_test_nest_lock OpenMP function
- omp_unset_lock OpenMP function
- omp_unset_nest_lock OpenMP function
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
ms.openlocfilehash: 1bf0e08f3b28368d9aea5438b3036ac8a0283735
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363083"
---
# <a name="openmp-functions"></a>Funções (OpenMP)

Fornece links para as funções usadas na API OpenMP.

O Visual C++ implementação do padrão OpenMP inclui os seguintes tipos de dados e funções.

Para a execução do ambiente:

|Função|Descrição|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|Define o número de threads em futuro regiões em paralelo, a menos que substituído por um [num_threads](openmp-clauses.md#num-threads) cláusula.|
|[omp_get_num_threads](#omp-get-num-threads)|Retorna o número de threads na região paralela.|
|[omp_get_max_threads](#omp-get-max-threads)|Retorna um inteiro que é igual ou maior que o número de threads que estaria disponível se uma região parallel sem [num_threads](openmp-clauses.md#num-threads) foram definidas nesse ponto no código.|
|[omp_get_thread_num](#omp-get-thread-num)|Retorna o número de threads do thread em execução dentro de sua equipe de thread.|
|[omp_get_num_procs](#omp-get-num-procs)|Retorna o número de processadores que estão disponíveis quando a função é chamada.|
|[omp_in_parallel](#omp-in-parallel)|Retorna diferente de zero se for chamado de dentro de uma região paralela.|
|[omp_set_dynamic](#omp-set-dynamic)|Indica que o número de threads disponíveis no futuro regiões em paralelo pode ser ajustado pelo tempo de execução.|
|[omp_get_dynamic](#omp-get-dynamic)|Retorna um valor que indica se o número de threads disponíveis no futuro regiões em paralelo pode ser ajustado pelo tempo de execução.|
|[omp_set_nested](#omp-set-nested)|Permitir o paralelismo aninhado.|
|[omp_get_nested](#omp-get-nested)|Retorna um valor que indica se o paralelismo aninhado está habilitado.|

Bloqueio:

|Função|Descrição|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|Inicializa um bloqueio simples.|
|[omp_init_nest_lock](#omp-init-nest-lock)|Inicializa um bloqueio.|
|[omp_destroy_lock](#omp-destroy-lock)|Cancela a inicialização de um bloqueio.|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|Cancela a inicialização de um bloqueio empilhável.|
|[omp_set_lock](#omp-set-lock)|Blocos de execução de thread até que um bloqueio esteja disponível.|
|[omp_set_nest_lock](#omp-set-nest-lock)|Blocos de execução de thread até que um bloqueio esteja disponível.|
|[omp_unset_lock](#omp-unset-lock)|Libera um bloqueio.|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|Libera um bloqueio empilhável.|
|[omp_test_lock](#omp-test-lock)|Tenta definir um bloqueio, mas não bloqueia a execução do thread.|
|[omp_test_nest_lock](#omp-test-nest-lock)|Tenta definir um bloqueio empilhável, mas não bloqueia a execução do thread.|

|Tipo de dados|Descrição|
|---------|-----------|
|`omp_lock_t`|Um tipo que contém o status de um bloqueio, se o bloqueio está disponível ou se um thread possui um bloqueio.|
|`omp_nest_lock_t`|Um tipo que contém uma das seguintes partes de informações sobre um bloqueio: se o bloqueio está disponível e a identidade do thread que possui o bloqueio e uma contagem de aninhamento.|

Para rotinas de tempo:

|Função|Descrição|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|Retorna que um valor em segundos do tempo decorrido de algum momento.|
|[omp_get_wtick](#omp-get-wtick)|Retorna o número de segundos entre os tiques do relógio de processador.|

## <a name="omp-destroy-lock"></a>omp_destroy_lock

Cancela a inicialização de um bloqueio.

```
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parâmetros

*lock*<br/>
Uma variável do tipo `omp_lock_t` que foi inicializado com [funções omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Comentários

Para obter mais informações, consulte [3.2.2 funções omp_destroy_lock e omp_destroy_nest_lock funções](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Exemplo

Ver [funções omp_init_lock](#omp-init-lock) para obter um exemplo de como usar `omp_destroy_lock`.

## <a name="omp-destroy-nest-lock"></a>omp_destroy_nest_lock

Cancela a inicialização de um bloqueio empilhável.

```
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parâmetros

*lock*<br/>
Uma variável do tipo `omp_nest_lock_t` que foi inicializado com [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Comentários

Para obter mais informações, consulte [3.2.2 funções omp_destroy_lock e omp_destroy_nest_lock funções](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Exemplo

Ver [omp_init_nest_lock](#omp-init-nest-lock) para obter um exemplo de como usar `omp_destroy_nest_lock`.

## <a name="omp-get-dynamic"></a>omp_get_dynamic

Retorna um valor que indica se o número de threads disponíveis no futuro regiões em paralelo pode ser ajustado pelo tempo de execução.

```
int omp_get_dynamic();
```

### <a name="return-value"></a>Valor retornado

Um valor diferente de zero significa threads serão ajustados dinamicamente.

### <a name="remarks"></a>Comentários

Ajuste dinâmico de segmentos é especificado com [omp_set_dynamic](#omp-set-dynamic) e [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic).

Para obter mais informações, consulte [3.1.7 função omp_set_dynamic](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Exemplo

Ver [omp_set_dynamic](#omp-set-dynamic) para obter um exemplo de como usar `omp_get_dynamic`.

## <a name="omp-get-max-threads"></a>omp_get_max_threads

Retorna um inteiro que é igual ou maior que o número de threads que estaria disponível se uma região parallel sem [num_threads](openmp-clauses.md#num-threads) foram definidas nesse ponto no código.

```
int omp_get_max_threads( )
```

### <a name="remarks"></a>Comentários

Para obter mais informações, consulte [3.1.3 função omp_get_max_threads](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md).

### <a name="example"></a>Exemplo

```cpp
// omp_get_max_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(8);
    printf_s("%d\n", omp_get_max_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));
}
```

```Output
8
8
8
8
8
```

## <a name="omp-get-nested"></a>omp_get_nested

Retorna um valor que indica se o paralelismo aninhado está habilitado.

```
int omp_get_nested( );
```

### <a name="return-value"></a>Valor retornado

Um valor diferente de zero significa que o paralelismo aninhado está habilitado.

### <a name="remarks"></a>Comentários

Paralelismo aninhado é especificado com [omp_set_nested](#omp-set-nested) e [OMP_NESTED](openmp-environment-variables.md#omp-nested).

Para obter mais informações, consulte [3.1.10 função omp_get_nested](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).

### <a name="example"></a>Exemplo

Ver [omp_set_nested](#omp-set-nested) para obter um exemplo de como usar `omp_get_nested`.

## <a name="omp-get-num-procs"></a>omp_get_num_procs

Retorna o número de processadores que estão disponíveis quando a função é chamada.

```
int omp_get_num_procs();
```

### <a name="remarks"></a>Comentários

Para obter mais informações, consulte [3.1.5 função omp_get_num_procs](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md).

### <a name="example"></a>Exemplo

```cpp
// omp_get_num_procs.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    printf_s("%d\n", omp_get_num_procs( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_procs( ));
        }
}
```

```Output
// Expect the following output when the example is run on a two-processor machine:
2
2
```

## <a name="omp-get-num-threads"></a>omp_get_num_threads

Retorna o número de threads na região paralela.

```
int omp_get_num_threads( );
```

### <a name="remarks"></a>Comentários

Para obter mais informações, consulte [3.1.2 função omp_get_num_threads](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md).

### <a name="example"></a>Exemplo

```cpp
// omp_get_num_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_num_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));
}
```

```Output
1
4
1
3
1
```

## <a name="omp-get-thread-num"></a>omp_get_thread_num

Retorna o número de threads do thread em execução dentro de sua equipe de thread.

```
int omp_get_thread_num( );
```

### <a name="remarks"></a>Comentários

Para obter mais informações, consulte [3.1.4 função omp_get_thread_num](../../../parallel/openmp/3-1-4-omp-get-thread-num-function.md).

### <a name="example"></a>Exemplo

Ver [paralelas](openmp-directives.md#parallel) para obter um exemplo de como usar `omp_get_thread_num`.

## <a name="omp-get-wtick"></a>omp_get_wtick

Retorna o número de segundos entre os tiques do relógio de processador.

```
double omp_get_wtick( );
```

### <a name="remarks"></a>Comentários

Para obter mais informações, consulte [3.3.2 função omp_get_wtick](../../../parallel/openmp/3-3-2-omp-get-wtick-function.md).

### <a name="example"></a>Exemplo

Ver [omp_get_wtime](#omp-get-wtime) para obter um exemplo de como usar `omp_get_wtick`.

## <a name="omp-get-wtime"></a>omp_get_wtime

Retorna que um valor em segundos do tempo decorrido de algum momento.

```
double omp_get_wtime( );
```

### <a name="return-value"></a>Valor retornado

Retorna que um valor em segundos do tempo decorrido desde o momento de alguns arbitrário, mas consistente.

### <a name="remarks"></a>Comentários

Esse ponto permanecerão consistente durante a execução do programa, possibilitando comparações futuras.

Para obter mais informações, consulte [3.3.1 função omp_get_wtime](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md).

### <a name="example"></a>Exemplo

```cpp
// omp_get_wtime.cpp
// compile with: /openmp
#include "omp.h"
#include <stdio.h>
#include <windows.h>

int main() {
    double start = omp_get_wtime( );
    Sleep(1000);
    double end = omp_get_wtime( );
    double wtick = omp_get_wtick( );

    printf_s("start = %.16g\nend = %.16g\ndiff = %.16g\n",
             start, end, end - start);

    printf_s("wtick = %.16g\n1/wtick = %.16g\n",
             wtick, 1.0 / wtick);
}
```

```Output
start = 594255.3671159324
end = 594256.3664474116
diff = 0.9993314791936427
wtick = 2.793651148400146e-007
1/wtick = 3579545
```

## <a name="omp-in-parallel"></a>omp_in_parallel

Retorna diferente de zero se for chamado de dentro de uma região paralela.

```
int omp_in_parallel( );
```

### <a name="remarks"></a>Comentários

Para obter mais informações, consulte [3.1.6 função omp_in_parallel](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md).

### <a name="example"></a>Exemplo

```cpp
// omp_in_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_in_parallel( ));

    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_in_parallel( ));
        }
}
```

```Output
0
1
```

## <a name="omp-init-lock"></a>omp_init_lock

Inicializa um bloqueio simples.

```
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parâmetros

*lock*<br/>
Uma variável do tipo `omp_lock_t`.

### <a name="remarks"></a>Comentários

Para obter mais informações, consulte [3.2.1 funções omp_init_lock e omp_init_nest_lock funções](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

### <a name="example"></a>Exemplo

```cpp
// omp_init_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t my_lock;

int main() {
   omp_init_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num( );
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_lock(&my_lock);
         printf_s("Thread %d - starting locked region\n", tid);
         printf_s("Thread %d - ending locked region\n", tid);
         omp_unset_lock(&my_lock);
      }
   }

   omp_destroy_lock(&my_lock);
}
```

```Output
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
```

## <a name="omp-init-nest-lock"></a>omp_init_nest_lock

Inicializa um bloqueio.

```
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parâmetros

*lock*<br/>
Uma variável do tipo `omp_nest_lock_t`.

### <a name="remarks"></a>Comentários

A contagem inicial de aninhamento é zero.

Para obter mais informações, consulte [3.2.1 funções omp_init_lock e omp_init_nest_lock funções](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

### <a name="example"></a>Exemplo

```cpp
// omp_init_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t my_lock;

void Test() {
   int tid = omp_get_thread_num( );
   omp_set_nest_lock(&my_lock);
   printf_s("Thread %d - starting nested locked region\n", tid);
   printf_s("Thread %d - ending nested locked region\n", tid);
   omp_unset_nest_lock(&my_lock);
}

int main() {
   omp_init_nest_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_nest_lock(&my_lock);
            if (i % 3)
               Test();
            omp_unset_nest_lock(&my_lock);
        }
    }

    omp_destroy_nest_lock(&my_lock);
}
```

```Output
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
```

## <a name="omp-set-dynamic"></a>omp_set_dynamic

Indica que o número de threads disponíveis no futuro regiões em paralelo pode ser ajustado pelo tempo de execução.

```
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>Parâmetros

*val*<br/>
Um valor que indica se o número de threads disponíveis no futuro regiões em paralelo pode ser ajustado pelo tempo de execução. Se for diferente de zero, que o tempo de execução pode ajustar o número de threads, se for zero, o tempo de execução não ajustar dinamicamente o número de threads.

### <a name="remarks"></a>Comentários

O número de threads nunca excederá o valor definido por [omp_set_num_threads](#omp-set-num-threads) ou pelo [OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads).

Use [omp_get_dynamic](#omp-get-dynamic) para exibir a configuração atual da `omp_set_dynamic`.

A configuração para `omp_set_dynamic` substituirá a configuração do [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic) variável de ambiente.

Para obter mais informações, consulte [3.1.7 função omp_set_dynamic](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Exemplo

```cpp
// omp_set_dynamic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_dynamic(9);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_dynamic( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_dynamic( ));
        }
}
```

```Output
1
1
```

## <a name="omp-set-lock"></a>omp_set_lock

Blocos de execução de thread até que um bloqueio esteja disponível.

```
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parâmetros

*lock*<br/>
Uma variável do tipo `omp_lock_t` que foi inicializado com [funções omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Comentários

Para obter mais informações, consulte [3.2.3 funções omp_set_lock e omp_set_nest_lock](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Exemplos

Ver [funções omp_init_lock](#omp-init-lock) para obter um exemplo de como usar `omp_set_lock`.

## <a name="omp-set-nest-lock"></a>omp_set_nest_lock

Blocos de execução de thread até que um bloqueio esteja disponível.

```
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parâmetros

*lock*<br/>
Uma variável do tipo `omp_nest_lock_t` que foi inicializado com [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Comentários

Para obter mais informações, consulte [3.2.3 funções omp_set_lock e omp_set_nest_lock](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Exemplos

Ver [omp_init_nest_lock](#omp-init-nest-lock) para obter um exemplo de como usar `omp_set_nest_lock`.

## <a name="omp-set-nested"></a>omp_set_nested

Permitir o paralelismo aninhado.

```
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>Parâmetros

*val*<br/>
Um valor diferente de zero permite que o paralelismo aninhado, enquanto zero desabilita o paralelismo aninhado.

### <a name="remarks"></a>Comentários

OMP aninhado paralelismo pode ser ativado com `omp_set_nested`, ou definindo o [OMP_NESTED](openmp-environment-variables.md#omp-nested) variável de ambiente.

A configuração para `omp_set_nested` substituirá a configuração do `OMP_NESTED` variável de ambiente.

Habilitando a variável de ambiente pode interromper um programa caso contrário, operacional, porque o número de threads aumenta exponencialmente ao aninhar regiões em paralelo. Por exemplo, uma função que é recursivo seis vezes com o número de threads OMP definido como 4 requer 4.096 (4 à potência de 6) threads. Exceto com vinculado à e/S de aplicativos, o desempenho de um aplicativo geralmente degrada se houver mais threads do que processadores.

Use [omp_get_nested](#omp-get-nested) para exibir a configuração atual da `omp_set_nested`.

Para obter mais informações, consulte [3.1.9 função omp_set_nested](../../../parallel/openmp/3-1-9-omp-set-nested-function.md).

### <a name="example"></a>Exemplo

```cpp
// omp_set_nested.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_nested(1);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_nested( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_nested( ));
        }
}
```

```Output
1
1
```

## <a name="omp-set-num-threads"></a>omp_set_num_threads

Define o número de threads em futuro regiões em paralelo, a menos que substituído por um [num_threads](openmp-clauses.md#num-threads) cláusula.

```
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>Parâmetros

*num_threads*<br/>
O número de threads na região paralela.

### <a name="remarks"></a>Comentários

Para obter mais informações, consulte [3.1.1 função omp_set_num_threads](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).

### <a name="example"></a>Exemplo

Ver [omp_get_num_threads](#omp-get-num-threads) para obter um exemplo de como usar `omp_set_num_threads`.

## <a name="omp-test-lock"></a>omp_test_lock

Tenta definir um bloqueio, mas não bloqueia a execução do thread.

```
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parâmetros

*lock*<br/>
Uma variável do tipo `omp_lock_t` que foi inicializado com [funções omp_init_lock](#omp-init-lock).

### <a name="remarks"></a>Comentários

Para obter mais informações, consulte [3.2.5 funções omp_test_lock e omp_test_nest_lock funções](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

### <a name="example"></a>Exemplo

```cpp
// omp_test_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t simple_lock;

int main() {
    omp_init_lock(&simple_lock);

    #pragma omp parallel num_threads(4)
    {
        int tid = omp_get_thread_num();

        while (!omp_test_lock(&simple_lock))
            printf_s("Thread %d - failed to acquire simple_lock\n",
                     tid);

        printf_s("Thread %d - acquired simple_lock\n", tid);

        printf_s("Thread %d - released simple_lock\n", tid);
        omp_unset_lock(&simple_lock);
    }

    omp_destroy_lock(&simple_lock);
}
```

```Output
Thread 1 - acquired simple_lock
Thread 1 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - acquired simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - acquired simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - released simple_lock
Thread 3 - failed to acquire simple_lock
Thread 3 - acquired simple_lock
Thread 3 - released simple_lock
```

## <a name="omp-test-nest-lock"></a>omp_test_nest_lock

Tenta definir um bloqueio empilhável, mas não bloqueia a execução do thread.

```
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parâmetros

*lock*<br/>
Uma variável do tipo `omp_nest_lock_t` que foi inicializado com [omp_init_nest_lock](#omp-init-nest-lock).

### <a name="remarks"></a>Comentários

Para obter mais informações, consulte [3.2.5 funções omp_test_lock e omp_test_nest_lock funções](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

### <a name="example"></a>Exemplo

```cpp
// omp_test_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t nestable_lock;

int main() {
   omp_init_nest_lock(&nestable_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num();
      while (!omp_test_nest_lock(&nestable_lock))
         printf_s("Thread %d - failed to acquire nestable_lock\n",
                tid);

      printf_s("Thread %d - acquired nestable_lock\n", tid);

      if (omp_test_nest_lock(&nestable_lock)) {
         printf_s("Thread %d - acquired nestable_lock again\n",
                tid);
         printf_s("Thread %d - released nestable_lock\n",
                tid);
         omp_unset_nest_lock(&nestable_lock);
      }

      printf_s("Thread %d - released nestable_lock\n", tid);
      omp_unset_nest_lock(&nestable_lock);
   }

   omp_destroy_nest_lock(&nestable_lock);
}
```

```Output
Thread 1 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock again
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - acquired nestable_lock
Thread 2 - acquired nestable_lock again
Thread 2 - released nestable_lock
Thread 2 - released nestable_lock
```

## <a name="omp-unset-lock"></a>omp_unset_lock

Libera um bloqueio.

```
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parâmetros

*lock*<br/>
Uma variável do tipo `omp_lock_t` que foi inicializado com [funções omp_init_lock](#omp-init-lock), possuídas por thread e em execução na função.

### <a name="remarks"></a>Comentários

Para obter mais informações, consulte [3.2.4 funções omp_unset_lock e omp_unset_nest_lock funções](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Exemplo

Ver [funções omp_init_lock](#omp-init-lock) para obter um exemplo de como usar `omp_unset_lock`.

## <a name="omp-unset-nest-lock"></a>omp_unset_nest_lock

Libera um bloqueio empilhável.

```
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parâmetros

*lock*<br/>
Uma variável do tipo `omp_nest_lock_t` que foi inicializado com [omp_init_nest_lock](#omp-init-nest-lock), possuídas por thread e em execução na função.

### <a name="remarks"></a>Comentários

Para obter mais informações, consulte [3.2.4 funções omp_unset_lock e omp_unset_nest_lock funções](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Exemplo

Ver [omp_init_nest_lock](#omp-init-nest-lock) para obter um exemplo de como usar `omp_unset_nest_lock`.
