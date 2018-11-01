---
title: Classe CD2DBitmap
ms.date: 11/04/2016
f1_keywords:
- CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::CD2DBitmap
- AFXRENDERTARGET/CD2DBitmap::Attach
- AFXRENDERTARGET/CD2DBitmap::CopyFromBitmap
- AFXRENDERTARGET/CD2DBitmap::CopyFromMemory
- AFXRENDERTARGET/CD2DBitmap::CopyFromRenderTarget
- AFXRENDERTARGET/CD2DBitmap::Create
- AFXRENDERTARGET/CD2DBitmap::Destroy
- AFXRENDERTARGET/CD2DBitmap::Detach
- AFXRENDERTARGET/CD2DBitmap::Get
- AFXRENDERTARGET/CD2DBitmap::GetDPI
- AFXRENDERTARGET/CD2DBitmap::GetPixelFormat
- AFXRENDERTARGET/CD2DBitmap::GetPixelSize
- AFXRENDERTARGET/CD2DBitmap::GetSize
- AFXRENDERTARGET/CD2DBitmap::IsValid
- AFXRENDERTARGET/CD2DBitmap::CommonInit
- AFXRENDERTARGET/CD2DBitmap::m_bAutoDestroyHBMP
- AFXRENDERTARGET/CD2DBitmap::m_hBmpSrc
- AFXRENDERTARGET/CD2DBitmap::m_lpszType
- AFXRENDERTARGET/CD2DBitmap::m_pBitmap
- AFXRENDERTARGET/CD2DBitmap::m_sizeDest
- AFXRENDERTARGET/CD2DBitmap::m_strPath
- AFXRENDERTARGET/CD2DBitmap::m_uiResID
helpviewer_keywords:
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], CD2DBitmap
- CD2DBitmap [MFC], Attach
- CD2DBitmap [MFC], CopyFromBitmap
- CD2DBitmap [MFC], CopyFromMemory
- CD2DBitmap [MFC], CopyFromRenderTarget
- CD2DBitmap [MFC], Create
- CD2DBitmap [MFC], Destroy
- CD2DBitmap [MFC], Detach
- CD2DBitmap [MFC], Get
- CD2DBitmap [MFC], GetDPI
- CD2DBitmap [MFC], GetPixelFormat
- CD2DBitmap [MFC], GetPixelSize
- CD2DBitmap [MFC], GetSize
- CD2DBitmap [MFC], IsValid
- CD2DBitmap [MFC], CommonInit
- CD2DBitmap [MFC], m_bAutoDestroyHBMP
- CD2DBitmap [MFC], m_hBmpSrc
- CD2DBitmap [MFC], m_lpszType
- CD2DBitmap [MFC], m_pBitmap
- CD2DBitmap [MFC], m_sizeDest
- CD2DBitmap [MFC], m_strPath
- CD2DBitmap [MFC], m_uiResID
ms.assetid: 2b3686f1-812c-462b-b449-9f0cb6949bf6
ms.openlocfilehash: 869d8c9cffae1a257de04cf82446025be33ef7de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605862"
---
# <a name="cd2dbitmap-class"></a>Classe CD2DBitmap

Um wrapper para ID2D1Bitmap.

## <a name="syntax"></a>Sintaxe

```
class CD2DBitmap : public CD2DResource;
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Sobrecarregado. Constrói um objeto CD2DBitmap HBITMAP.|
|[CD2DBitmap:: ~ CD2DBitmap](#_dtorcd2dbitmap)|O destruidor. Chamado quando um objeto de bitmap D2D está sendo destruído.|

### <a name="protected-constructors"></a>Construtores Protegidos

|Nome|Descrição|
|----------|-----------------|
|[CD2DBitmap::CD2DBitmap](#cd2dbitmap)|Sobrecarregado. Constrói um objeto CD2DBitmap.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CD2DBitmap::Attach](#attach)|Anexa existente de interface de recurso para o objeto|
|[CD2DBitmap::CopyFromBitmap](#copyfrombitmap)|Copia a região especificada do bitmap especificado para o bitmap do atual|
|[CD2DBitmap::CopyFromMemory](#copyfrommemory)|Copia a região especificada de memória para o bitmap do atual|
|[CD2DBitmap::CopyFromRenderTarget](#copyfromrendertarget)|Cópias de destino de renderização de uma região especificada especificado para o bitmap do atual|
|[CD2DBitmap::Create](#create)|Cria um CD2DBitmap. (Substitui [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmap::Destroy](#destroy)|Destrói um objeto CD2DBitmap. (Substitui [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DBitmap::Detach](#detach)|Desanexa a interface do recurso do objeto|
|[CD2DBitmap::Get](#get)|Interface de ID2D1Bitmap retorna|
|[CD2DBitmap::GetDPI](#getdpi)|Retornar os pontos por polegada (DPI), do bitmap|
|[CD2DBitmap::GetPixelFormat](#getpixelformat)|Recupera o modo alfa e formato de pixel do bitmap|
|[CD2DBitmap::GetPixelSize](#getpixelsize)|Retorna o tamanho, em unidades dependentes de dispositivo (pixels), do bitmap|
|[CD2DBitmap::GetSize](#getsize)|Retorna o tamanho, em pixels independentes de dispositivo (DIPs), do bitmap|
|[CD2DBitmap::IsValid](#isvalid)|Verifica a validade de recurso (substitui [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|

### <a name="protected-methods"></a>Métodos Protegidos

|Nome|Descrição|
|----------|-----------------|
|[CD2DBitmap::CommonInit](#commoninit)|Inicializa o objeto|

### <a name="public-operators"></a>Operadores públicos

|Nome|Descrição|
|----------|-----------------|
|[CD2DBitmap::Operator ID2D1Bitmap *](#operator_id2d1bitmap_star)|Interface de ID2D1Bitmap retorna|

### <a name="protected-data-members"></a>Membros de dados protegidos

|Nome|Descrição|
|----------|-----------------|
|[CD2DBitmap::m_bAutoDestroyHBMP](#m_bautodestroyhbmp)|TRUE se m_hBmpSrc deve ser destruída; Caso contrário, FALSE.|
|[CD2DBitmap::m_hBmpSrc](#m_hbmpsrc)|Identificador da fonte de bitmap.|
|[CD2DBitmap::m_lpszType](#m_lpsztype)|Tipo de recurso.|
|[CD2DBitmap::m_pBitmap](#m_pbitmap)|Armazena um ponteiro para um objeto ID2D1Bitmap.|
|[CD2DBitmap::m_sizeDest](#m_sizedest)|O tamanho do destino de bitmap.|
|[CD2DBitmap::m_strPath](#m_strpath)|Caminho do arquivo botmap.|
|[CD2DBitmap::m_uiResID](#m_uiresid)|ID do recurso de bitmap.|

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DBitmap`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxrendertarget.h

##  <a name="_dtorcd2dbitmap"></a>  CD2DBitmap:: ~ CD2DBitmap

O destruidor. Chamado quando um objeto de bitmap D2D está sendo destruído.

```
virtual ~CD2DBitmap();
```

##  <a name="attach"></a>  CD2DBitmap::Attach

Anexa existente de interface de recurso para o objeto.

```
void Attach(ID2D1Bitmap* pResource);
```

### <a name="parameters"></a>Parâmetros

*pResource*<br/>
Interface de recursos existente. Não pode ser NULL.

##  <a name="cd2dbitmap"></a>  CD2DBitmap::CD2DBitmap

Constrói um objeto CD2DBitmap de recurso.

```
CD2DBitmap(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszPath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    HBITMAP hbmpSrc,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    BOOL bAutoDestroy = TRUE);

CD2DBitmap(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parâmetros

*pParentTarget*<br/>
Um ponteiro para o destino de renderização.

*uiResID*<br/>
O número de ID de recurso do recurso.

*lpszType*<br/>
Ponteiro para uma cadeia de caracteres terminada em nulo que contém o tipo de recurso.

*sizeDest*<br/>
Tamanho de destino do bitmap.

*bAutoDestroy*<br/>
Indica se o objeto será destruído pelo proprietário (pParentTarget).

*lpszPath*<br/>
Ponteiro para uma cadeia de caracteres terminada em nulo que contém o nome do arquivo.

*hbmpSrc*<br/>
Identificador para o bitmap.

##  <a name="commoninit"></a>  CD2DBitmap::CommonInit

Inicializa o objeto.

```
void CommonInit();
```

##  <a name="copyfrombitmap"></a>  CD2DBitmap::CopyFromBitmap

Copia a região especificada do bitmap especificado para o bitmap do atual.

```
HRESULT CopyFromBitmap(
    const CD2DBitmap* pBitmap,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>Parâmetros

*pBitmap*<br/>
O bitmap para copiar de.

*destPoint*<br/>
No bitmap atual, o canto superior esquerdo da área à qual a região especificada pelo srcRect é copiado.

*srcRect*<br/>
A área do bitmap a copiar.

### <a name="return-value"></a>Valor de retorno

Se o método for bem-sucedido, retornará S_OK. Caso contrário, ele retornará um código de erro HRESULT.

##  <a name="copyfrommemory"></a>  CD2DBitmap::CopyFromMemory

Copia a região especificada de memória para o bitmap do atual.

```
HRESULT CopyFromMemory(
    const void* srcData,
    UINT32 pitch,
    const CD2DRectU* destRect = NULL);
```

### <a name="parameters"></a>Parâmetros

*srcData*<br/>
Os dados a serem copiados.

*Densidade*<br/>
O stride ou tom, do bitmap de origem armazenado em srcData. O stride é o número de bytes de uma verificação de linha (uma linha de pixels na memória). O stride pode ser computado da seguinte fórmula: largura de pixel \* bytes por pixel + preenchimento de memória.

*destRect*<br/>
No bitmap atual, o canto superior esquerdo da área à qual a região especificada pelo srcRect é copiado.

### <a name="return-value"></a>Valor de retorno

Se o método for bem-sucedido, retornará S_OK. Caso contrário, ele retornará um código de erro HRESULT.

##  <a name="copyfromrendertarget"></a>  CD2DBitmap::CopyFromRenderTarget

Copia a região especificada especificado destino de renderização para o bitmap do atual.

```
HRESULT CopyFromRenderTarget(
    const CRenderTarget* pRenderTarget,
    const CD2DPointU* destPoint = NULL,
    const CD2DRectU* srcRect = NULL);
```

### <a name="parameters"></a>Parâmetros

*pRenderTarget*<br/>
O destino de renderização que contém a região para copiar.

*destPoint*<br/>
No bitmap atual, o canto superior esquerdo da área à qual a região especificada pelo srcRect é copiado.

*srcRect*<br/>
A área de renderTarget para copiar.

### <a name="return-value"></a>Valor de retorno

Se o método for bem-sucedido, retornará S_OK. Caso contrário, ele retornará um código de erro HRESULT.

##  <a name="create"></a>  CD2DBitmap::Create

Cria um CD2DBitmap.

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>Parâmetros

*pRenderTarget*<br/>
Um ponteiro para o destino de renderização.

### <a name="return-value"></a>Valor de retorno

Se o método for bem-sucedido, retornará S_OK. Caso contrário, ele retornará um código de erro HRESULT.

##  <a name="destroy"></a>  CD2DBitmap::Destroy

Destrói um objeto CD2DBitmap.

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DBitmap::Detach

Desanexa a interface do recurso do objeto.

```
ID2D1Bitmap* Detach();
```

### <a name="return-value"></a>Valor de retorno

Ponteiro para interface de recurso desanexado.

##  <a name="get"></a>  CD2DBitmap::Get

Interface de ID2D1Bitmap retorna.

```
ID2D1Bitmap* Get();
```

### <a name="return-value"></a>Valor de retorno

Ponteiro para uma interface ID2D1Bitmap ou NULL se o objeto ainda não foi inicializado.

##  <a name="getdpi"></a>  CD2DBitmap::GetDPI

Retorne os pontos por polegada (DPI), do bitmap.

```
CD2DSizeF GetDPI() const;
```

### <a name="return-value"></a>Valor de retorno

O DPI horizontal e vertical do bitmap.

##  <a name="getpixelformat"></a>  CD2DBitmap::GetPixelFormat

Recupera o modo alfa e formato de pixel do bitmap

```
D2D1_PIXEL_FORMAT GetPixelFormat() const;
```

### <a name="return-value"></a>Valor de retorno

O pixel alfa e formato de modo do bitmap.

##  <a name="getpixelsize"></a>  CD2DBitmap::GetPixelSize

Retorna o tamanho, em unidades de dependente de dispositivo (pixels), do bitmap.

```
CD2DSizeU GetPixelSize() const;
```

### <a name="return-value"></a>Valor de retorno

O tamanho, em pixels, do bitmap...

##  <a name="getsize"></a>  CD2DBitmap::GetSize

Retorna o tamanho, em pixels independentes de dispositivo (DIPs), do bitmap.

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>Valor de retorno

O tamanho, em DIPs, do bitmap.

##  <a name="isvalid"></a>  CD2DBitmap::IsValid

Verifica a validade de recurso.

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Valor de retorno

TRUE se o recurso for válido. Caso contrário, FALSE.

##  <a name="m_bautodestroyhbmp"></a>  CD2DBitmap::m_bAutoDestroyHBMP

TRUE se m_hBmpSrc deve ser destruída; Caso contrário, FALSE.

```
BOOL m_bAutoDestroyHBMP;
```

##  <a name="m_hbmpsrc"></a>  CD2DBitmap::m_hBmpSrc

Identificador da fonte de bitmap.

```
HBITMAP m_hBmpSrc;
```

##  <a name="m_lpsztype"></a>  CD2DBitmap::m_lpszType

Tipo de recurso.

```
LPCTSTR m_lpszType;
```

##  <a name="m_pbitmap"></a>  CD2DBitmap::m_pBitmap

Armazena um ponteiro para um objeto ID2D1Bitmap.

```
ID2D1Bitmap* m_pBitmap;
```

##  <a name="m_sizedest"></a>  CD2DBitmap::m_sizeDest

O tamanho do destino de bitmap.

```
CD2DSizeU m_sizeDest;
```

##  <a name="m_strpath"></a>  CD2DBitmap::m_strPath

Caminho do arquivo botmap.

```
CString m_strPath;
```

##  <a name="m_uiresid"></a>  CD2DBitmap::m_uiResID

ID do recurso de bitmap.

```
UINT m_uiResID;
```

##  <a name="operator_id2d1bitmap_star"></a>  CD2DBitmap::Operator ID2D1Bitmap *

Interface de ID2D1Bitmap retorna

```
operator ID2D1Bitmap*();
```

### <a name="return-value"></a>Valor de retorno

Ponteiro para uma interface ID2D1Bitmap ou NULL se o objeto ainda não foi inicializado.

## <a name="see-also"></a>Consulte também

[Classes](../../mfc/reference/mfc-classes.md)
