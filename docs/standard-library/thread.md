---
title: '&lt;thread&gt;'
ms.date: 11/04/2016
f1_keywords:
- <thread>
ms.assetid: 0c858405-4efb-449d-bf76-70d3693c9234
ms.openlocfilehash: 7053402dfb566f10c7be4c0eebaef40f3d371f43
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460081"
---
# <a name="ltthreadgt"></a>&lt;thread&gt;

Inclua o thread de \<cabeçalho padrão > para definir o **thread** de classe e várias funções de suporte.

## <a name="syntax"></a>Sintaxe

```cpp
#include <thread>
```

## <a name="remarks"></a>Comentários

> [!NOTE]
> No código que é compilado usando **/CLR**, esse cabeçalho é bloqueado.

A `__STDCPP_THREADS__` macro é definida como um valor diferente de zero para indicar que os threads têm suporte neste cabeçalho.

## <a name="members"></a>Membros

### <a name="public-classes"></a>Classes públicas

|Nome|Descrição|
|----------|-----------------|
|[Classe thread](../standard-library/thread-class.md)|Define um objeto que é usado para observar e gerenciar um thread de execução em um aplicativo.|

### <a name="public-structures"></a>Estruturas públicas

|Nome|Descrição|
|----------|-----------------|
|[Estrutura hash (Biblioteca Padrão C++)](../standard-library/hash-structure-stl.md)|Define uma função de membro que retorna um valor que é determinado exclusivamente por um `thread::id`. A função membro define uma função de [hash](../standard-library/hash-class.md) que é adequada para mapear valores `thread::id` do tipo para uma distribuição de valores de índice.|

### <a name="public-functions"></a>Funções públicas

|Nome|Descrição|
|----------|-----------------|
|[get_id](../standard-library/thread-functions.md#get_id)|Identifica exclusivamente o thread atual de execução.|
|[sleep_for](../standard-library/thread-functions.md#sleep_for)|Bloqueia o thread de chamada.|
|[sleep_until](../standard-library/thread-functions.md#sleep_until)|Bloqueia o thread de chamada, pelo menos, até o tempo especificado.|
|[swap](../standard-library/thread-functions.md#swap)|Troca os Estados de dois objetos de **thread** .|
|[yield](../standard-library/thread-functions.md#yield)|Sinaliza ao sistema operacional para executar outros threads, mesmo se o thread atual continuar normalmente em execução.|

### <a name="public-operators"></a>Operadores públicos

|Nome|Descrição|
|----------|-----------------|
|[operador > = operador](../standard-library/thread-operators.md#op_gt_eq)|Determina se um objeto `thread::id` é maior ou igual a outro.|
|[Operador de > de operador](../standard-library/thread-operators.md#op_gt)|Determina se um objeto `thread::id` é maior que outro.|
|[operador < = operador](../standard-library/thread-operators.md#op_lt_eq)|Determina se um objeto `thread::id` é menor ou igual a outro.|
|[Operador de < de operador](../standard-library/thread-operators.md#op_lt)|Determina se um objeto `thread::id` é menor que outro.|
|[operador! = operador](../standard-library/thread-operators.md#op_neq)|Compara dois objetos `thread::id` quanto à desigualdade.|
|[operador = = operador](../standard-library/thread-operators.md#op_eq_eq)|Compara dois objetos `thread::id` quanto à igualdade.|
|[operador de < de < de operador](../standard-library/thread-operators.md#op_lt_lt)|Insere uma representação de texto de um objeto `thread::id` em um fluxo.|

## <a name="see-also"></a>Consulte também

[Referência de Arquivos de Cabeçalho](../standard-library/cpp-standard-library-header-files.md)\
[Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
