---
title: Classe CBitmapRenderTarget
ms.date: 11/04/2016
f1_keywords:
- CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::Attach
- AFXRENDERTARGET/CBitmapRenderTarget::Detach
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmap
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::m_pBitmapRenderTarget
helpviewer_keywords:
- CBitmapRenderTarget [MFC], CBitmapRenderTarget
- CBitmapRenderTarget [MFC], Attach
- CBitmapRenderTarget [MFC], Detach
- CBitmapRenderTarget [MFC], GetBitmap
- CBitmapRenderTarget [MFC], GetBitmapRenderTarget
- CBitmapRenderTarget [MFC], m_pBitmapRenderTarget
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
ms.openlocfilehash: 8c110ec8f7c232180bf054e8e4ba90a18f1902c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388430"
---
# <a name="cbitmaprendertarget-class"></a>Classe CBitmapRenderTarget

Um wrapper para ID2D1BitmapRenderTarget.

## <a name="syntax"></a>Sintaxe

```
class CBitmapRenderTarget : public CRenderTarget;
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[CBitmapRenderTarget::CBitmapRenderTarget](#cbitmaprendertarget)|Constrói um objeto CBitmapRenderTarget.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CBitmapRenderTarget::Attach](#attach)|Anexa existente renderizar a interface para o objeto de destino|
|[CBitmapRenderTarget::Detach](#detach)|Desanexa a interface de destino de renderização do objeto|
|[CBitmapRenderTarget::GetBitmap](#getbitmap)|Recupera o bitmap para este destino de renderização. O bitmap retornado pode ser usado para operações de desenho.|
|[CBitmapRenderTarget::GetBitmapRenderTarget](#getbitmaprendertarget)|Returns ID2D1BitmapRenderTarget interface|

### <a name="public-operators"></a>Operadores públicos

|Nome|Descrição|
|----------|-----------------|
|[CBitmapRenderTarget::operator ID2D1BitmapRenderTarget*](#operator_id2d1bitmaprendertarget_star)|Returns ID2D1BitmapRenderTarget interface|

### <a name="protected-data-members"></a>Membros de dados protegidos

|Nome|Descrição|
|----------|-----------------|
|[CBitmapRenderTarget::m_pBitmapRenderTarget](#m_pbitmaprendertarget)|Um ponteiro para um objeto ID2D1BitmapRenderTarget.|

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

`CBitmapRenderTarget`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxrendertarget.h

##  <a name="attach"></a>  CBitmapRenderTarget::Attach

Anexa existente renderizar a interface para o objeto de destino

```
void Attach(ID2D1BitmapRenderTarget* pTarget);
```

### <a name="parameters"></a>Parâmetros

*pTarget*<br/>
Adaptador de destino de renderização existente. Não pode ser NULL

##  <a name="cbitmaprendertarget"></a>  CBitmapRenderTarget::CBitmapRenderTarget

Constrói um objeto CBitmapRenderTarget.

```
CBitmapRenderTarget();
```

##  <a name="detach"></a>  CBitmapRenderTarget::Detach

Desanexa a interface de destino de renderização do objeto

```
ID2D1BitmapRenderTarget* Detach();
```

### <a name="return-value"></a>Valor de retorno

Ponteiro para desanexado renderizar a interface de destino.

##  <a name="getbitmap"></a>  CBitmapRenderTarget::GetBitmap

Recupera o bitmap para este destino de renderização. O bitmap retornado pode ser usado para operações de desenho.

```
BOOL GetBitmap(CD2DBitmap& bitmap);
```

### <a name="parameters"></a>Parâmetros

*bitmap*<br/>
Quando este método retorna, contém o bitmap válido para este destino de renderização. Esse bitmap pode ser usado para operações de desenho.

### <a name="return-value"></a>Valor de retorno

Se o método for bem-sucedido, ele retornará TRUE. Caso contrário, retornará FALSE.

##  <a name="getbitmaprendertarget"></a>  CBitmapRenderTarget::GetBitmapRenderTarget

Returns ID2D1BitmapRenderTarget interface

```
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```

### <a name="return-value"></a>Valor de retorno

Ponteiro para uma interface ID2D1BitmapRenderTarget ou NULL se o objeto ainda não foi inicializado.

##  <a name="m_pbitmaprendertarget"></a>  CBitmapRenderTarget::m_pBitmapRenderTarget

Um ponteiro para um objeto ID2D1BitmapRenderTarget.

```
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;
```

##  <a name="operator_id2d1bitmaprendertarget_star"></a>  CBitmapRenderTarget::operator ID2D1BitmapRenderTarget*

Returns ID2D1BitmapRenderTarget interface

```
operator ID2D1BitmapRenderTarget*();
```

### <a name="return-value"></a>Valor de retorno

Ponteiro para uma interface ID2D1BitmapRenderTarget ou NULL se o objeto ainda não foi inicializado.

## <a name="see-also"></a>Consulte também

[Classes](../../mfc/reference/mfc-classes.md)
