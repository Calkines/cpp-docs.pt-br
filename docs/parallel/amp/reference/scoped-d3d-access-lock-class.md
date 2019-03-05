---
title: Classe scoped_d3d_access_lock
ms.date: 11/04/2016
f1_keywords:
- scoped_d3d_access_lock
- AMPRT/scoped_d3d_access_lock
- AMPRT/concurrency::direct3d::scoped_d3d_access_lock::scoped_d3d_access_lock
ms.assetid: 0ad333e6-9839-4736-a722-16d95d70c4b1
ms.openlocfilehash: e36c3c2cfa9d1b617e377a7e340f98875457bdf1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272458"
---
# <a name="scopedd3daccesslock-class"></a>Classe scoped_d3d_access_lock

Wrapper de RAII para um bloqueio de acesso de D3D em um objeto accelerator_view.

### <a name="syntax"></a>Sintaxe

```
class scoped_d3d_access_lock;
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|[Construtor scoped_d3d_access_lock](#ctor)|Sobrecarregado. Constrói um objeto `scoped_d3d_access_lock`. O bloqueio é liberado quando esse objeto sai do escopo.|
|[~ scoped_d3d_access_lock destruidor](#dtor)|Libera o bloqueio de acesso de D3D de associado `accelerator_view` objeto.|

### <a name="public-operators"></a>Operadores públicos

|Nome|Descrição|
|----------|-----------------|
|[operator=](#operator_eq)|Utiliza a propriedade de um bloqueio de outro `scoped_d3d_access_lock`.|

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`scoped_d3d_access_lock`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** amprt. h

**Namespace:** concurrency::direct3d

##  <a name="ctor"></a> scoped_d3d_access_lock

Constrói um objeto `scoped_d3d_access_lock`. O bloqueio é liberado quando esse objeto sai do escopo.

```
explicit scoped_d3d_access_lock(// [1] constructor
    accelerator_view& _Av);

explicit scoped_d3d_access_lock(// [2] constructor
    accelerator_view& _Av,
    adopt_d3d_access_lock_t _T);

scoped_d3d_access_lock(// [3] move constructor
    scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>Parâmetros

*_Av*<br/>
O `accelerator_view` para adotar o bloqueio.

*_T*<br/>
O objeto `adopt_d3d_access_lock_t`.

*_Other*<br/>
O `scoped_d3d_access_lock` objeto do qual mover um bloqueio existente.

## <a name="construction"></a>Construção

[1] construtor adquire um bloqueio de acesso de D3D na determinada [accelerator_view](accelerator-view-class.md) objeto. Blocos de construção até o bloqueio é adquirido.

[2] construtor adote um bloqueio de acesso de D3D da determinada [accelerator_view](accelerator-view-class.md) objeto.

[3] construtor de movimento usa um bloqueio de acesso de D3D existente de outro `scoped_d3d_access_lock` objeto. Construção não é bloqueada.

##  <a name="dtor"></a> ~scoped_d3d_access_lock

Libera o bloqueio de acesso de D3D de associado `accelerator_view` objeto.

```
~scoped_d3d_access_lock();
```

## <a name="operator_eq"></a> operator=

Utiliza a propriedade de um bloqueio de acesso de D3D de outro `scoped_d3d_access_lock` objeto, liberando o bloqueio anterior.

```
scoped_d3d_access_lock& operator= (scoped_d3d_access_lock&& _Other);
```

### <a name="parameters"></a>Parâmetros

*_Other*<br/>
O accelerator_view do qual mover o bloqueio de acesso D3D.

### <a name="return-value"></a>Valor de retorno

Uma referência a este `scoped_accelerator_view_lock`.

## <a name="see-also"></a>Consulte também

[Namespace Concurrency::direct3d](concurrency-direct3d-namespace.md)
