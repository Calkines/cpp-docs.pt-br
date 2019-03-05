---
title: Classe CD2DRadialGradientBrush
ms.date: 11/04/2016
f1_keywords:
- CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::Attach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Create
- AFXRENDERTARGET/CD2DRadialGradientBrush::Destroy
- AFXRENDERTARGET/CD2DRadialGradientBrush::Detach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Get
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_pRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_RadialGradientBrushProperties
helpviewer_keywords:
- CD2DRadialGradientBrush [MFC], CD2DRadialGradientBrush
- CD2DRadialGradientBrush [MFC], Attach
- CD2DRadialGradientBrush [MFC], Create
- CD2DRadialGradientBrush [MFC], Destroy
- CD2DRadialGradientBrush [MFC], Detach
- CD2DRadialGradientBrush [MFC], Get
- CD2DRadialGradientBrush [MFC], GetCenter
- CD2DRadialGradientBrush [MFC], GetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], GetRadiusX
- CD2DRadialGradientBrush [MFC], GetRadiusY
- CD2DRadialGradientBrush [MFC], SetCenter
- CD2DRadialGradientBrush [MFC], SetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], SetRadiusX
- CD2DRadialGradientBrush [MFC], SetRadiusY
- CD2DRadialGradientBrush [MFC], m_pRadialGradientBrush
- CD2DRadialGradientBrush [MFC], m_RadialGradientBrushProperties
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
ms.openlocfilehash: 22029ebcf8cf519571e81e11c84de146c9d54b26
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277268"
---
# <a name="cd2dradialgradientbrush-class"></a>Classe CD2DRadialGradientBrush

Um wrapper para ID2D1RadialGradientBrush.

## <a name="syntax"></a>Sintaxe

```
class CD2DRadialGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](#cd2dradialgradientbrush)|Constrói um objeto CD2DLinearGradientBrush.|
|[CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush](#_dtorcd2dradialgradientbrush)|O destruidor. Chamado quando um objeto de pincel de gradiente radial D2D está sendo destruído.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CD2DRadialGradientBrush::Attach](#attach)|Anexa existente de interface de recurso para o objeto|
|[CD2DRadialGradientBrush::Create](#create)|Cria um CD2DRadialGradientBrush. (Substitui [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DRadialGradientBrush::Destroy](#destroy)|Destrói um objeto CD2DRadialGradientBrush. (Substitui [CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DRadialGradientBrush::Detach](#detach)|Desanexa a interface do recurso do objeto|
|[CD2DRadialGradientBrush::Get](#get)|Interface de ID2D1RadialGradientBrush retorna|
|[CD2DRadialGradientBrush::GetCenter](#getcenter)|Recupera o centro da elipse gradiente|
|[CD2DRadialGradientBrush::GetGradientOriginOffset](#getgradientoriginoffset)|Recupera o deslocamento de origem do gradiente em relação ao centro da elipse gradiente|
|[CD2DRadialGradientBrush::GetRadiusX](#getradiusx)|Recupera o raio x da elipse gradiente|
|[CD2DRadialGradientBrush::GetRadiusY](#getradiusy)|Recupera o raio y da elipse gradiente|
|[CD2DRadialGradientBrush::SetCenter](#setcenter)|Especifica o centro da elipse gradiente no espaço de coordenadas do pincel|
|[CD2DRadialGradientBrush::SetGradientOriginOffset](#setgradientoriginoffset)|Especifica o deslocamento de origem do gradiente em relação ao centro da elipse gradiente|
|[CD2DRadialGradientBrush::SetRadiusX](#setradiusx)|Especifica o raio x da elipse gradiente, no espaço de coordenadas do pincel|
|[CD2DRadialGradientBrush::SetRadiusY](#setradiusy)|Especifica o raio y da elipse gradiente, no espaço de coordenadas do pincel|

### <a name="public-operators"></a>Operadores públicos

|Nome|Descrição|
|----------|-----------------|
|[CD2DRadialGradientBrush::Operator ID2D1RadialGradientBrush *](#operator_id2d1radialgradientbrush_star)|Interface de ID2D1RadialGradientBrush retorna|

### <a name="protected-data-members"></a>Membros de dados protegidos

|Nome|Descrição|
|----------|-----------------|
|[CD2DRadialGradientBrush::m_pRadialGradientBrush](#m_pradialgradientbrush)|Um ponteiro para um ID2D1RadialGradientBrush.|
|[CD2DRadialGradientBrush::m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|O centro, deslocamento de origem de gradiente e raio x e raio y do pincel do gradiente.|

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DRadialGradientBrush`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxrendertarget.h

##  <a name="_dtorcd2dradialgradientbrush"></a>  CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush

O destruidor. Chamado quando um objeto de pincel de gradiente radial D2D está sendo destruído.

```
virtual ~CD2DRadialGradientBrush();
```

##  <a name="attach"></a>  CD2DRadialGradientBrush::Attach

Anexa existente de interface de recurso para o objeto

```
void Attach(ID2D1RadialGradientBrush* pResource);
```

### <a name="parameters"></a>Parâmetros

*pResource*<br/>
Interface de recursos existente. Não pode ser NULL

##  <a name="cd2dradialgradientbrush"></a>  CD2DRadialGradientBrush::CD2DRadialGradientBrush

Constrói um objeto CD2DLinearGradientBrush.

```
CD2DRadialGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES RadialGradientBrushProperties,
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parâmetros

*pParentTarget*<br/>
Um ponteiro para o destino de renderização.

*gradientStops*<br/>
Um ponteiro para uma matriz de estruturas de D2D1_GRADIENT_STOP.

*gradientStopsCount*<br/>
Um valor maior que ou igual a 1 que especifica o número de paradas de gradiente na matriz gradientStops.

*RadialGradientBrushProperties*<br/>
O centro, deslocamento de origem de gradiente e raio x e raio y do pincel do gradiente.

*colorInterpolationGamma*<br/>
O espaço no qual cor interpolação entre as paradas de gradiente é executada.

*extendMode*<br/>
O comportamento do gradiente fora do intervalo [0,1] normalizado.

*pBrushProperties*<br/>
Um ponteiro para a opacidade e a transformação de um pincel.

*bAutoDestroy*<br/>
Indica se o objeto será destruído pelo proprietário (pParentTarget).

##  <a name="create"></a>  CD2DRadialGradientBrush::Create

Cria um CD2DRadialGradientBrush.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parâmetros

*pRenderTarget*<br/>
Um ponteiro para o destino de renderização.

### <a name="return-value"></a>Valor de retorno

Se o método for bem-sucedido, retornará S_OK. Caso contrário, ele retornará um código de erro HRESULT.

##  <a name="destroy"></a>  CD2DRadialGradientBrush::Destroy

Destrói um objeto CD2DRadialGradientBrush.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DRadialGradientBrush::Detach

Desanexa a interface do recurso do objeto

```
ID2D1RadialGradientBrush* Detach();
```

### <a name="return-value"></a>Valor de retorno

Ponteiro para interface de recurso desanexado.

##  <a name="get"></a>  CD2DRadialGradientBrush::Get

Interface de ID2D1RadialGradientBrush retorna

```
ID2D1RadialGradientBrush* Get();
```

### <a name="return-value"></a>Valor de retorno

Ponteiro para uma interface ID2D1RadialGradientBrush ou NULL se o objeto ainda não foi inicializado.

##  <a name="getcenter"></a>  CD2DRadialGradientBrush::GetCenter

Recupera o centro da elipse gradiente

```
CD2DPointF GetCenter() const;
```

### <a name="return-value"></a>Valor de retorno

O centro da elipse gradiente. Esse valor é expresso no espaço de coordenadas do pincel

##  <a name="getgradientoriginoffset"></a>  CD2DRadialGradientBrush::GetGradientOriginOffset

Recupera o deslocamento de origem do gradiente em relação ao centro da elipse gradiente

```
CD2DPointF GetGradientOriginOffset() const;
```

### <a name="return-value"></a>Valor de retorno

O deslocamento da origem do gradiente do centro da elipse gradiente. Esse valor é expresso no espaço de coordenadas do pincel

##  <a name="getradiusx"></a>  CD2DRadialGradientBrush::GetRadiusX

Recupera o raio x da elipse gradiente

```
FLOAT GetRadiusX() const;
```

### <a name="return-value"></a>Valor de retorno

O raio x da elipse gradiente. Esse valor é expresso no espaço de coordenadas do pincel

##  <a name="getradiusy"></a>  CD2DRadialGradientBrush::GetRadiusY

Recupera o raio y da elipse gradiente

```
FLOAT GetRadiusY() const;
```

### <a name="return-value"></a>Valor de retorno

O raio y da elipse gradiente. Esse valor é expresso no espaço de coordenadas do pincel

##  <a name="m_pradialgradientbrush"></a>  CD2DRadialGradientBrush::m_pRadialGradientBrush

Um ponteiro para um ID2D1RadialGradientBrush.

```
ID2D1RadialGradientBrush* m_pRadialGradientBrush;
```

##  <a name="m_radialgradientbrushproperties"></a>  CD2DRadialGradientBrush::m_RadialGradientBrushProperties

O centro, deslocamento de origem de gradiente e raio x e raio y do pincel do gradiente.

```
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;
```

##  <a name="operator_id2d1radialgradientbrush_star"></a>  CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush*

Interface de ID2D1RadialGradientBrush retorna

```
operator ID2D1RadialGradientBrush*();
```

### <a name="return-value"></a>Valor de retorno

Ponteiro para uma interface ID2D1RadialGradientBrush ou NULL se o objeto ainda não foi inicializado.

##  <a name="setcenter"></a>  CD2DRadialGradientBrush::SetCenter

Especifica o centro da elipse gradiente no espaço de coordenadas do pincel

```
void SetCenter(CD2DPointF point);
```

### <a name="parameters"></a>Parâmetros

*point*<br/>
O centro da elipse gradiente, no espaço de coordenadas do pincel

##  <a name="setgradientoriginoffset"></a>  CD2DRadialGradientBrush::SetGradientOriginOffset

Especifica o deslocamento de origem do gradiente em relação ao centro da elipse gradiente

```
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```

### <a name="parameters"></a>Parâmetros

*gradientOriginOffset*<br/>
O deslocamento da origem do gradiente do centro da elipse gradiente

##  <a name="setradiusx"></a>  CD2DRadialGradientBrush::SetRadiusX

Especifica o raio x da elipse gradiente, no espaço de coordenadas do pincel

```
void SetRadiusX(FLOAT radiusX);
```

### <a name="parameters"></a>Parâmetros

*radiusX*<br/>
O raio x da elipse gradiente. Esse valor está no espaço de coordenadas do pincel

##  <a name="setradiusy"></a>  CD2DRadialGradientBrush::SetRadiusY

Especifica o raio y da elipse gradiente, no espaço de coordenadas do pincel

```
void SetRadiusY(FLOAT radiusY);
```

### <a name="parameters"></a>Parâmetros

*radiusY*<br/>
O raio y da elipse gradiente. Esse valor está no espaço de coordenadas do pincel

## <a name="see-also"></a>Consulte também

[Classes](../../mfc/reference/mfc-classes.md)
