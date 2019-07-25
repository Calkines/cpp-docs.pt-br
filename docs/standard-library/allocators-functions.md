---
title: Macros &lt;allocators&gt;
ms.date: 11/04/2016
f1_keywords:
- allocators/std::ALLOCATOR_DECL
- allocators/std::CACHE_CHUNKLIST
- allocators/std::CACHE_FREELIST
- allocators/std::CACHE_SUBALLOC
- allocators/std::SYNC_DEFAULT
ms.assetid: 9cb5ee07-1ff9-4594-ae32-3c8c6efb511a
helpviewer_keywords:
- std::ALLOCATOR_DECL [C++]
- std::CACHE_CHUNKLIST [C++]
- std::CACHE_FREELIST [C++]
- std::CACHE_SUBALLOC [C++]
- std::SYNC_DEFAULT [C++]
ms.openlocfilehash: 10cd1d51c2cd6053dcbaa0f5bf1548f80ed01659
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448235"
---
# <a name="ltallocatorsgt-macros"></a>Macros &lt;allocators&gt;

||||
|-|-|-|
|[ALLOCATOR_DECL](#allocator_decl)|[CACHE_CHUNKLIST](#cache_chunklist)|[CACHE_FREELIST](#cache_freelist)|
|[CACHE_SUBALLOC](#cache_suballoc)|[SYNC_DEFAULT](#sync_default)|

## <a name="allocator_decl"></a>  ALLOCATOR_DECL

Produz uma classe de modelo allocator.

```cpp
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```

### <a name="remarks"></a>Comentários

A macro produz uma definição de modelo `template <class Type> class name {.....}` e uma especialização `template <> class name<void> {.....}` que, em conjunto, definem uma classe de modelo allocator que usa o filtro de sincronização `sync` e um cache do tipo `cache`.

Para os compiladores que podem compilar reassociação, a definição de modelo resultante tem esta aparência:

```cpp
struct rebind
   {    /* convert a name<Type> to a name<Other> */
   typedef name<Other> other;
   };
```

Para compiladores que não podem compilar reassociação, a definição de modelo resultante tem esta aparência:

```cpp
template <class Type<class name
    : public stdext::allocators::allocator_base<Type,
    sync<stdext::allocators::rts_alloc<cache>>>
{
public:
    name() {}
    template <class Other>
    name(const name<Other>&) {}
    template <class Other>
    name& operator= (const name<Other>&)
    {
        return *this;
    }
};
```

## <a name="cache_chunklist"></a>  CACHE_CHUNKLIST

Produz `stdext::allocators::cache_chunklist<sizeof(Type)>`.

```cpp
#define CACHE_CHUNKLIST <cache_class>
```

### <a name="remarks"></a>Comentários

## <a name="cache_freelist"></a>  CACHE_FREELIST

Produz `stdext::allocators::cache_freelist<sizeof(Type), max>`.

```cpp
#define CACHE_FREELIST(max) <cache_class>
```

### <a name="remarks"></a>Comentários

## <a name="cache_suballoc"></a>  CACHE_SUBALLOC

Produz `stdext::allocators::cache_suballoc<sizeof(Type)>`.

```cpp
#define CACHE_SUBALLOC <cache_class>
```

### <a name="remarks"></a>Comentários

## <a name="sync_default"></a>  SYNC_DEFAULT

Produz um filtro de sincronização.

```cpp
#define SYNC_DEFAULT <sync_template>
```

### <a name="remarks"></a>Comentários

Se um compilador der suporte à compilação de aplicativos de single-threaded e multi-threaded, para aplicativos de single-threaded, a macro produzirá `stdext::allocators::sync_none`, em todos os outros casos, ela produzirá `stdext::allocators::sync_shared`.

## <a name="see-also"></a>Consulte também

[\<allocators>](../standard-library/allocators-header.md)
