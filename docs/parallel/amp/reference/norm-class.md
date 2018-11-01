---
title: Classe norm
ms.date: 11/04/2016
f1_keywords:
- norm
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
ms.openlocfilehash: 2d37dcb430be9941444a90ac0a4ba34f3ee30515
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630757"
---
# <a name="norm-class"></a>Classe norm

Representa um número de norma. Cada elemento é flutuante número de ponto no intervalo de [-1.0f, 1.0f].

## <a name="syntax"></a>Sintaxe

```
class norm;
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|[NORM construtor](#ctor)|Sobrecarregado. Construtor padrão. Inicialize a 0.0f.|

### <a name="public-operators"></a>Operadores públicos

|Nome|Descrição|
|----------|-----------------|
|NORM::Operator-||
|norm::operator--||
|NORM::operator float|Operador de conversão. Converter o número de norma para flutuante valor de ponto.|
|NORM::Operator * =||
|NORM::Operator =||
|NORM::Operator + +||
|+ NORM::Operator =||
|norm::operator=||
|norm::operator-=||

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`norm`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** amp_short_vectors. h

**Namespace:** Concurrency:: Graphics

##  <a name="ctor"></a> NORM

Construtor padrão. Inicialize a 0.0f.

```
norm(
    void) restrict(amp,
    cpu);

explicit norm(
    float _V) restrict(amp,
    cpu);

explicit norm(
    unsigned int _V) restrict(amp,
    cpu);

explicit norm(
    int _V) restrict(amp,
    cpu);

explicit norm(
    double _V) restrict(amp,
    cpu);

norm(
    const norm& _Other) restrict(amp,
    cpu);

norm(
    const unorm& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>Parâmetros

*_V*<br/>
O valor usado para inicializar.

*Outro*<br/>
O objeto usado para inicializar.

## <a name="see-also"></a>Consulte também

[Namespace Concurrency::graphics](concurrency-graphics-namespace.md)
