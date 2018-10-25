---
title: Classe CMFCToolTipCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetIconSize
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetParams
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawBorder
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawLabel
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnFillBackground
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetFixedWidth
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetHotRibbonButton
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetLocation
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetParams
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolTipCtrl [MFC], GetIconSize
- CMFCToolTipCtrl [MFC], GetParams
- CMFCToolTipCtrl [MFC], OnDrawBorder
- CMFCToolTipCtrl [MFC], OnDrawDescription
- CMFCToolTipCtrl [MFC], OnDrawIcon
- CMFCToolTipCtrl [MFC], OnDrawLabel
- CMFCToolTipCtrl [MFC], OnDrawSeparator
- CMFCToolTipCtrl [MFC], OnFillBackground
- CMFCToolTipCtrl [MFC], SetDescription
- CMFCToolTipCtrl [MFC], SetFixedWidth
- CMFCToolTipCtrl [MFC], SetHotRibbonButton
- CMFCToolTipCtrl [MFC], SetLocation
- CMFCToolTipCtrl [MFC], SetParams
ms.assetid: 9fbfcfb1-a8ab-417f-ae29-9a9ca85ee58f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d3a704f4c683e774057265604ecd69cd03dfb657
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056939"
---
# <a name="cmfctooltipctrl-class"></a>Classe CMFCToolTipCtrl

Uma implementação estendida da dica de ferramenta com base nas [classe CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md). Uma dica de ferramenta com base no `CMFCToolTipCtrl` classe pode exibir um ícone, um rótulo e uma descrição. Você pode personalizar sua aparência visual usando um preenchimento gradual, cores de borda e texto personalizado, texto em negrito, cantos arredondados ou um estilo de balão.

Para obter mais detalhes, consulte o código-fonte localizado na **VC\\atlmfc\\src\\mfc** pasta de instalação do Visual Studio.

## <a name="syntax"></a>Sintaxe

```
class CMFCToolTipCtrl : public CToolTipCtrl
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|Construtor padrão.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CMFCToolTipCtrl::GetIconSize](#geticonsize)|Retorna o tamanho de um ícone em uma dica de ferramenta.|
|[CMFCToolTipCtrl::GetParams](#getparams)|Retorna as configurações de exibição de uma dica de ferramenta.|
|[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)|Desenha a borda de uma dica de ferramenta.|
|[CMFCToolTipCtrl::OnDrawDescription](#ondrawdescription)||
|[CMFCToolTipCtrl::OnDrawIcon](#ondrawicon)|Exibe um ícone em uma dica de ferramenta.|
|[CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)|Desenha o rótulo de uma dica de ferramenta ou calcula o tamanho do rótulo.|
|[CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)|Desenha o separador entre o rótulo e a descrição em uma dica de ferramenta.|
|[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)|Preenche a tela de fundo da dica de ferramenta.|
|[CMFCToolTipCtrl::SetDescription](#setdescription)|Define a descrição a ser exibido, a dica de ferramenta.|
|[CMFCToolTipCtrl::SetFixedWidth](#setfixedwidth)||
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||
|[CMFCToolTipCtrl::SetLocation](#setlocation)||
|[CMFCToolTipCtrl::SetParams](#setparams)|Especifica a aparência visual de uma dica de ferramenta usando um `CMFCToolTipInfo` objeto.|

## <a name="remarks"></a>Comentários

Use `CMFCToolTipCtrl`, `CMFCToolTipInfo`, e [classe CTooltipManager](../../mfc/reference/ctooltipmanager-class.md) objetos juntos para implementar dicas de ferramenta personalizadas em seu aplicativo.

Por exemplo, para usar dicas de ferramenta do estilo de balão, siga estas etapas:

1. Use o [classe CWinAppEx](../../mfc/reference/cwinappex-class.md) método para inicializar o Gerenciador de dica de ferramenta em seu aplicativo.

2. Criar um `CMFCToolTipInfo` estrutura para especificar o estilo visual que você deseja:

```
CMFCToolTipInfo params;
    params.m_bBoldLabel = FALSE;
    params.m_bDrawDescription = FALSE;
    params.m_bDrawIcon = FALSE;
    params.m_bRoundedCorners = TRUE;
    params.m_bDrawSeparator = FALSE;
    if (m_bCustomColors)
{
    params.m_clrFill = RGB (255,
    255,
    255);

    params.m_clrFillGradient = RGB (228,
    228,
    240);

    params.m_clrText = RGB (61,
    83,
    80);

    params.m_clrBorder = RGB (144,
    149,
    168);

}
```
3. Use o [CTooltipManager::SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams) método para definir o estilo visual para todas as dicas de ferramenta no aplicativo usando os estilos definidos no `CMFCToolTipInfo` objeto:

```
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMFCToolTipCtrl), &params);
```
Também é possível derivar uma nova classe de `CMFCToolTipCtrl` para controlar o comportamento de dica de ferramenta e renderização. Para especificar uma nova classe de controle de dica de ferramenta, use o `CTooltipManager::SetTooltipParams` método:

```
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMyToolTipCtrl))
```
Para restaurar o padrão a dica de ferramenta classe de controle e redefinir a aparência da dica de ferramenta para seu estado padrão, especifique NULL, o tempo de execução classe e a dica de ferramenta informações parâmetros de `SetTooltipParams`:

```
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    NULL,
    NULL);
```

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra como construir um `CMFCToolTipCtrl` do objeto, defina a descrição do que a dica de ferramenta exibe e definir a largura do controle de dica de ferramenta.

[!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

[CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxtooltipctrl.h

##  <a name="cmfctooltipctrl"></a>  CMFCToolTipCtrl::CMFCToolTipCtrl

```
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```

### <a name="parameters"></a>Parâmetros

[in] *pParams*<br/>

### <a name="remarks"></a>Comentários

##  <a name="geticonsize"></a>  CMFCToolTipCtrl::GetIconSize

Retorna o tamanho de um ícone em uma dica de ferramenta.

```
virtual CSize GetIconSize();
```

### <a name="return-value"></a>Valor de retorno

O tamanho do ícone, em pixels.

##  <a name="getparams"></a>  CMFCToolTipCtrl::GetParams

Retorna as configurações de exibição de uma dica de ferramenta.

```
const CMFCToolTipInfo& GetParams() const;
```

### <a name="return-value"></a>Valor de retorno

As configurações de exibição de dica de ferramenta atual, que são armazenadas em um [classe CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) objeto.

##  <a name="ondrawborder"></a>  CMFCToolTipCtrl::OnDrawBorder

Desenha a borda de uma dica de ferramenta.

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect,
    COLORREF clrLine);
```

### <a name="parameters"></a>Parâmetros

*pDC*<br/>
[in] Ponteiro para um contexto de dispositivo.

*Rect*<br/>
[in] O retângulo delimitador da dica de ferramenta.

*clrLine*<br/>
[in] Cor da borda.

### <a name="remarks"></a>Comentários

Substitua este método em uma classe derivada para personalizar a aparência da borda da dica de ferramenta.

##  <a name="ondrawdescription"></a>  CMFCToolTipCtrl::OnDrawDescription

```
virtual CSize OnDrawDescription(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Parâmetros

[in] *pDC*<br/>
[in] *rect*<br/>
[in] *bCalcOnly*<br/>

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="ondrawicon"></a>  CMFCToolTipCtrl::OnDrawIcon

Exibe um ícone em uma dica de ferramenta.

```
virtual BOOL OnDrawIcon(
    CDC* pDC,
    CRect rectImage);
```

### <a name="parameters"></a>Parâmetros

*pDC*<br/>
[in] Um ponteiro para um contexto de dispositivo.

*rectImage*<br/>
[in] Coordenadas do ícone.

### <a name="return-value"></a>Valor de retorno

TRUE se o ícone de ter sido desenhado. Caso contrário, FALSE.

### <a name="remarks"></a>Comentários

Substitua este método em uma classe derivada para exibir um ícone personalizado. Você também deve substituir [CMFCToolTipCtrl::GetIconSize](#geticonsize) para habilitar a dica de ferramenta calcular corretamente o layout de texto e uma descrição.

##  <a name="ondrawlabel"></a>  CMFCToolTipCtrl::OnDrawLabel

Desenha o rótulo de uma dica de ferramenta ou calcula o tamanho do rótulo.

```
virtual CSize OnDrawLabel(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>Parâmetros

*pDC*<br/>
[in] Um ponteiro para um contexto de dispositivo.

*Rect*<br/>
[in] Retângulo delimitador da área de rótulo.

*bCalcOnly*<br/>
[in] Se for TRUE, o rótulo não será desenhado.

### <a name="return-value"></a>Valor de retorno

Tamanho do rótulo, em pixels.

### <a name="remarks"></a>Comentários

Substitua este método em uma classe derivada se você quiser personalizar a aparência do rótulo de dica de ferramenta.

##  <a name="ondrawseparator"></a>  CMFCToolTipCtrl::OnDrawSeparator

Desenha o separador entre o rótulo e a descrição em uma dica de ferramenta.

```
virtual void OnDrawSeparator(
    CDC* pDC,
    int x1,
    int x2,
    int y);
```

### <a name="parameters"></a>Parâmetros

*pDC*<br/>
[in] Um ponteiro para um contexto de dispositivo.

*x1*<br/>
[in] Coordenada horizontal da extremidade esquerda do separador.

*X2*<br/>
[in] Coordenada horizontal da extremidade direita do separador.

*Y*<br/>
[in] Coordenada vertical do separador.

### <a name="remarks"></a>Comentários

A implementação padrão desenha uma linha do ponto (x1, y) para o ponto (x2, y).

Substitua este método em uma classe derivada para personalizar a aparência do separador.

##  <a name="onfillbackground"></a>  CMFCToolTipCtrl::OnFillBackground

Preenche a tela de fundo da dica de ferramenta.

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect,
    COLORREF& clrText,
    COLORREF& clrLine);
```

### <a name="parameters"></a>Parâmetros

*pDC*<br/>
[in] Um ponteiro para um contexto de dispositivo.

*Rect*<br/>
[in] Especifica o retângulo delimitador da área a ser preenchida.

*clrText*<br/>
[in] Cor de primeiro plano da dica de ferramenta.

*clrLine*<br/>
[in] Cor das bordas e a linha de delimitador entre o rótulo e uma descrição.

### <a name="remarks"></a>Comentários

A implementação padrão preenche o retângulo especificado por *rect* com a cor ou padrão especificado pela chamada a mais recente [CMFCToolTipCtrl::SetParams](#setparams).

Substitua este método em uma classe derivada se você quiser personalizar a aparência da dica de ferramenta.

##  <a name="setdescription"></a>  CMFCToolTipCtrl::SetDescription

Define a descrição a ser exibido, a dica de ferramenta.

```
virtual void SetDescription(const CString strDesrciption);
```

### <a name="parameters"></a>Parâmetros

*strDesrciption*<br/>
[in] Texto de descrição.

### <a name="remarks"></a>Comentários

O texto de descrição é exibido na dica de ferramenta sob o separador.

##  <a name="setfixedwidth"></a>  CMFCToolTipCtrl::SetFixedWidth

```
void SetFixedWidth(
    int nWidthRegular,
    int nWidthLargeImage);
```

### <a name="parameters"></a>Parâmetros

[in] *nWidthRegular*<br/>
[in] *nWidthLargeImage*<br/>

### <a name="remarks"></a>Comentários

##  <a name="sethotribbonbutton"></a>  CMFCToolTipCtrl::SetHotRibbonButton

```
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```

### <a name="parameters"></a>Parâmetros

[in] *pRibbonButton*<br/>

### <a name="remarks"></a>Comentários

##  <a name="setlocation"></a>  CMFCToolTipCtrl::SetLocation

```
void SetLocation(CPoint pt);
```

### <a name="parameters"></a>Parâmetros

[in] *pt*<br/>

### <a name="remarks"></a>Comentários

##  <a name="setparams"></a>  CMFCToolTipCtrl::SetParams

Especifica a aparência visual de uma dica de ferramenta usando um [classe CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) objeto.

```
void SetParams(CMFCToolTipInfo* pParams);
```

### <a name="parameters"></a>Parâmetros

*pParams*<br/>
[in] Ponteiro para um [classe CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md) objeto que contém os parâmetros de exibição.

### <a name="remarks"></a>Comentários

Sempre que a dica de ferramenta é exibida, ela é desenhada usando as cores e estilos visuais que *pParams* especifica. O valor de *pParams* é armazenado no membro protegido `m_Params`, que pode ser acessado por uma classe derivada que substitui [CMFCToolTipCtrl::OnDrawBorder](#ondrawborder), [CMFCToolTipCtrl: : OnDrawIcon](#ondrawicon), [CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel), [CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator), ou [CMFCToolTipCtrl::OnFillBackground](#onfillbackground)para manter a aparência especificada.

## <a name="see-also"></a>Consulte também

[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)<br/>
[Classe CTooltipManager](../../mfc/reference/ctooltipmanager-class.md)<br/>
[Classe CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)<br/>
[Classe CWinAppEx](../../mfc/reference/cwinappex-class.md)
