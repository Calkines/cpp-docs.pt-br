---
title: Classe float_2
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::float_2::yx
- amp_short_vectors/Concurrency::graphics::float_2::operator-=
- amp_short_vectors/Concurrency::graphics::float_2::operator++
- amp_short_vectors/Concurrency::graphics::float_2::operator-
- amp_short_vectors/Concurrency::graphics::float_2::r
- amp_short_vectors/Concurrency::graphics::float_2::get_yx
- amp_short_vectors/Concurrency::graphics::float_2::get_xy
- amp_short_vectors/Concurrency::graphics::float_2::operator/=
- amp_short_vectors/Concurrency::graphics::float_2::set_yx
- amp_short_vectors/Concurrency::graphics::float_2::x
- amp_short_vectors/Concurrency::graphics::float_2::get_y
- amp_short_vectors/Concurrency::graphics::float_2::operator+=
- amp_short_vectors/Concurrency::graphics::float_2::gr
- amp_short_vectors/Concurrency::graphics::float_2::operator=
- amp_short_vectors/Concurrency::graphics::float_2::set_x
- amp_short_vectors/Concurrency::graphics::float_2::operator--
- amp_short_vectors/Concurrency::graphics::float_2::get_x
- amp_short_vectors/Concurrency::graphics::float_2::operator*=
- amp_short_vectors/Concurrency::graphics::float_2::rg
- amp_short_vectors/Concurrency::graphics::float_2::set_xy
- amp_short_vectors/Concurrency::graphics::float_2::xy
- amp_short_vectors/Concurrency::graphics::float_2
- amp_short_vectors/Concurrency::graphics::float_2::set_y
- amp_short_vectors/Concurrency::graphics::float_2::y
- amp_short_vectors/Concurrency::graphics::float_2::g
ms.assetid: b3ebd48e-f8c8-4f00-a640-357f702f0cae
ms.openlocfilehash: 94a0936c1e5630ae53af9d9386d3c9248061ed71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180265"
---
# <a name="float2-class"></a>Classe float_2

Representa um vetor curto de dois floats.

## <a name="syntax"></a>Sintaxe

```
class float_2;
```

## <a name="members"></a>Membros

### <a name="public-typedefs"></a>Typedefs públicos

|Nome|Descrição|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[Construtor float_2](#ctor)|Sobrecarregado. Padrão construtor, inicializa todos os elementos com 0.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|float_2::get_x||
|float_2::get_xy||
|float_2::get_y||
|float_2::get_yx||
|float_2::ref_g||
|float_2::ref_r||
|float_2::ref_x||
|float_2::ref_y||
|float_2::set_x||
|float_2::set_xy||
|float_2::set_y||
|float_2::set_yx||

### <a name="public-operators"></a>Operadores públicos

|Nome|Descrição|
|----------|-----------------|
|float_2::operator-||
|float_2::operator--||
|float_2::operator*=||
|float_2::operator/=||
|float_2::operator++||
|float_2::operator+=||
|float_2::operator=||
|float_2::operator-=||

### <a name="public-constants"></a>Constantes públicas

|Nome|Descrição|
|----------|-----------------|
|[tamanho constante](#float_2__size)||

### <a name="public-data-members"></a>Membros de Dados Públicos

|Nome|Descrição|
|----------|-----------------|
|float_2::g||
|float_2::gr||
|float_2::r||
|float_2::rg||
|float_2::x||
|float_2::xy||
|float_2::y||
|float_2::yx||

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`float_2`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** amp_short_vectors. h

**Namespace:** Concurrency:: Graphics

##  <a name="ctor"></a> float_2

Padrão construtor, inicializa todos os elementos com 0.

```
float_2() restrict(amp,
    cpu);

float_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

float_2(
    float _V) restrict(amp,
    cpu);

float_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const double_2& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Parâmetros

*_V0*<br/>
O valor para inicializar o elemento 0.

*_V1*<br/>
O valor para inicializar o elemento 1.

*_V*<br/>
O valor para a inicialização.

*_Other*<br/>
O objeto usado para inicializar.

##  <a name="float_2__size"></a> size

```
static const int size = 2;
```

## <a name="see-also"></a>Consulte também

[Namespace Concurrency::graphics](concurrency-graphics-namespace.md)
