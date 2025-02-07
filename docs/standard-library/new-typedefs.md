---
title: Typedefs &lt;new&gt;
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 80123bc35422984ef92bdba6da45052d3461b1d7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245145"
---
# <a name="ltnewgt-typedefs"></a>Typedefs &lt;new&gt;

## <a name="hardware_constructive_interference_size"></a> hardware_constructive_interference_size

```cpp
inline constexpr size_t hardware_constructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Comentários

Esse número é o máximo recomendado de tamanho de memória contígua ocupada por dois objetos acessados com a localidade temporal por threads simultâneos. Ele deverá ser pelo menos `alignof(max_align_t)`.

### <a name="example"></a>Exemplo

```cpp
struct together { 
    atomic<int> dog;
    int puppy;
};

struct kennel {
    // Other data members...
    alignas(sizeof(together)) together pack;
    // Other data members...
};

static_assert(sizeof(together) <= hardware_constructive_interference_size);
```

## <a name="hardware_destructive_interference_size"></a> hardware_destructive_interference_size

```cpp
inline constexpr size_t hardware_destructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Comentários

Esse número é o deslocamento recomendado mínimo entre dois objetos acessados simultaneamente para evitar a degradação de desempenho adicionais devido à contenção introduzida pela implementação. Ele deverá ser pelo menos `alignof(max_align_t)`.

### <a name="example"></a>Exemplo

```cpp
struct keep_apart {
    alignas(hardware_destructive_interference_size) atomic<int> cat;
    alignas(hardware_destructive_interference_size) atomic<int> dog;
};
```

## <a name="new_handler"></a> new_handler

O tipo aponta para uma função adequada para uso como um manipulador new.

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>Comentários

Esse tipo de função do manipulador é chamado pelo **operador new** ou `operator new[]` quando eles não podem atender uma solicitação de armazenamento adicional.

### <a name="example"></a>Exemplo

Consulte [set_new_handler](../standard-library/new-functions.md#set_new_handler) para obter um exemplo usando `new_handler` como um valor retornado.
