---
title: Funções &lt;chrono&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- chrono/std::duration_cast
- chrono/std::time_point_cast
ms.assetid: d6800e15-77a1-4df3-900e-d8b2fee190c7
ms.openlocfilehash: fc0af2eeb2e3207537fa6edf056aa7382198a5d8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053754"
---
# <a name="ltchronogt-functions"></a>Funções &lt;chrono&gt;

||||
|-|-|-|
|[duration_cast](#duration_cast)|[time_point_cast](#time_point_cast)|

## <a name="duration_cast"></a>  duration_cast

Converte um objeto `duration` em um tipo especificado.

```cpp
template <class To, class Rep, class Period>
constexpr To duration_cast(const duration<Rep, Period>& Dur);
```

### <a name="return-value"></a>Valor de retorno

Um objeto `duration` do tipo `To` que representa o intervalo de tempo `Dur`, que será truncado se precisar caber no tipo de destino.

### <a name="remarks"></a>Comentários

Se `To` for uma instanciação de `duration`, essa função não participará na resolução de sobrecarga.

## <a name="time_point_cast"></a>  time_point_cast

Converte um objeto [time_point](../standard-library/time-point-class.md) para um tipo especificado.

```cpp
template <class To, class Clock, class Duration>
time_point<Clock, To> time_point_cast(const time_point<Clock, Duration>& Tp);
```

### <a name="return-value"></a>Valor de retorno

Um objeto `time_point` que tem uma duração do tipo `To`.

### <a name="remarks"></a>Comentários

A menos que `To` seja uma instanciação de [duração](../standard-library/duration-class.md), essa função não participará da resolução de sobrecarga.

## <a name="see-also"></a>Consulte também

[\<chrono>](../standard-library/chrono.md)<br/>
