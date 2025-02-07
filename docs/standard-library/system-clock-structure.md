---
title: Estrutura system_clock
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::system_clock
- chrono/std::chrono::system_clock::from_time_t
- chrono/std::chrono::system_clock::now
- chrono/std::chrono::system_clock::to_time_t
- chrono/std::chrono::system_clock::is_monotonic Constant
- chrono/std::chrono::system_clock::is_steady Constant
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
ms.openlocfilehash: 7a9fd83840883de5172df8b2e1e451984a95ea47
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450184"
---
# <a name="systemclock-structure"></a>Estrutura system_clock

Representa um *tipo de relógio* baseado no relógio em tempo real do sistema.

## <a name="syntax"></a>Sintaxe

```cpp
struct system_clock;
```

## <a name="remarks"></a>Comentários

Um *tipo de relógio* é usado para obter a hora atual como UTC. O tipo incorpora uma instanciação de [duration](../standard-library/duration-class.md) e o modelo de classe [time_point](../standard-library/time-point-class.md) e define uma função membro estática `now()` que retorna a hora.

Um relógio será *monotônico* se o valor retornado por uma primeira chamada a `now()` for sempre menor ou igual ao valor retornado por uma chamada posterior a `now()`.

Um relógio será *estável* se ele for *monotônico* e se o tempo entre os tiques do relógio for constante.

## <a name="members"></a>Membros

### <a name="public-typedefs"></a>Typedefs públicos

|Nome|Descrição|
|----------|-----------------|
|`system_clock::duration`|Um sinônimo de `duration<rep, period>`.|
|`system_clock::period`|Um sinônimo do tipo que é usado para representar o período de tiques na instanciação independente de `duration`.|
|`system_clock::rep`|Um sinônimo do tipo que é usado para representar o número de tiques do relógio na instanciação independente de `duration`.|
|`system_clock::time_point`|Um sinônimo de `time_point<Clock, duration>`, em que `Clock` é um sinônimo do próprio tipo de relógio ou de outro tipo de relógio que se baseia na mesma época e que tem o mesmo tipo `duration` aninhado.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[from_time_t](#from_time_t)|Estático. Retorna um `time_point` que mais se aproxima de um tempo especificado.|
|[seguida](#now)|Estático. Retorna a data atual.|
|[to_time_t](#to_time_t)|Estático. Retorna um objeto `time_t` que mais se aproxima de um `time_point` especificado.|

### <a name="public-constants"></a>Constantes públicas

|Nome|Descrição|
|----------|-----------------|
|[Constante system_clock::is_monotonic](#is_monotonic_constant)|Especifica se o tipo de relógio é monotônico.|
|[Constante system_clock::is_steady](#is_steady_constant)|Especifica se o tipo de relógio é estável.|

## <a name="requirements"></a>Requisitos

**Cabeçalho:** \<> Chrono

**Namespace:** std::chrono

## <a name="from_time_t"></a>  system_clock::from_time_t

Método estático que retorna um [time_point](../standard-library/time-point-class.md) que melhor aproxima o tempo representado por *TM*.

```cpp
static time_point from_time_t(time_t Tm) noexcept;
```

### <a name="parameters"></a>Parâmetros

*TM*\
Um objeto [time_t](../c-runtime-library/standard-types.md).

## <a name="is_monotonic_constant"></a>  Constante system_clock::is_monotonic

Valor estático que especifica se o tipo de relógio é monotônico.

```cpp
static const bool is_monotonic = false;
```

### <a name="return-value"></a>Valor de retorno

Nessa implementação, `system_clock::is_monotonic` sempre retorna **false**.

### <a name="remarks"></a>Comentários

Um relógio será *monotônico* se o valor retornado por uma primeira chamada a `now()` for sempre menor ou igual ao valor retornado por uma chamada posterior a `now()`.

## <a name="is_steady_constant"></a>  Constante system_clock::is_steady

Valor estático que especifica se o tipo de relógio é *estável*.

```cpp
static const bool is_steady = false;
```

### <a name="return-value"></a>Valor de retorno

Nessa implementação, `system_clock::is_steady` sempre retorna **false**.

### <a name="remarks"></a>Comentários

Um relógio será *estável* se ele for [monotônico](#is_monotonic_constant) e se o tempo entre os tiques do relógio for constante.

## <a name="now"></a>  system_clock::now

Método estático que retorna a hora atual.

```cpp
static time_point now() noexcept;
```

### <a name="return-value"></a>Valor de retorno

Um objeto [time_point](../standard-library/time-point-class.md) que representa a hora atual.

## <a name="to_time_t"></a>  system_clock::to_time_t

Método estático que retorna um [time_t](../c-runtime-library/standard-types.md) que melhor aproxima o tempo representado por *tempo*.

```cpp
static time_t to_time_t(const time_point& Time) noexcept;
```

### <a name="parameters"></a>Parâmetros

*Momento*\
Um objeto [time_point](../standard-library/time-point-class.md).

## <a name="see-also"></a>Consulte também

[Referência de Arquivos de Cabeçalho](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[Struct steady_clock](../standard-library/steady-clock-struct.md)
