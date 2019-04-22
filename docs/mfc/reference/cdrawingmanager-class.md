---
title: Classe CDrawingManager
ms.date: 11/04/2016
f1_keywords:
- CDrawingManager
- AFXDRAWMANAGER/CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CreateBitmap_32
- AFXDRAWMANAGER/CDrawingManager::DrawAlpha
- AFXDRAWMANAGER/CDrawingManager::DrawRotated
- AFXDRAWMANAGER/CDrawingManager::DrawEllipse
- AFXDRAWMANAGER/CDrawingManager::DrawGradientRing
- AFXDRAWMANAGER/CDrawingManager::DrawRect
- AFXDRAWMANAGER/CDrawingManager::DrawShadow
- AFXDRAWMANAGER/CDrawingManager::Fill4ColorsGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient2
- AFXDRAWMANAGER/CDrawingManager::GrayRect
- AFXDRAWMANAGER/CDrawingManager::HighlightRect
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_ONE
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_TWO
- AFXDRAWMANAGER/CDrawingManager::HSVtoRGB
- AFXDRAWMANAGER/CDrawingManager::HuetoRGB
- AFXDRAWMANAGER/CDrawingManager::MirrorRect
- AFXDRAWMANAGER/CDrawingManager::PixelAlpha
- AFXDRAWMANAGER/CDrawingManager::PrepareShadowMask
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSL
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSV
- AFXDRAWMANAGER/CDrawingManager::SetAlphaPixel
- AFXDRAWMANAGER/CDrawingManager::SetPixel
- AFXDRAWMANAGER/CDrawingManager::SmartMixColors
helpviewer_keywords:
- CDrawingManager [MFC], CDrawingManager
- CDrawingManager [MFC], CreateBitmap_32
- CDrawingManager [MFC], DrawAlpha
- CDrawingManager [MFC], DrawRotated
- CDrawingManager [MFC], DrawEllipse
- CDrawingManager [MFC], DrawGradientRing
- CDrawingManager [MFC], DrawRect
- CDrawingManager [MFC], DrawShadow
- CDrawingManager [MFC], Fill4ColorsGradient
- CDrawingManager [MFC], FillGradient
- CDrawingManager [MFC], FillGradient2
- CDrawingManager [MFC], GrayRect
- CDrawingManager [MFC], HighlightRect
- CDrawingManager [MFC], HLStoRGB_ONE
- CDrawingManager [MFC], HLStoRGB_TWO
- CDrawingManager [MFC], HSVtoRGB
- CDrawingManager [MFC], HuetoRGB
- CDrawingManager [MFC], MirrorRect
- CDrawingManager [MFC], PixelAlpha
- CDrawingManager [MFC], PrepareShadowMask
- CDrawingManager [MFC], RGBtoHSL
- CDrawingManager [MFC], RGBtoHSV
- CDrawingManager [MFC], SetAlphaPixel
- CDrawingManager [MFC], SetPixel
- CDrawingManager [MFC], SmartMixColors
ms.assetid: 9e4775ca-101b-4aa9-a85a-4d047c701215
ms.openlocfilehash: 506ab7a06653942ecff05043a7e7efabd535115f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781686"
---
# <a name="cdrawingmanager-class"></a>Classe CDrawingManager

O `CDrawingManager` classe implementa os algoritmos de desenho complexos.

## <a name="syntax"></a>Sintaxe

```
class CDrawingManager : public CObject
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[CDrawingManager::CDrawingManager](#cdrawingmanager)|Constrói um objeto `CDrawingManager`.|
|`CDrawingManager::~CDrawingManager`|Destruidor.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CDrawingManager::CreateBitmap_32](#createbitmap_32)|Cria um bitmap de 32 bits independentes de dispositivo (DIB) que os aplicativos podem gravar diretamente.|
|[CDrawingManager::DrawAlpha](#drawalpha)|Exibe os bitmaps que possuem pixels transparentes ou semitransparentes.|
|[CDrawingManager::DrawRotated](#drawrotated)|Gira uma fonte de conteúdo do controlador de domínio dentro do retângulo determinado pelo + /-90 graus|
|[CDrawingManager::DrawEllipse](#drawellipse)|Desenha uma elipse com as cores da borda e preenchimento fornecidas.|
|[CDrawingManager::DrawGradientRing](#drawgradientring)|Desenha um anel e a preenche com um gradiente de cores.|
|[CDrawingManager::DrawLine, CDrawingManager::DrawLineA](#drawline_cdrawingmanager__drawlinea)|Desenha uma linha.|
|[CDrawingManager::DrawRect](#drawrect)|Desenha um retângulo com as cores da borda e preenchimento fornecidos.|
|[CDrawingManager::DrawShadow](#drawshadow)|Desenha uma sombra para uma área retangular.|
|[CDrawingManager::Fill4ColorsGradient](#fill4colorsgradient)|Preenche uma área retangular com dois gradientes de cor.|
|[CDrawingManager::FillGradient](#fillgradient)|Preenche uma área retangular com um gradiente de cores especificada.|
|[CDrawingManager::FillGradient2](#fillgradient2)|Preenche uma área retangular com um gradiente de cores especificada. A direção da alteração de cor do gradiente também é especificada.|
|[CDrawingManager::GrayRect](#grayrect)|Preenche um retângulo com uma cor cinza especificada.|
|[CDrawingManager::HighlightRect](#highlightrect)|Realça uma área retangular.|
|[CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)|Converte uma cor de uma representação de HLS em uma representação de RGB.|
|[CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)|Converte uma cor de uma representação de HLS em uma representação de RGB.|
|[CDrawingManager::HSVtoRGB](#hsvtorgb)|Converte uma cor de uma representação HSV em uma representação de RGB.|
|[CDrawingManager::HuetoRGB](#huetorgb)|Método auxiliar que converte um valor de matiz em um componente vermelho, verde ou azul.|
|[CDrawingManager::MirrorRect](#mirrorrect)|Inverte uma área retangular.|
|[CDrawingManager::PixelAlpha](#pixelalpha)|Método auxiliar que determina a cor final de um pixel semitransparente.|
|[CDrawingManager::PrepareShadowMask](#prepareshadowmask)|Cria um bitmap que pode ser usado como uma sombra.|
|[CDrawingManager::RGBtoHSL](#rgbtohsl)|Converte uma cor de uma representação de RGB em uma representação de HSL.|
|[CDrawingManager::RGBtoHSV](#rgbtohsv)|Converte uma cor de uma representação de RGB em uma representação HSV.|
|[CDrawingManager::SetAlphaPixel](#setalphapixel)|Método auxiliar que as cores de um pixel parcialmente transparente em um bitmap.|
|[CDrawingManager::SetPixel](#setpixel)|Método auxiliar que altera um único pixel em um bitmap para a cor especificada.|
|[CDrawingManager::SmartMixColors](#smartmixcolors)|Combina duas cores com base em uma proporção ponderada.|

## <a name="remarks"></a>Comentários

O `CDrawingManager` classe fornece funções para desenhar retângulos realçados, gradações de cores e sombras. Ele também executa a combinação alfa. Você pode usar essa classe para alterar diretamente da interface do usuário do seu aplicativo.

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxdrawmanager.h

##  <a name="cdrawingmanager"></a>  CDrawingManager::CDrawingManager

Constrói uma [CDrawingManager](../../mfc/reference/cdrawingmanager-class.md) objeto.

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>Parâmetros

*dc*<br/>
[in] Uma referência a um contexto de dispositivo. O `CDrawingManager` usa esse contexto para o desenho.

##  <a name="createbitmap_32"></a>  CDrawingManager::CreateBitmap_32

Cria um bitmap de 32 bits independentes de dispositivo (DIB) que os aplicativos podem gravar diretamente.

```
static HBITMAP __stdcall CreateBitmap_32(
    const CSize& size,
    void** pBits);

static HBITMAP __stdcall CreateBitmap_32(
    HBITMAP bitmap,
    COLORREF clrTransparent = -1);
```

### <a name="parameters"></a>Parâmetros

|||
|-|-|
|Parâmetro|Descrição|
|*size*|[in] Um [CSize](../../atl-mfc-shared/reference/csize-class.md) parâmetro que indica o tamanho do bitmap.|
|*pBits*|[out] Valores de bit de um ponteiro para um ponteiro de dados que recebe o local de DIB.|
|*bitmap*|Um identificador para o bitmap original|
|*clrTransparent*|Um valor RGB especificando uma cor transparente do bitmap original.|

### <a name="return-value"></a>Valor de retorno

Um identificador para o bitmap DIB recém-criado se esse método for bem-sucedida; Caso contrário, nulo.

### <a name="remarks"></a>Comentários

Para obter mais informações sobre como criar um bitmap DIB, consulte [CreateDIBSection](/windows/desktop/api/wingdi/nf-wingdi-createdibitmap).

##  <a name="drawalpha"></a>  CDrawingManager::DrawAlpha

Exibe os bitmaps que possuem pixels transparentes ou semitransparentes.

```
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>Parâmetros

*pDstDC*<br/>
[in] Um ponteiro para o contexto de dispositivo de destino.

*rectDst*<br/>
[in] O retângulo de destino.

*pSrcDC*<br/>
[in] Um ponteiro para o contexto de dispositivo para a fonte.

*rectSrc*<br/>
[in] O retângulo de origem.

### <a name="remarks"></a>Comentários

Esse método realiza a transparência para dois bitmaps. Para obter mais informações sobre transparência, consulte [AlphaBlend](/windows/desktop/api/wingdi/nf-wingdi-alphablend) no SDK do Windows.

##  <a name="drawellipse"></a>  CDrawingManager::DrawEllipse

Desenha uma elipse com as cores da borda e preenchimento fornecidas.

```
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parâmetros

*rect*<br/>
[in] O retângulo delimitador para a elipse.

*clrFill*<br/>
[in] A cor que esse método usa para preencher a elipse.

*clrLine*<br/>
[in] A cor que esse método usa como a borda da elipse.

### <a name="remarks"></a>Comentários

Esse método retorna sem desenhar uma elipse se qualquer cor é definida como -1. Ele também retorna sem desenhar uma elipse se qualquer dimensão do retângulo delimitador é 0.

##  <a name="drawgradientring"></a>  CDrawingManager::DrawGradientRing

Desenha um anel e a preenche com um gradiente de cores.

```
BOOL DrawGradientRing(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    COLORREF colorBorder,
    int nAngle,
    int nWidth,
    COLORREF clrFace = (COLORREF)-1);
```

### <a name="parameters"></a>Parâmetros

*rect*<br/>
[in] Um [CRect](../../atl-mfc-shared/reference/crect-class.md) parâmetro que especifica o limite para o anel de gradiente.

*colorStart*<br/>
[in] A primeira cor do gradiente.

*colorFinish*<br/>
[in] A última cor do gradiente.

*colorBorder*<br/>
[in] A cor da borda.

*nAngle*<br/>
[in] Um parâmetro que especifica o ângulo inicial do gradiente desenho. Esse valor deve estar entre 0 e 360.

*nWidth*<br/>
[in] A largura da borda para o anel.

*clrFace*<br/>
[in] A cor do interior do anel.

### <a name="return-value"></a>Valor de retorno

Diferente de zero se bem-sucedido; Caso contrário, 0.

### <a name="remarks"></a>Comentários

O retângulo definido por *rect* devem ser pelo menos 5 pixels de largo e 5 pixels de altura.

##  <a name="drawline_cdrawingmanager__drawlinea"></a>  CDrawingManager::DrawLine, CDrawingManager::DrawLineA

Desenha uma linha.

```
void DrawLine(
    int x1,
    int y1,
    int x2,
    int y2,
    COLORREF clrLine);

void DrawLineA(
    double x1,
    double y1,
    double x2,
    double y2,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parâmetros

|||
|-|-|
|Parâmetro|Descrição|
|*x1*|[in] A coordenada x em que a linha começa.|
|*y1*|[in] A coordenada y em que a linha começa.|
|*x2*|[in] A coordenada x em que a linha termine.|
|*y2*|[in] A coordenada y em que a linha termine.|
|*clrLine*|[in] A cor da linha.|

### <a name="remarks"></a>Comentários

Esse método falhar se *clrLine* é igual a -1.

##  <a name="drawrect"></a>  CDrawingManager::DrawRect

Desenha um retângulo com as cores da borda e preenchimento fornecidos.

```
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parâmetros

*rect*<br/>
[in] Os limites do retângulo.

*clrFill*<br/>
[in] A cor que esse método usa para preencher o retângulo.

*clrLine*<br/>
[in] A cor que esse método usa para a borda do retângulo.

### <a name="remarks"></a>Comentários

Esse método retorna sem desenhar um retângulo se qualquer cor é definida como -1. Ele também retorna se a dimensão do retângulo é 0.

##  <a name="drawshadow"></a>  CDrawingManager::DrawShadow

Desenha uma sombra para uma área retangular.

```
BOOL DrawShadow(
    CRect rect,
    int nDepth,
    int iMinBrightness = 100,
    int iMaxBrightness = 50,
    CBitmap* pBmpSaveBottom = NULL,
    CBitmap* pBmpSaveRight = NULL,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bRightShadow = TRUE);
```

### <a name="parameters"></a>Parâmetros

*rect*<br/>
[in] Uma área retangular em seu aplicativo. O Gerenciador de desenho será desenhar uma sombra sob essa área.

*nDepth*<br/>
[in] A largura e altura da sombra.

*iMinBrightness*<br/>
[in] O brilho mínimo da sombra.

*iMaxBrightness*<br/>
[in] O brilho máximo da sombra.

*pBmpSaveBottom*<br/>
[in] Um ponteiro para um bitmap que contém a imagem para a parte inferior da sombra.

*pBmpSaveRight*<br/>
[in] Um ponteiro para um bitmap que contém a imagem para a sombra que é desenhada no lado direito do retângulo.

*clrBase*<br/>
[in] A cor da sombra.

*bRightShadow*<br/>
[in] Um parâmetro booliano que indica como a sombra é desenhada. Se *bRightShadow* é `TRUE`, `DrawShadow` desenha uma sombra no lado direito do retângulo.

### <a name="return-value"></a>Valor de retorno

Diferente de zero se bem-sucedido; Caso contrário, 0.

### <a name="remarks"></a>Comentários

Você pode fornecer dois bitmaps válidos para a parte inferior e direita sombras usando os parâmetros *pBmpSaveBottom* e *pBmpSaveRight*. Se esses [CBitmap](../../mfc/reference/cbitmap-class.md) objetos têm um objeto GDI anexado, `DrawShadow` usará esses bitmaps como sombras. Se o `CBitmap` parâmetros não têm um objeto GDI anexado, `DrawShadow` desenha a sombra e anexa os bitmaps para os parâmetros. Em futuras chamadas para `DrawShadow`, você pode fornecer esses bitmaps para acelerar o processo de desenho. Para obter mais informações sobre o `CBitmap` classe e objetos GDI, consulte [objetos gráficos](../../mfc/graphic-objects.md).

Se um desses parâmetros é `NULL`, `DrawShadow` automaticamente desenhará a sombra.

Se você definir *bRightShadow* como FALSE, a sombra será desenhada abaixo e à esquerda da área retangular.

### <a name="example"></a>Exemplo

O exemplo a seguir demonstra como usar o `DrawShadow` método da `CDrawingManager` classe. Este trecho de código é parte do [amostra de demonstração de folha Prop](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

##  <a name="fill4colorsgradient"></a>  CDrawingManager::Fill4ColorsGradient

Preenche uma área retangular com dois gradientes de cor.

```
void Fill4ColorsGradient(
    CRect rect,
    COLORREF colorStart1,
    COLORREF colorFinish1,
    COLORREF colorStart2,
    COLORREF colorFinish2,
    BOOL bHorz = TRUE,
    int nPercentage = 50);
```

### <a name="parameters"></a>Parâmetros

*rect*<br/>
[in] Retângulo a ser preenchido.

*colorStart1*<br/>
[in] A cor inicial do gradiente de cores de primeiro.

*colorFinish1*<br/>
[in] A cor final do gradiente de cores de primeiro.

*colorStart2*<br/>
[in] A cor inicial do gradiente de cores segundo.

*colorFinish2*<br/>
[in] A cor final do gradiente de cores segundo.

*bHorz*<br/>
[in] Um parâmetro booliano que indica se `Fill4ColorsGradient` cores um gradiente horizontal ou vertical. TRUE indica que um gradiente horizontal.

*nPercentage*<br/>
[in] Um inteiro de 0 a 100. Esse valor indica a porcentagem do retângulo a ser preenchido com o gradiente de cores de primeiro.

### <a name="remarks"></a>Comentários

Quando um retângulo é preenchido com dois gradientes de cor, eles são localizado acima uns aos outros ou próximas umas às outras, dependendo do valor de *bHorz*. Cada gradiente de cores é calculada separadamente com o método [CDrawingManager::FillGradient](#fillgradient).

Este método gera uma falha de asserção se *nPercentage* é menor que 0 ou maior que 100.

##  <a name="fillgradient"></a>  CDrawingManager::FillGradient

Preenche uma área retangular com gradiente de cores especificada.

```
void FillGradient(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    BOOL bHorz = TRUE,
    int nStartFlatPercentage = 0,
    int nEndFlatPercentage = 0);
```

### <a name="parameters"></a>Parâmetros

*rect*<br/>
[in] A área retangular para preencher.

*colorStart*<br/>
[in] A primeira cor do gradiente.

*colorFinish*<br/>
[in] A cor final do gradiente.

*bHorz*<br/>
[in] Um parâmetro booliano que especifica se `FillGradient` deve desenhar um gradiente horizontal ou vertical.

*nStartFlatPercentage*<br/>
[in] A porcentagem do retângulo que `FillGradient` preenche com *colorStart* antes de iniciar o gradiente.

*nEndFlatPercentage*<br/>
[in] A porcentagem do retângulo que `FillGradient` preenche com *colorFinish* após a conclusão do gradiente.

### <a name="example"></a>Exemplo

O exemplo a seguir demonstra como usar o `FillGradient` método da `CDrawingManager` classe. Este trecho de código faz parte de [amostra de demonstração do MS Office 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

##  <a name="fillgradient2"></a>  CDrawingManager::FillGradient2

Preenche uma área retangular com um gradiente de cores especificada.

```
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>Parâmetros

*rect*<br/>
[in] A área retangular para preencher.

*colorStart*<br/>
[in] A primeira cor do gradiente.

*colorFinish*<br/>
[in] A última cor do gradiente.

*nAngle*<br/>
[in] Um inteiro entre 0 e 360. Esse parâmetro especifica a direção do gradiente de cores.

### <a name="remarks"></a>Comentários

Use *nAngle* para especificar a direção do gradiente de cores. Quando você especifica a direção do gradiente de cores, você também especificar onde começa o gradiente de cores. Um valor de 0 para *nAngle* indica que o gradiente é iniciado na parte superior do retângulo. Como *nAngle* aumenta, o local inicial para o gradiente move no sentido anti-horário com base no ângulo.

### <a name="example"></a>Exemplo

O exemplo a seguir demonstra como usar o `FillGradient2` método da `CDrawingManager` classe. Este trecho de código é parte do [exemplo de novos controles](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

##  <a name="grayrect"></a>  CDrawingManager::GrayRect

Preenche um retângulo com uma cor cinza especificada.

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>Parâmetros

*rect*<br/>
[in] A área retangular para preencher.

*nPercentage*<br/>
[in] O percentual de cinza que você deseja no retângulo.

*clrTransparent*<br/>
[in] A cor transparente.

*clrDisabled*<br/>
[in] A cor que usa esse método para eliminação de saturação, se *nPercentage* é definido como -1.

### <a name="return-value"></a>Valor de retorno

TRUE se o método foi bem-sucedida; Caso contrário, FALSE.

### <a name="remarks"></a>Comentários

Para o parâmetro *nPercentage*, um valor mais baixo indica uma cor mais escura.

O valor máximo para *nPercentage* é 200. Um valor maior que 200 não altera a aparência do retângulo. Se o valor for -1, esse método usa *clrDisabled* para limitar a saturação do retângulo.

##  <a name="highlightrect"></a>  CDrawingManager::HighlightRect

Realça uma área retangular.

```
BOOL HighlightRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    int nTolerance = 0,
    COLORREF clrBlend = (COLORREF)-1);
```

### <a name="parameters"></a>Parâmetros

*rect*<br/>
[in] Uma área retangular para realçar.

*nPercentage*<br/>
[in] Uma porcentagem que indica o grau de transparência do realce deve ser.

*clrTransparent*<br/>
[in] A cor transparente.

*nTolerance*<br/>
[in] Um inteiro entre 0 e 255 que indica a tolerância de cor.

*clrBlend*<br/>
[in] A cor de base para mesclagem.

### <a name="return-value"></a>Valor de retorno

TRUE se o método for bem-sucedido; Caso contrário, FALSE.

### <a name="remarks"></a>Comentários

Se *nPercentage* estiver entre 0 e 99, `HighlightRect` usa a algoritmo de mistura de alfa. Para obter mais informações sobre a combinação alfa, consulte [alfa de mesclagem linhas e preenchimentos](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills). Se *nPercentage* é -1, esse método usa o nível de realce padrão. Se *nPercentage* é 100, esse método não faz nada e retorna TRUE.

O método usa o parâmetro *nTolerance* para determinar se é para realçar a área retangular. Para realçar o retângulo, a diferença entre a cor do plano de fundo do seu aplicativo e *clrTransparent* deve ser menor que *nTolerance* em cada componente de cor (vermelho, verde e azul).

##  <a name="hlstorgb_one"></a>  CDrawingManager::HLStoRGB_ONE

Converte uma cor de uma representação de HLS em uma representação de RGB.

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parâmetros

*H*<br/>
[in] Um número entre 0 e 1 que representa o matiz da cor.

*L*<br/>
[in] Um número entre 0 e 1 que indica a luminosidade da cor.

*S*<br/>
[in] Um número entre 0 e 1 que indica a saturação da cor.

### <a name="return-value"></a>Valor de retorno

A representação de RGB da cor HLS fornecida.

### <a name="remarks"></a>Comentários

Uma cor pode ser representada como HSV (matiz, saturação e valor), HSL (matiz, saturação e luminosidade) ou RGB (vermelho, verde e azul). Para obter mais informações sobre as diferentes representações de cor, consulte [cor](/windows/desktop/uxguide/vis-color).

Esse método e o `CDrawingManager::HLStoRGB_TWO` método executar a mesma operação, mas requerem valores diferentes para o *H* parâmetro. Nesse método, *H* é uma porcentagem do círculo. No `CDrawingManager::HLStoRGB_TWO` método, *H* é um valor de grau entre 0 e 360, que representam vermelho. Por exemplo, com `HLStoRGB_ONE`, um valor de 0,25 para *H* é equivalente a um valor de 90 com `HLStoRGB_TWO`.

##  <a name="hlstorgb_two"></a>  CDrawingManager::HLStoRGB_TWO

Converte uma cor de uma representação de HLS em uma representação de RGB.

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>Parâmetros

*H*<br/>
[in] Um número entre 0 e 360, que representa o matiz da cor.

*L*<br/>
[in] Um número entre 0 e 1 que indica a luminosidade da cor.

*S*<br/>
[in] Um número entre 0 e 1 que indica a saturação da cor.

### <a name="return-value"></a>Valor de retorno

A representação de RGB da cor HLS fornecida.

### <a name="remarks"></a>Comentários

Uma cor pode ser representada como HSV (matiz, saturação e valor), HSL (matiz, saturação e luminosidade) ou RGB (vermelho, verde e azul). Para obter mais informações sobre as diferentes representações de cor, consulte [cor](/windows/desktop/uxguide/vis-color).

Esse método e o [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) método executar a mesma operação, mas requerem valores diferentes para o *H* parâmetro. Nesse método, *H* é um valor de grau entre 0 e 360, que representam vermelho. No [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one) método *H* é uma porcentagem do círculo. Por exemplo, com `HLStoRGB_ONE`, um valor de 0,25 para *H* é equivalente a um valor de 90 com `HLStoRGB_TWO`.

##  <a name="hsvtorgb"></a>  CDrawingManager::HSVtoRGB

Converte uma cor de uma representação HSV em uma representação de RGB.

```
static COLORREF __stdcall HSVtoRGB(
    double H,
    double S,
    double V);
```

### <a name="parameters"></a>Parâmetros

|||
|-|-|
|Parâmetro|Descrição|
|*H*|[in] Um número entre 0 e 360, que indica o matiz da cor.|
|*S*|[in] Um número entre 0 e 1 que indica a saturação da cor.|
|*V*|[in] Um número entre 0 e 1 que indica o valor da cor.|

### <a name="return-value"></a>Valor de retorno

A representação de RGB da cor HSV fornecida.

### <a name="remarks"></a>Comentários

Uma cor pode ser representada como HSV (matiz, saturação e valor), HSL (matiz, saturação e luminosidade) ou RGB (vermelho, verde e azul). Para obter mais informações sobre as diferentes representações de cor, consulte [cor](/windows/desktop/uxguide/vis-color).

##  <a name="huetorgb"></a>  CDrawingManager::HuetoRGB

Converte um valor de matiz em um componente vermelho, verde ou azul.

```
static double __stdcall HuetoRGB(
    double m1,
    double m2,
    double h);

static BYTE __stdcall HueToRGB(
    float rm1,
    float rm2,
    float rh);
```

### <a name="parameters"></a>Parâmetros

*m1*<br/>
[in] Consulte os comentários.

*m2*<br/>
[in] Consulte os comentários.

*h*<br/>
[in] Consulte os comentários.

*rm1*<br/>
[in] Consulte os comentários.

*rm2*<br/>
[in] Consulte os comentários.

*rh*<br/>
[in] Consulte os comentários.

### <a name="return-value"></a>Valor de retorno

O componente vermelho, verde ou azul individual para o matiz fornecido.

### <a name="remarks"></a>Comentários

Esse método é um método auxiliar que o `CDrawingManager` classe usa para calcular os componentes individuais de vermelhos, verdes e azuis da cor em uma representação HSV ou HSL. Esse método não foi projetado para ser chamado diretamente pelo programador. Os parâmetros de entrada são valores que dependem do algoritmo de conversão.

Para converter uma cor HSV ou HSL em uma representação de RGB, chame um dos seguintes métodos:

- [CDrawingManager::HSVtoRGB](#hsvtorgb)

- [CDrawingManager::HLStoRGB_ONE](#hlstorgb_one)

- [CDrawingManager::HLStoRGB_TWO](#hlstorgb_two)

##  <a name="mirrorrect"></a>  CDrawingManager::MirrorRect

Inverte uma área retangular.

```
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parâmetros

*rect*<br/>
[in] O retângulo delimitador da área a inverter.

*bHorz*<br/>
[in] Um parâmetro booliano que indica se o retângulo gira horizontal ou verticalmente.

### <a name="remarks"></a>Comentários

Esse método pode inverter qualquer área do contexto do dispositivo pertencente a `CDrawingManager` classe. Se *bHorz* é definido como TRUE, este método inverte a área horizontalmente. Caso contrário, ele inverte a área verticalmente.

##  <a name="pixelalpha"></a>  CDrawingManager::PixelAlpha

Calcula a cor final de um pixel semitransparente.

```
static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    int percent);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    double percentR,
    double percentG,
    double percentB);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    COLORREF dstPixel,
    int percent);
```

### <a name="parameters"></a>Parâmetros

*srcPixel*<br/>
[in] A cor inicial para o pixel.

*percent*<br/>
[in] Um número entre 0 e 100 que representa a porcentagem de transparência. Um valor de 100 indica que a cor inicial é completamente transparente.

*percentR*<br/>
[in] Um número entre 0 e 100 que representa a porcentagem de transparência para o componente vermelho.

*percentG*<br/>
[in] Um número entre 0 e 100 que representa a porcentagem de transparência para o componente verde.

*percentB*<br/>
[in] Um número entre 0 e 100 que representa a porcentagem de transparência para o componente azul.

*dstPixel*<br/>
[in] A cor de base para o pixel.

### <a name="return-value"></a>Valor de retorno

A cor final para o pixel semitransparente.

### <a name="remarks"></a>Comentários

Essa é uma classe auxiliar para colorir semitransparente bitmaps e não foi projetada para ser chamado diretamente pelo programador.

Quando você usa a versão do método que tem *dstPixel*, a cor final é uma combinação de *dstPixel* e *srcPixel*. O *srcPixel* cor é a cor parcialmente transparente sobre a cor base do *dstPixel*.

##  <a name="prepareshadowmask"></a>  CDrawingManager::PrepareShadowMask

Cria um bitmap que pode ser usado como uma sombra.

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>Parâmetros

*nDepth*<br/>
[in] A largura e altura da sombra.

*clrBase*<br/>
[in] A cor da sombra.

*iMinBrightness*<br/>
[in] O brilho mínimo da sombra.

*iMaxBrightness*<br/>
[in] O brilho máximo da sombra.

### <a name="return-value"></a>Valor de retorno

Um identificador para o bitmap criado se esse método for bem-sucedida; Caso contrário, nulo.

### <a name="remarks"></a>Comentários

Se *nDepth* é definido como 0, esse método é encerrado e retornará NULL. Se *nDepth* for menor que 3, a largura e altura da sombra são definidas como 3 pixels.

##  <a name="rgbtohsl"></a>  CDrawingManager::RGBtoHSL

Converte uma cor de uma representação de vermelho, verde e azul (RGB) para um matiz, saturação e representação de luminosidade (HSL).

```
static void __stdcall RGBtoHSL(
    COLORREF rgb,
    double* H,
    double* S,
    double* L);
```

### <a name="parameters"></a>Parâmetros

|||
|-|-|
|Parâmetro|Descrição|
|*rgb*|[in] A cor em valores de RGB.|
|*H*|[out] Um ponteiro para um duplo em que o método armazena o matiz da cor.|
|*S*|[out] Um ponteiro para um duplo em que o método armazena a saturação da cor.|
|*L*|[out] Um ponteiro para um duplo em que o método armazena a luminosidade da cor.|

### <a name="remarks"></a>Comentários

Uma cor pode ser representada como HSV (matiz, saturação e valor), HSL (matiz, saturação e luminosidade) ou RGB (vermelho, verde e azul). Para obter mais informações sobre as diferentes representações de cor, consulte [cor](/windows/desktop/uxguide/vis-color).

O valor retornado de *H* é representado como uma fração entre 0 e 1, onde 0 e 1 representam vermelho. Os valores retornados para *S* e *L* são números entre 0 e 1.

##  <a name="rgbtohsv"></a>  CDrawingManager::RGBtoHSV

Converte uma cor de uma representação de RGB em uma representação HSV.

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>Parâmetros

*rgb*<br/>
[in] A cor a ser convertido em uma representação de RGB.

*H*<br/>
[out] Um ponteiro para um duplo em que este método armazena a matiz resultante para a cor.

*S*<br/>
[out] Um ponteiro para um duplo em que este método armazena a saturação resultante para a cor.

*V*<br/>
[out] Um ponteiro para um duplo em que este método armazena o valor resultante para a cor.

### <a name="remarks"></a>Comentários

Uma cor pode ser representada como HSV (matiz, saturação e valor), HSL (matiz, saturação e luminosidade) ou RGB (vermelho, verde e azul). Para obter mais informações sobre as diferentes representações de cor, consulte [cor](/windows/desktop/uxguide/vis-color).

O valor retornado de *H* é um número entre 0 e 360, onde 0 e 360 indicar vermelho. O retorno de valores para *S* e *V* são números entre 0 e 1.

##  <a name="setalphapixel"></a>  CDrawingManager::SetAlphaPixel

Um pixel transparente em um bitmap de cores.

```
static void __stdcall SetAlphaPixel(
    COLORREF* pBits,
    CRect rect,
    int x,
    int y,
    int percent,
    int iShadowSize,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bIsRight = TRUE);
```

### <a name="parameters"></a>Parâmetros

*pBits*<br/>
[in] Um ponteiro para os valores de bit do bitmap.

*rect*<br/>
[in] Uma área retangular em seu aplicativo. O Gerenciador de desenho desenha uma sombra abaixo e à direita desta área.

*x*<br/>
[in] A coordenada horizontal do pixel para a cor.

*y*<br/>
[in] A coordenada vertical do pixel para a cor.

*percent*<br/>
[in] A porcentagem de transparência.

*iShadowSize*<br/>
[in] A largura e altura da sombra.

*clrBase*<br/>
[in] A cor da sombra.

*bIsRight*<br/>
[in] Um parâmetro booliano que indica qual pixel para a cor. Consulte a seção Comentários para obter mais informações.

### <a name="remarks"></a>Comentários

Esse método é um método auxiliar que é usado pelas [CDrawingManager::DrawShadow](#drawshadow) método. É recomendável que se você quiser desenhar uma sombra, chame `CDrawingManager::DrawShadow` em vez disso.

Se *bIsRight* é definido como TRUE, a cor do pixel é medido *x* pixels da borda direita de *rect*. Se for FALSE, a cor do pixel é medido *x* pixels da borda esquerda da *rect*.

##  <a name="setpixel"></a>  CDrawingManager::SetPixel

Altera um único pixel em um bitmap para a cor especificada.

```
static void __stdcall SetPixel(
    COLORREF* pBits,
    int cx,
    int cy,
    int x,
    int y,
    COLORREF color);
```

### <a name="parameters"></a>Parâmetros

|||
|-|-|
|Parâmetro|Descrição|
|*pBits*|[in] Um ponteiro para os valores de bit do bitmap.|
|*cx*|[in] A largura total do bitmap.|
|*cy*|[in] A altura total do bitmap.|
|*x*|[in] A coordenada x do pixel no bitmap para alterar.|
|*y*|[in] A coordenada y do pixel no bitmap para alterar.|
|*color*|[in] A nova cor para o pixel identificado pelas coordenadas fornecidas.|

##  <a name="smartmixcolors"></a>  CDrawingManager::SmartMixColors

Combina duas cores com base em uma proporção ponderada.

```
static COLORREF __stdcall SmartMixColors(
    COLORREF color1,
    COLORREF color2,
    double dblLumRatio = 1.,
    int k1 = 1,
    int k2 = 1);
```

### <a name="parameters"></a>Parâmetros

|||
|-|-|
|Parâmetro|Descrição|
|*color1*|[in] A primeira cor misturar.|
|*color2*|[in] A segunda cor misturar.|
|*dblLumRatio*|[in] A razão para a nova luminosidade da cor. `SmartMixColors` Multiplica a luminosidade da cor mista por essa proporção antes de determinar uma cor final.|
|*k1*|[in] A proporção ponderada para a primeira cor.|
|*k2*|[in] A proporção ponderada para a segunda cor.|

### <a name="return-value"></a>Valor de retorno

Uma cor que representa uma combinação ponderada das cores fornecidas.

### <a name="remarks"></a>Comentários

Esse método falhará com um erro se o *k1* ou *k2* é menor que zero. Se ambos os parâmetros são definidos como 0, o método retorna `RGB(0, 0, 0)`.

A proporção ponderada é calculada com a seguinte fórmula: (color1 \* k1 + cor2 \* k2) /(k1 + k2). Depois que a proporção ponderada é determinada, o método calcula a luminosidade da cor misto. Ele, em seguida, multiplica a luminosidade por *dblLumRatio*. Se o valor for maior que 1.0, o método define a luminosidade da cor misto para o novo valor. Caso contrário, a luminosidade é definida como 1.0.

##  <a name="drawrotated"></a>  CDrawingManager::DrawRotated

Uma fonte de conteúdo do controlador de domínio dentro do retângulo determinado gira 90 graus.

```
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>Parâmetros

*rectDest*<br/>
Retângulo de destino.

*dcSrc*<br/>
O contexto de dispositivo de origem.

*bClockWise*<br/>
VERDADEIRO indica graus de rotação + 90; FALSE indica Girar-90 graus.

### <a name="remarks"></a>Comentários

## <a name="see-also"></a>Consulte também

[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
