---
title: Estrutura AFX_GLOBAL_DATA | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::CleanUp
- AFXGLOBALS/AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawParentBackground
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawTextOnGlass
- AFXGLOBALS/AFX_GLOBAL_DATA::ExcludeTag
- AFXGLOBALS/AFX_GLOBAL_DATA::GetColor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetDirect2dFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetHandCursor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList3
- AFXGLOBALS/AFX_GLOBAL_DATA::GetNonClientMetrics
- AFXGLOBALS/AFX_GLOBAL_DATA::GetShellAutohideBars
- AFXGLOBALS/AFX_GLOBAL_DATA::GetTextHeight
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWICFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWriteFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
- AFXGLOBALS/AFX_GLOBAL_DATA::Is32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
- AFXGLOBALS/AFX_GLOBAL_DATA::IsDwmCompositionEnabled
- AFXGLOBALS/AFX_GLOBAL_DATA::IsHighContrastMode
- AFXGLOBALS/AFX_GLOBAL_DATA::OnSettingChange
- AFXGLOBALS/AFX_GLOBAL_DATA::RegisterWindowClass
- AFXGLOBALS/AFX_GLOBAL_DATA::ReleaseTaskBarRefs
- AFXGLOBALS/AFX_GLOBAL_DATA::Resume
- AFXGLOBALS/AFX_GLOBAL_DATA::SetLayeredAttrib
- AFXGLOBALS/AFX_GLOBAL_DATA::SetMenuFont
- AFXGLOBALS/AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateFonts
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateSysColors
- AFXGLOBALS/AFX_GLOBAL_DATA::EnableAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsWindows7
- AFXGLOBALS/AFX_GLOBAL_DATA::clrActiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::clrInactiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseSystemFont
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurHand
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretch
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretchVert
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hiconTool
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessDock
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
dev_langs:
- C++
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 935a92beb49d26240aa63f5cfbd4adc9f22d06e8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078005"
---
# <a name="afxglobaldata-structure"></a>Estrutura AFX_GLOBAL_DATA

O `AFX_GLOBAL_DATA` estrutura contém campos e métodos que são usados para gerenciar a estrutura ou personalizar a aparência e comportamento do seu aplicativo.

## <a name="syntax"></a>Sintaxe

```
struct AFX_GLOBAL_DATA
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|Constrói um `AFX_GLOBAL_DATA` estrutura.|
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|Destruidor.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[AFX_GLOBAL_DATA::CleanUp](#cleanup)|Libera os recursos são alocados por do framework, como pincéis, fontes e DLLs.|
|[AFX_GLOBAL_DATA::D2D1MakeRotateMatrix](#d2d1makerotatematrix)|Cria uma transformação de rotação gira em um ângulo especificado em torno de um ponto especificado.|
|[AFX_GLOBAL_DATA::DrawParentBackground](#drawparentbackground)|Desenha a tela de fundo do pai de um controle na área especificada.|
|[AFX_GLOBAL_DATA::DrawTextOnGlass](#drawtextonglass)|Desenha o texto especificado no estilo visual do tema especificado.|
|[AFX_GLOBAL_DATA::ExcludeTag](#excludetag)|Remove o par de marca XML especificado de um buffer especificado.|
|[AFX_GLOBAL_DATA::GetColor](#getcolor)|Recupera a cor atual do elemento de interface do usuário especificado.|
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|Retorna um ponteiro para o `ID2D1Factory` interface que é armazenado em dados globais. Se a interface não é inicializada, ele é criado e tem os parâmetros padrão.|
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|Recupera o cursor predefinido que lembra uma mão e cujo identificador é `IDC_HAND`.|
|[AFX_GLOBAL_DATA::GetITaskbarList](#getitaskbarlist)|Cria e armazena os dados globais um ponteiro para interface ITaskBarList.|
|[AFX_GLOBAL_DATA::GetITaskbarList3](#getitaskbarlist3)|Cria e armazena os dados globais um ponteiro para interface ITaskBarList3.|
|[AFX_GLOBAL_DATA::GetNonClientMetrics](#getnonclientmetrics)|Recupera as métricas associadas a área não cliente do windows não minimizadas.|
|[AFX_GLOBAL_DATA::GetShellAutohideBars](#getshellautohidebars)|Determina a posições de auto Shell ocultar barras.|
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|Recupera a altura dos caracteres de texto na fonte atual.|
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|Retorna um ponteiro para o `IWICImagingFactory` interface que é armazenado em dados globais. Se a interface não é inicializada, ele é criado e tem os parâmetros padrão.|
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|Retorna um ponteiro para o `IDWriteFactory` interface que é armazenado em dados globais. Se a interface não é inicializada, ele é criado e tem os parâmetros padrão.|
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Inicializa `D2D`, `DirectWrite`, e `WIC` fábricas. Chame esse método antes da janela principal é inicializada.|
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|Indica se os ícones predefinidos de 32 bits são compatíveis.|
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Determina se o `D2D` foi inicializado.|
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Fornece uma maneira simples para chamar o Windows [DwmIsCompositionEnabled](/windows/desktop/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) método.|
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|Indica se as imagens são exibidas no momento em alto contraste.|
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|Detecta o estado atual da animação de menus e a recursos de ocultar automaticamente na barra de tarefas da área de trabalho.|
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|Registra a classe de janela MFC especificada.|
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|Libera as interfaces obtidas por meio de métodos GetITaskbarList e GetITaskbarList3.|
|[AFX_GLOBAL_DATA::resume](#resume)|Reinicializa a ponteiros de função interna que pode acessar os métodos que dão suporte ao Windows [temas e estilos visuais](/windows/desktop/Controls/visual-styles-overview).|
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Fornece uma maneira simples para chamar o Windows [SetLayeredWindowAttributes](/windows/desktop/api/winuser/nf-winuser-setlayeredwindowattributes) método.|
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|Cria a fonte lógica especificada.|
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|Cria e inicializa um objeto de item do Shell de um nome de análise.|
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|Reintializes fontes lógicas que são usadas pela estrutura.|
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|Inicializa as cores, profundidade de cores, pincéis, canetas e imagens que são usadas pela estrutura.|

### <a name="protected-methods"></a>Métodos Protegidos

|Nome|Descrição|
|----------|-----------------|
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|Habilita ou desabilita o suporte do Microsoft Active Accessibility. Acessibilidade ativa oferece métodos confiáveis para expor informações sobre os elementos de interface do usuário.|
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|Indica se o suporte do Microsoft Active Accessibility está habilitado.|
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|Indica se o sistema operacional dá suporte a janelas em camadas.|

### <a name="data-members"></a>Membros de Dados

|Nome|Descrição|
|----------|-----------------|
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|Indica se o sistema operacional atual oferece suporte a combinação alfa.|
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|Indica se o aplicativo está sendo executado no sistema operacional do Windows 7 ou superior|
|[AFX_GLOBAL_DATA::clrActiveCaptionGradient](#clractivecaptiongradient)|Especifica a cor do gradiente de legenda ativa. Geralmente usado para painéis de encaixe.|
|[AFX_GLOBAL_DATA::clrInactiveCaptionGradient](#clrinactivecaptiongradient)|Especifica a cor do gradiente de legenda inativa de Active Directory. Geralmente usado para painéis de encaixe.|
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|Indica se a estrutura usa ícones de cores predefinidas de 32 bits ou ícones de uma resolução mais baixa.|
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|Indica se uma fonte de sistema é usada para menus, barras de ferramentas e faixas de opções.|
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|Armazena o identificador para o cursor de mão.|
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|Armazena o identificador para o cursor horizontal de ampliação.|
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|Armazena o identificador para o cursor de ampliação vertical.|
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|Armazena o identificador para o ícone de ferramenta.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|Especifica o deslocamento da barra de ferramentas AutoOcultar mais à esquerda para o lado esquerdo da barra de encaixe.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|Especifica o intervalo entre as barras de ferramentas de ocultar automaticamente.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|Especifica a espessura do quadro de arrastar que é usado para comunicar o estado encaixado.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|Especifica a espessura do quadro de arrastar que é usado para comunicar o estado flutuante.|

### <a name="remarks"></a>Comentários

A maioria dos dados no `AFX_GLOBAL_DATA` estrutura é inicializada quando o aplicativo for iniciado.

### <a name="inheritance-hierarchy"></a>Hierarquia de herança

`AFX_GLOBAL_DATA`

### <a name="requirements"></a>Requisitos

**Cabeçalho:** afxglobals. h

### <a name="see-also"></a>Consulte também

[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Estruturas, estilos, retornos de chamada e mapas de mensagem](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

## <a name="bisosalphablendingsupport"></a> AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport

Indica se o sistema operacional dá suporte a combinação alfa.

```
BOOL  bIsOSAlphaBlendingSupport;
```

### <a name="remarks"></a>Comentários

VERDADEIRO indica que há suporte para a combinação alfa; Caso contrário, FALSE.

## <a name="cleanup"></a> AFX_GLOBAL_DATA::CleanUp

Libera os recursos são alocados por do framework, como pincéis, fontes e DLLs.

```
void CleanUp();
```

## <a name="d2d1makerotatematrix"></a> AFX_GLOBAL_DATA::D2D1MakeRotateMatrix

Cria uma transformação de rotação gira em um ângulo especificado em torno de um ponto especificado.

```
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,
    D2D1_POINT_2F center,
    D2D1_MATRIX_3X2_F *matrix);
```

### <a name="parameters"></a>Parâmetros

*ângulo*<br/>
O ângulo da rotação no sentido horário, em graus.

*Centro*<br/>
O ponto sobre qual girar.

*matriz*<br/>
Quando este método retorna, contém a transformação de rotação de novo. Você deve alocar armazenamento para esse parâmetro.

### <a name="return-value"></a>Valor de retorno

Caso contrário, Retorna S_OK se for bem-sucedido ou um valor de erro.

## <a name="drawparentbackground"></a> AFX_GLOBAL_DATA::DrawParentBackground

Desenha a tela de fundo do pai de um controle na área especificada.

```
BOOL DrawParentBackground(
    CWnd* pWnd,
    CDC* pDC,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Parâmetros

*Apropriei*<br/>
[in] Ponteiro para uma janela do controle.

*pDC*<br/>
[in] Ponteiro para um contexto de dispositivo.

*lpRect*<br/>
[in] Ponteiro para um retângulo que delimita a área na qual desenhar. O valor padrão é NULL.

### <a name="return-value"></a>Valor de retorno

TRUE se esse método for bem-sucedida; Caso contrário, FALSE.

## <a name="drawtextonglass"></a> AFX_GLOBAL_DATA::DrawTextOnGlass

Desenha o texto especificado no estilo visual do tema especificado.

```
BOOL DrawTextOnGlass(
    HTHEME hTheme,
    CDC* pDC,
    int iPartId,
    int iStateId,
    CString strText,
    CRect rect,
    DWORD dwFlags,
    int nGlowSize = 0,
    COLORREF clrText = (COLORREF)-1);
```

### <a name="parameters"></a>Parâmetros

*hTheme*<br/>
[in] Identificador para os dados de tema de uma janela ou NULL. A estrutura usa o tema especificado para desenhar o texto se esse parâmetro não for nulo e temas são suportados. Caso contrário, o framework não usa um tema para desenhar o texto.

Use o [OpenThemeData](/windows/desktop/api/uxtheme/nf-uxtheme-openthemedata) método para criar um HTHEME.

*pDC*<br/>
[in] Ponteiro para um contexto de dispositivo.

*iPartId*<br/>
[in] A parte do controle que tem a aparência do texto desejado. Para obter mais informações, consulte a coluna de partes da tabela no [partes e estados](https://msdn.microsoft.com/library/windows/desktop/bb773210). Se esse valor for 0, o texto é desenhado em uma fonte selecionada no contexto de dispositivo ou a fonte padrão.

*iStateId*<br/>
[in] O estado do controle que tem a aparência do texto desejado. Para obter mais informações, consulte a coluna de estados da tabela no [partes e estados](https://msdn.microsoft.com/library/windows/desktop/bb773210).

*strText*<br/>
[in] O texto a ser desenhado.

*Rect*<br/>
[in] O limite da área na qual o texto especificado é desenhado.

*dwFlags*<br/>
[in] Uma combinação bit a bit (OR) de sinalizadores que especificam como o texto especificado é desenhado.

Se o *hTheme* parâmetro é `NULL` ou se os temas não são tem suporte e habilitados, o *nFormat* parâmetro do [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext) método descreve válidos sinalizadores. Se houver suporte para temas, o *dwFlags* parâmetro do [DrawThemeTextEx](/windows/desktop/api/uxtheme/nf-uxtheme-drawthemetextex) método descreve os sinalizadores válidos.

*nGlowSize*<br/>
[in] O tamanho de um efeito de brilho é desenhado no plano de fundo antes de desenhar o texto especificado. O valor padrão é 0.

*clrText*<br/>
[in] A cor em que o texto especificado é desenhado. O valor padrão é a cor padrão.

### <a name="return-value"></a>Valor de retorno

TRUE se um tema é usado para desenhar o texto especificado; Caso contrário, FALSE.

### <a name="remarks"></a>Comentários

Um tema define o estilo visual de um aplicativo. Um tema não é usado para desenhar o texto, se o *hTheme* parâmetro for NULL, ou se o [DrawThemeTextEx](/windows/desktop/api/uxtheme/nf-uxtheme-drawthemetextex) não há suporte para o método, ou se [Gerenciador de janelas da área de trabalho](/windows/desktop/dwm/dwm-overview) composição está desabilitado.

### <a name="see-also"></a>Consulte também

[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[COLORREF](/windows/desktop/gdi/colorref)<br/>
[Partes e Estados](https://msdn.microsoft.com/library/windows/desktop/bb773210)<br/>
[CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)<br/>
[DrawThemeTextEx](/windows/desktop/api/uxtheme/nf-uxtheme-drawthemetextex)<br/>
[Gerenciador de janelas da área de trabalho](/windows/desktop/dwm/dwm-overview)<br/>
[Ativar e controlar a composição do DWM](/windows/desktop/dwm/composition-ovw)

## <a name="enableaccessibilitysupport"></a> AFX_GLOBAL_DATA::EnableAccessibilitySupport

Habilita ou desabilita o suporte do Microsoft Active Accessibility.

```
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parâmetros

*bAtivar*<br/>
[in] TRUE para habilitar o suporte de acessibilidade; FALSE para desabilitar o suporte de acessibilidade. O valor padrão é TRUE.

### <a name="remarks"></a>Comentários

Acessibilidade ativa é uma tecnologia baseada em COM que melhora os maneira como os programas e o trabalho de sistema operacional do Windows junto com produtos de tecnologia assistencial. Ele fornece métodos confiáveis para expor informações sobre os elementos de interface do usuário. No entanto, um modelo de acessibilidade mais recente, chamado de automação de interface do usuário da Microsoft agora está disponível. Para obter uma comparação das duas tecnologias, consulte [automação de interface do usuário e o Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).

Use o [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport) método para determinar se o suporte do Microsoft Active Accessibility está habilitado.

### <a name="see-also"></a>Consulte também

[Automação de interface do usuário e Acessibilidade Ativa da Microsoft](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)<br/>
[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)

## <a name="excludetag"></a> AFX_GLOBAL_DATA::ExcludeTag

Remove o par de marca XML especificado de um buffer especificado.

```
BOOL ExcludeTag(
    CString& strBuffer,
    LPCTSTR lpszTag,
    CString& strTag,
    BOOL bIsCharsList = FALSE);
```

### <a name="parameters"></a>Parâmetros

*strBuffer*<br/>
[in] Um buffer de texto.

*lpszTag*<br/>
[in] O nome de um par de abertura e fechamento de marcas XML.

*strTag*<br/>
[out] Quando este método retorna, o *strTag* parâmetro contém o texto que está entre a abertura e fechamento XML marcas que são nomeadas, o *lpszTag* parâmetro. Nenhum espaço em branco à esquerda ou à direita é retirado do resultado.

*bIsCharsList*<br/>
[in] True para símbolos de converter para caracteres de escape na *strTag* parâmetro em caracteres de escape real; FALSO para não realizar a conversão. O valor padrão é FALSE. Para obter mais informações, consulte Comentários.

### <a name="return-value"></a>Valor de retorno

TRUE se esse método for bem-sucedida; Caso contrário, FALSE.

### <a name="remarks"></a>Comentários

Um par de marca XML consiste em chamada de abertura e fechamento de marcas que indicam o início e término de uma sequência de texto no buffer especificado. O *strBuffer* parâmetro especifica o buffer e o *lpszTag* parâmetro especifica o nome das marcas XML.

Use os símbolos na tabela a seguir para codificar um conjunto de caracteres de escape no buffer especificado. Especifique TRUE para o *bIsCharsList* parâmetro a converter os símbolos na *strTag* parâmetro em caracteres de escape real. A tabela a seguir usa o [t ()](../../c-runtime-library/data-type-mappings.md) macro para especificar o símbolo e cadeias de caracteres de escape.

|Símbolo|Caractere de escape|
|------------|----------------------|
|T ("\\\t")|_T("\t")|
|T ("\\\n")|_T("\n")|
|T ("\\\r")|_T("\r")|
|T ("\\\b")|_T("\b")|
|_T("LT")|T ("\<")|
|_T("GT")|_T("&GT;")|
|_T("AMP")|_T("&AMP;")|

## <a name="getcolor"></a> AFX_GLOBAL_DATA::GetColor

Recupera a cor atual do elemento de interface do usuário especificado.

```
COLORREF GetColor(int nColor);
```

### <a name="parameters"></a>Parâmetros

*nColor*<br/>
[in] Um valor que especifica um elemento de interface do usuário cuja cor é recuperado. Para obter uma lista de valores válidos, consulte o *nIndex* parâmetro do [GetSysColor](/windows/desktop/api/winuser/nf-winuser-getsyscolor) método.

### <a name="return-value"></a>Valor de retorno

O valor de cor RGB do elemento de interface do usuário especificado. Para obter mais informações, consulte Comentários.

### <a name="remarks"></a>Comentários

Se o *nColor* parâmetro está fora do intervalo, o valor retornado será zero. Como zero é também um valor válido de RGB, é possível usar esse método para determinar se uma cor do sistema é compatível com o sistema operacional atual. Em vez disso, use o [GetSysColorBrush](/windows/desktop/api/winuser/nf-winuser-getsyscolorbrush) método, que retorna NULL se não há suporte para a cor.

### <a name="see-also"></a>Consulte também

[Função GetSysColor](/windows/desktop/api/winuser/nf-winuser-getsyscolor)<br/>
[COLORREF](/windows/desktop/gdi/colorref)<br/>
[GetSysColorBrush](/windows/desktop/api/winuser/nf-winuser-getsyscolorbrush)

## <a name="getdirect2dfactory"></a> AFX_GLOBAL_DATA::GetDirect2dFactory

Retorna um ponteiro para a interface ID2D1Factory armazenado em dados globais. Se a interface não é inicializada, ele é criado e tem os parâmetros padrão.

```
ID2D1Factory* GetDirect2dFactory();
```

### <a name="return-value"></a>Valor de retorno

Um ponteiro para interface ID2D1Factory se a criação de uma fábrica for bem-sucedida, ou nulo se a falha na criação ou o sistema operacional atual não tem o suporte D2D.

## <a name="gethandcursor"></a>  AFX_GLOBAL_DATA::GetHandCursor

Recupera o cursor predefinido que lembra uma mão e cujo identificador é IDC_HAND.

```
HCURSOR GetHandCursor();
```

### <a name="return-value"></a>Valor de retorno

O identificador do cursor de mão.

## <a name="getnonclientmetrics"></a> AFX_GLOBAL_DATA::GetNonClientMetrics

Recupera as métricas associadas a área não cliente do windows não minimizadas.

```
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```

### <a name="parameters"></a>Parâmetros

*Informações de*<br/>
[no, out] Um [NONCLIENTMETRICS](https://msdn.microsoft.com/library/windows/desktop/ff729175) estrutura que contém as métricas escalonáveis associadas com a área não cliente de uma janela não minimizada.

### <a name="return-value"></a>Valor de retorno

TRUE se este método for bem-sucedido; Caso contrário, FALSE.

### <a name="see-also"></a>Consulte também

[Estrutura NONCLIENTMETRICS](https://msdn.microsoft.com/library/windows/desktop/ff729175)

## <a name="gettextheight"></a> AFX_GLOBAL_DATA::GetTextHeight

Recupera a altura dos caracteres de texto na fonte atual.

```
int GetTextHeight(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parâmetros

*bHorz*<br/>
[in] TRUE para recuperar a altura dos caracteres quando o texto é executado horizontalmente; FALSE para recuperar a altura dos caracteres quando o texto é executado verticalmente. O valor padrão é TRUE.

### <a name="return-value"></a>Valor de retorno

A altura da fonte atual, que é medida da sua ascender até seu descendente.

## <a name="getwicfactory"></a> AFX_GLOBAL_DATA::GetWICFactory

Retorna um ponteiro para uma interface IWICImagingFactory armazenado em dados globais. Se a interface não é inicializada, ele é criado e tem os parâmetros padrão.

```
IWICImagingFactory* GetWICFactory();
```

### <a name="return-value"></a>Valor de retorno

Um ponteiro para uma interface IWICImagingFactory se a criação de uma fábrica for bem-sucedida, ou nulo se a falha na criação ou o sistema operacional atual não tem suporte do WIC.

## <a name="getwritefactory"></a> AFX_GLOBAL_DATA::GetWriteFactory

Retorna um ponteiro para a interface IDWriteFactory armazenado em dados globais. Se a interface não é inicializada, ele é criado e tem os parâmetros padrão.

```
IDWriteFactory* GetWriteFactory();
```

### <a name="return-value"></a>Valor de retorno

Um ponteiro para interface IDWriteFactory se a criação de uma fábrica for bem-sucedida, ou nulo se a falha na criação ou o sistema operacional atual não tem suporte do DirectWrite.

## <a name="initd2d"></a> AFX_GLOBAL_DATA::InitD2D

Inicializa as fábricas D2D, DirectWrite e WIC. Chame esse método antes da janela principal é inicializada.

```
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Parâmetros

*d2dFactoryType*<br/>
O modelo de threading de fábrica D2D e os recursos que ele cria.

*writeFactoryType*<br/>
Um valor que especifica se o objeto de fábrica de gravação será compartilhado ou isolado

### <a name="return-value"></a>Valor de retorno

Retornará TRUE se as fábricas foram intilalizrd, FALSO - caso contrário

## <a name="is32biticons"></a> AFX_GLOBAL_DATA::Is32BitIcons

Indica se os ícones predefinidos de 32 bits são compatíveis.

```
BOOL Is32BitIcons() const;

```

### <a name="return-value"></a>Valor de retorno

TRUE se os ícones predefinidos de 32 bits têm suporte; Caso contrário, FALSE.

### <a name="remarks"></a>Comentários

Esse método retornará TRUE se o framework oferece suporte a ícones internos de 32 bits, se o sistema operacional dá suporte a 16 bits por pixel ou mais, e se as imagens não são exibidas em alto contraste.

## <a name="isaccessibilitysupport"></a> AFX_GLOBAL_DATA::IsAccessibilitySupport

Indica se o suporte do Microsoft Active Accessibility está habilitado.

```
BOOL IsAccessibilitySupport() const;
```

### <a name="return-value"></a>Valor de retorno

TRUE se o suporte à acessibilidade estiver habilitado; Caso contrário, FALSE.

### <a name="remarks"></a>Comentários

Acessibilidade ativa da Microsoft foi a solução anterior para tornar aplicativos acessíveis. Automação de interface do usuário da Microsoft é o novo modelo de acessibilidade para o Microsoft Windows e se destina a atender às necessidades de produtos de tecnologia assistencial e ferramentas de teste automatizado.

Use o [AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport) método para habilitar ou desabilitar o suporte à acessibilidade ativa.

### <a name="see-also"></a>Consulte também

[Automação de interface do usuário e Acessibilidade Ativa da Microsoft](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)

## <a name="isd2dinitialized"></a> AFX_GLOBAL_DATA::IsD2DInitialized

Determina se o D2D foi inicializado

```
BOOL IsD2DInitialized() const;
```

### <a name="return-value"></a>Valor de retorno

TRUE se D2D foi inicializado; Caso contrário, FALSE.

## <a name="isdwmcompositionenabled"></a> AFX_GLOBAL_DATA::IsDwmCompositionEnabled

Fornece uma maneira simples para chamar o Windows [DwmIsCompositionEnabled](/windows/desktop/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) método.

```
BOOL IsDwmCompositionEnabled();
```

### <a name="return-value"></a>Valor de retorno

TRUE se [Gerenciador de janelas da área de trabalho](/windows/desktop/dwm/dwm-overview) composição é habilitado; caso contrário, FALSE.

### <a name="see-also"></a>Consulte também

[Gerenciador de janelas da área de trabalho](/windows/desktop/dwm/dwm-overview)<br/>
[Ativar e controlar a composição do DWM](/windows/desktop/dwm/composition-ovw)

## <a name="ishighcontrastmode"></a> AFX_GLOBAL_DATA::IsHighContrastMode

Indica se as imagens são exibidas no momento em alto contraste.
```
BOOL IsHighContrastMode() const;
```

### <a name="return-value"></a>Valor de retorno

TRUE se as imagens são exibidas no momento no modo de alto contraste preto ou branco; Caso contrário, FALSE.

### <a name="remarks"></a>Comentários

No modo de alto contraste preto, bordas opostas a luz são brancas e o plano de fundo é preto. No modo de alto contraste branca, bordas opostas a luz são pretas e a tela de fundo é branca.

## <a name="iswindowslayersupportavailable"></a> AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable

Indica se o sistema operacional dá suporte a janelas em camadas.

```
BOOL IsWindowsLayerSupportAvailable() const;
```

### <a name="return-value"></a>Valor de retorno

TRUE se as janelas em camadas têm suporte; Caso contrário, FALSE.

### <a name="remarks"></a>Comentários

Se houver suporte para janelas em camadas, *inteligentes de encaixe* marcadores usam as janelas em camadas.

## <a name="m_busebuiltin32biticons"></a> AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons

Indica se a estrutura usa ícones de cores predefinidas de 32 bits ou ícones de uma resolução mais baixa.

```
BOOL  m_bUseBuiltIn32BitIcons;
```

### <a name="remarks"></a>Comentários

O valor TRUE Especifica que a estrutura usar ícones de cores de 32 bits; FALSE Especifica os ícones de resolução mais baixos. O `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` construtor inicializa esse membro como TRUE.

Esse membro deve ser definido na inicialização do aplicativo.

## <a name="m_busesystemfont"></a> AFX_GLOBAL_DATA::m_bUseSystemFont

Indica se uma fonte de sistema é usada para menus, barras de ferramentas e faixas de opções.

```
BOOL m_bUseSystemFont;
```

### <a name="remarks"></a>Comentários

O valor TRUE especifica para usar uma fonte de sistema; Caso contrário, FALSE. O `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` construtor inicializa esse membro como FALSE.

Teste este membro não é a única maneira para a estrutura determinar a fonte para usar. O `AFX_GLOBAL_DATA::UpdateFonts` método também testa fontes padrão e alternativos para determinar quais estilos visuais estão disponíveis a ser aplicado a menus, barras de ferramentas e faixas de opções.

## <a name="m_hcurhand"></a> AFX_GLOBAL_DATA::m_hcurHand

Armazena o identificador para o cursor de mão.

```
HCURSOR m_hcurHand;
```

## <a name="m_hcurstretch"></a> AFX_GLOBAL_DATA::m_hcurStretch

Armazena o identificador para o cursor horizontal de ampliação.

```
HCURSOR m_hcurStretch;
```

## <a name="m_hcurstretchvert"></a> AFX_GLOBAL_DATA::m_hcurStretchVert

Armazena o identificador para o cursor de ampliação vertical.

```
HCURSOR m_hcurStretchVert;
```

## <a name="m_hicontool"></a> AFX_GLOBAL_DATA::m_hiconTool

Armazena o identificador para o ícone de ferramenta.

```
HICON m_hiconTool;
```

## <a name="m_nautohidetoolbarmargin"></a> AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin

Especifica o deslocamento da barra de ferramentas AutoOcultar mais à esquerda para o lado esquerdo da barra de encaixe.

```
int  m_nAutoHideToolBarMargin;
```

### <a name="remarks"></a>Comentários

O `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` construtor inicializa este membro para 4 pixels.

## <a name="m_nautohidetoolbarspacing"></a> AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing

Especifica o intervalo entre as barras de ferramentas de ocultar automaticamente.

```
int   m_nAutoHideToolBarSpacing;
```

### <a name="remarks"></a>Comentários

O `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` construtor inicializa este membro para 14 pixels.

## <a name="m_ndragframethicknessdock"></a> AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

Especifica a espessura do quadro arrastar que é usado para indicar o estado de ancoramento.

```
int  m_nDragFrameThicknessDock;
```

### <a name="remarks"></a>Comentários

O `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` construtor inicializa este membro para 3 pixels.

## <a name="m_ndragframethicknessfloat"></a> AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat

Especifica a espessura do quadro de arrastar que é usado para indicar o estado flutuante.

```
int  m_nDragFrameThicknessFloat;
```

### <a name="remarks"></a>Comentários

O `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` construtor inicializa este membro para 4 pixels.

## <a name="onsettingchange"></a> AFX_GLOBAL_DATA::OnSettingChange

Detecta o estado atual da animação de menus e a recursos de ocultar automaticamente na barra de tarefas da área de trabalho.

```
void OnSettingChange();
```

### <a name="remarks"></a>Comentários

Esse método define variáveis de estrutura para o estado de determinados atributos de área de trabalho do usuário. Este método detecta o estado atual da animação de menus, esmaecimento do menu e barra ocultar automaticamente recursos de tarefas.

## <a name="registerwindowclass"></a> AFX_GLOBAL_DATA::RegisterWindowClass

Registra a classe de janela MFC especificada.

```
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```

### <a name="parameters"></a>Parâmetros

*lpszClassNamePrefix*<br/>
[in] O nome da classe de janela para registrar.

### <a name="return-value"></a>Valor de retorno

O nome qualificado da classe registrado se esse método for bem-sucedida; Caso contrário, uma [exceção de recurso](exception-processing.md#afxthrowresourceexception).

### <a name="remarks"></a>Comentários

O valor retornado é uma lista delimitada por dois-pontos do *lpszClassNamePrefix* parâmetro de cadeia de caracteres e as representações de texto hexadecimal das alças da instância atual do aplicativo; o cursor de aplicativo, que é a seta cursor cujo identificador é IDC_ARROW; e o pincel do plano de fundo. Para obter mais informações sobre como registrar as classes de janela MFC, consulte [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass).

### <a name="see-also"></a>Consulte também

[AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass)<br/>
[AfxThrowResourceException](../../mfc/reference/exception-processing.md#afxthrowresourceexception)

## <a name="resume"></a> AFX_GLOBAL_DATA::resume

Reinicializa os ponteiros de função interna que pode acessar os métodos que dão suporte a temas do Windows e os estilos visuais.

```
BOOL Resume();
```

### <a name="return-value"></a>Valor de retorno

TRUE se este método for bem-sucedido; Caso contrário, FALSE. No modo de depuração, esse método declara se este método não for bem-sucedida.

### <a name="remarks"></a>Comentários

Esse método é chamado quando o framework recebe o [WM_POWERBROADCAST](/windows/desktop/Power/wm-powerbroadcast) mensagem.

## <a name="setlayeredattrib"></a> AFX_GLOBAL_DATA::SetLayeredAttrib

Fornece uma maneira simples para chamar o Windows [SetLayeredWindowAttributes](/windows/desktop/api/winuser/nf-winuser-setlayeredwindowattributes) método.

```
BOOL SetLayeredAttrib(
    HWND hwnd,
    COLORREF crKey,
    BYTE bAlpha,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parâmetros

*HWND*<br/>
[in] Identificador da janela em camadas.

*crKey*<br/>
[in] A cor de transparência da chave que o [Gerenciador de janelas da área de trabalho](/windows/desktop/dwm/dwm-overview) usa para compor a janela em camadas.

*bAlpha*<br/>
[in] O valor alfa é usado para descrever a opacidade da janela em camadas.

*dwFlags*<br/>
[in] Uma combinação bit a bit (OR) de sinalizadores que especificam quais parâmetros de método para usar. Especifique LWA_COLORKEY para usar o *crKey* parâmetro como a cor de transparência. Especifique LWA_ALPHA para usar o *bAlpha* parâmetro para determinar a opacidade da janela em camadas.

### <a name="return-value"></a>Valor de retorno

TRUE se este método for bem-sucedido; Caso contrário, FALSE.

### <a name="see-also"></a>Consulte também

[COLORREF](/windows/desktop/gdi/colorref)<br/>
[SetLayeredWindowAttributes](/windows/desktop/api/winuser/nf-winuser-setlayeredwindowattributes)

## <a name="setmenufont"></a> AFX_GLOBAL_DATA::SetMenuFont

Cria a fonte lógica especificada.

```
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz);
```

### <a name="parameters"></a>Parâmetros

*lpLogFont*<br/>
[in] Ponteiro para uma estrutura que contém os atributos de uma fonte.

*bHorz*<br/>
[in] TRUE para especificar que o texto é executado horizontalmente; FALSO para especificar que o texto é executado verticalmente.

### <a name="return-value"></a>Valor de retorno

TRUE se este método for bem-sucedido; Caso contrário, FALSE. No modo de depuração, esse método declara se este método não for bem-sucedida.

### <a name="remarks"></a>Comentários

Esse método cria uma fonte normal horizontal, uma fonte sublinhado, e uma fonte em negrito que é usado em default itens de menu. Opcionalmente, esse método cria uma fonte vertical regular. Para obter mais informações sobre fontes de lógicas, consulte [CFont::CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).

## <a name="updatefonts"></a> AFX_GLOBAL_DATA::UpdateFonts

Reintializes fontes lógicas que são usadas pela estrutura.

```
void UpdateFonts();
```

### <a name="remarks"></a>Comentários

Para obter mais informações sobre fontes de lógicas, consulte `CFont::CreateFontIndirect`.

## <a name="updatesyscolors"></a> AFX_GLOBAL_DATA::UpdateSysColors

Inicializa as cores, profundidade de cores, pincéis, canetas e imagens que são usadas pela estrutura.

```
void UpdateSysColors();
```

## <a name="biswindows7"></a> AFX_GLOBAL_DATA::bIsWindows7

Indica se o aplicativo está sendo executado no Windows 7 ou superior.

```
BOOL bIsWindows7;
```

## <a name="clractivecaptiongradient"></a> AFX_GLOBAL_DATA::clrActiveCaptionGradient

Especifica a cor do gradiente da legenda do Active Directory. Geralmente usado para painéis de encaixe.

```
COLORREF clrActiveCaptionGradient;
```

## <a name="clrinactivecaptiongradient"></a> AFX_GLOBAL_DATA::clrInactiveCaptionGradient

Especifica a cor do gradiente da legenda inativa. Geralmente usado para painéis de encaixe.

```
COLORREF clrInactiveCaptionGradient;
```

## <a name="getitaskbarlist"></a> AFX_GLOBAL_DATA::GetITaskbarList

Cria e armazena os dados globais em um ponteiro para o `ITaskBarList` interface.

```
ITaskbarList *GetITaskbarList();
```

### <a name="return-value"></a>Valor de retorno

Um ponteiro para o `ITaskbarList` interface se a criação de uma barra de objeto da lista de tarefas for bem-sucedida; NULL se a criação falhar ou se o sistema operacional atual é menor que o Windows 7.

## <a name="getitaskbarlist3"></a> AFX_GLOBAL_DATA::GetITaskbarList3

Cria e armazena os dados globais em um ponteiro para o `ITaskBarList3` interface.

```
ITaskbarList3 *GetITaskbarList3();
```

### <a name="return-value"></a>Valor de retorno

Um ponteiro para o `ITaskbarList3` interface se a criação de uma barra de objeto da lista de tarefas for bem-sucedida; NULL se a criação falhar ou se o sistema operacional atual é menor que o Windows 7.

## <a name="getshellautohidebars"></a> AFX_GLOBAL_DATA::GetShellAutohideBars

Determina a posições de auto Shell ocultar barras.

```
int GetShellAutohideBars();
```

### <a name="return-value"></a>Valor de retorno

Um valor inteiro com codificado sinalizadores que especificam as posições de auto ocultar barras. Pode combinar os seguintes valores: AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.

## <a name="releasetaskbarrefs"></a> AFX_GLOBAL_DATA::ReleaseTaskBarRefs

Libera as interfaces obtidas por meio de `GetITaskbarList` e `GetITaskbarList3` métodos.

```
void ReleaseTaskBarRefs();
```

## <a name="shellcreateitemfromparsingname"></a> AFX_GLOBAL_DATA::ShellCreateItemFromParsingName

Cria e inicializa um objeto de item do Shell de um nome de análise.

```
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,
    IBindCtx *pbc,
    REFIID riid,
    void **ppv);
```

### <a name="parameters"></a>Parâmetros

*pszPath*<br/>
[in] Um ponteiro para um nome de exibição.

*PBC*<br/>
Um ponteiro para um contexto de associação que controla a operação de análise.

*riid*<br/>
Uma referência a uma ID de interface.

*ppv*<br/>
[out] Quando essa função retorna, contém o ponteiro de interface solicitado no *riid*. Isso geralmente será `IShellItem` ou `IShellItem2`.

### <a name="return-value"></a>Valor de retorno

Retorna S_OK se bem-sucedido; um valor de erro caso contrário.

