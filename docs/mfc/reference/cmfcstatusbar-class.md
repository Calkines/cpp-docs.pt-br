---
title: Classe CMFCStatusBar | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar::CalcFixedLayout
- AFXSTATUSBAR/CMFCStatusBar::CommandToIndex
- AFXSTATUSBAR/CMFCStatusBar::Create
- AFXSTATUSBAR/CMFCStatusBar::CreateEx
- AFXSTATUSBAR/CMFCStatusBar::DoesAllowDynInsertBefore
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneDoubleClick
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneProgressBar
- AFXSTATUSBAR/CMFCStatusBar::GetCount
- AFXSTATUSBAR/CMFCStatusBar::GetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetItemID
- AFXSTATUSBAR/CMFCStatusBar::GetItemRect
- AFXSTATUSBAR/CMFCStatusBar::GetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::GetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::GetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::GetPaneText
- AFXSTATUSBAR/CMFCStatusBar::GetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::GetTipText
- AFXSTATUSBAR/CMFCStatusBar::InvalidatePaneContent
- AFXSTATUSBAR/CMFCStatusBar::PreCreateWindow
- AFXSTATUSBAR/CMFCStatusBar::SetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::SetIndicators
- AFXSTATUSBAR/CMFCStatusBar::SetPaneAnimation
- AFXSTATUSBAR/CMFCStatusBar::SetPaneBackgroundColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneIcon
- AFXSTATUSBAR/CMFCStatusBar::SetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::SetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::SetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::SetPaneText
- AFXSTATUSBAR/CMFCStatusBar::SetPaneTextColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::SetTipText
- AFXSTATUSBAR/CMFCStatusBar::OnDrawPane
dev_langs:
- C++
helpviewer_keywords:
- CMFCStatusBar class
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
caps.latest.revision: 36
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 20881637d74bafffbcf2e0c3dcd1cc98e173aa07
ms.lasthandoff: 02/25/2017

---
# <a name="cmfcstatusbar-class"></a>Classe CMFCStatusBar
O `CMFCStatusBar` classe implementa uma barra de status semelhante de `CStatusBar` classe. No entanto, o `CMFCStatusBar` classe tem recursos não oferecidos pelo `CStatusBar` classe, como a capacidade de exibir imagens, animações e barras de progresso; e a capacidade de responder passar o mouse clicar duas vezes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class CMFCStatusBar : public CPane  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-methods"></a>Métodos Públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CMFCStatusBar::CalcFixedLayout](#calcfixedlayout)|(Substitui [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CMFCStatusBar::CommandToIndex](#commandtoindex)||  
|[CMFCStatusBar::Create](#create)|Cria uma barra de controle e anexa-o para o [CPane](../../mfc/reference/cpane-class.md) objeto. (Substitui [CPane::Create](../../mfc/reference/cpane-class.md#create).)|  
|[CMFCStatusBar::CreateEx](#createex)|Cria uma barra de controle e anexa-o para o [CPane](../../mfc/reference/cpane-class.md) objeto. (Substitui [CPane::CreateEx](../../mfc/reference/cpane-class.md#createex).)|  
|[CMFCStatusBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Determina se outro painel pode ser inserido dinamicamente entre esse painel e o quadro principal. (Substitui [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|  
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|Habilita ou desabilita a manipulação de mouse clica duas vezes na barra de status.|  
|[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)|Exibe uma barra de progresso no painel especificado.|  
|[CMFCStatusBar::GetCount](#getcount)|Retorna o número de painéis na barra de status.|  
|[CMFCStatusBar::GetDrawExtendedArea](#getdrawextendedarea)||  
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||  
|[CMFCStatusBar::GetItemID](#getitemid)||  
|[CMFCStatusBar::GetItemRect](#getitemrect)||  
|[CMFCStatusBar::GetPaneInfo](#getpaneinfo)||  
|[CMFCStatusBar::GetPaneProgress](#getpaneprogress)||  
|[CMFCStatusBar::GetPaneStyle](#getpanestyle)|Retorna o estilo de painel. (Substitui [CBasePane::GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle).)|  
|[CMFCStatusBar::GetPaneText](#getpanetext)||  
|[CMFCStatusBar::GetPaneWidth](#getpanewidth)|Retorna a largura, em pixels, do painel especificado da barra de status.|  
|[CMFCStatusBar::GetTipText](#gettiptext)|Retorna o texto da dica de ferramenta do painel especificado da barra de status.|  
|[CMFCStatusBar::InvalidatePaneContent](#invalidatepanecontent)|Invalida o painel especificado e seu conteúdo é redesenhado.|  
|[CMFCStatusBar::PreCreateWindow](#precreatewindow)|Chamado pela estrutura antes da criação da janela do Windows anexada a esta `CWnd` objeto. (Substitui [CWnd::PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).)|  
|[CMFCStatusBar::SetDrawExtendedArea](#setdrawextendedarea)||  
|[CMFCStatusBar::SetIndicators](#setindicators)||  
|[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)|Atribui uma animação para o painel especificado.|  
|[CMFCStatusBar::SetPaneBackgroundColor](#setpanebackgroundcolor)|Define a cor de plano de fundo do painel especificado da barra de status.|  
|[CMFCStatusBar::SetPaneIcon](#setpaneicon)|Define o ícone de indicador para o painel da barra de status especificado.|  
|[CMFCStatusBar::SetPaneInfo](#setpaneinfo)||  
|[CMFCStatusBar::SetPaneProgress](#setpaneprogress)|Define o progresso atual da barra de progresso do painel especificado da barra de status.|  
|[CMFCStatusBar::SetPaneStyle](#setpanestyle)|Define o estilo do painel. (Substitui [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).)|  
|[CMFCStatusBar::SetPaneText](#setpanetext)||  
|[CMFCStatusBar::SetPaneTextColor](#setpanetextcolor)|Define a cor do texto do painel especificado da barra de status.|  
|[CMFCStatusBar::SetPaneWidth](#setpanewidth)|Define a largura em pixels do painel especificado da barra de status.|  
|[CMFCStatusBar::SetTipText](#settiptext)|Define o texto de dica de ferramenta do painel especificado da barra de status.|  
  
### <a name="protected-methods"></a>Métodos Protegidos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CMFCStatusBar::OnDrawPane](#ondrawpane)|Chamado pela estrutura quando ele redesenha o painel da barra de status.|  
  
## <a name="remarks"></a>Comentários  
 O diagrama a seguir mostra uma figura da barra de status do [exemplo de demonstração da barra de Status](../../visual-cpp-samples.md) aplicativo.  
  
 ![Exemplo de CMFCStatusBar](../../mfc/reference/media/cmfcstatusbar.png "cmfcstatusbar")  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra as variáveis locais que o aplicativo usa para chamar vários métodos de `CMFCStatusBar` classe. Essas variáveis são declaradas em StatusBarDemoView.h. O quadro principal é declarado em MainFrm.h, o documento for declarado em StatusBarDemoDoc.h e o modo de exibição é declarado em StatusBarDemoView.h. Este trecho de código é parte do [exemplo de demonstração da barra de Status](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo n º&9;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como obter uma referência a `CMFCStatusBar` objeto introduzindo o `GetStatusBar` método MainFrm.h e, em seguida, chamar esse método a partir o `GetStatusBar` método StatusBarDemoView.h. Este trecho de código é parte do [exemplo de demonstração da barra de Status](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo&#7;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo n º&8;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como chamar vários métodos `CMFCStatusBar` classe StatusBarDemoView.cpp. As constantes são declaradas no MainFrm.h. O exemplo mostra como definir o ícone, defina o texto de dica de ferramenta do painel da barra de status, exibir uma barra de progresso no painel especificado, atribuir uma animação ao painel especificado, definir o texto e a largura do painel da barra de status e definir o indicador de progresso atual da barra de progresso para o painel da barra de status. Este trecho de código é parte do [exemplo de demonstração da barra de Status](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo n º&6;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo n º&1;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo n º&2;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo n º&3;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo n º&4;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo n º&5;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** afxstatusbar.h  
  
##  <a name="calcfixedlayout"></a>CMFCStatusBar::CalcFixedLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `bStretch`  
 [in] `bHorz`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="commandtoindex"></a>CMFCStatusBar::CommandToIndex  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIDFind`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="create"></a>CMFCStatusBar::Create  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pParentWnd`  
 [in] `dwStyle`  
 [in] `nID`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="createex"></a>CMFCStatusBar::CreateEx  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = 0,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pParentWnd`  
 [in] `dwCtrlStyle`  
 [in] `dwStyle`  
 [in] `nID`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="doesallowdyninsertbefore"></a>CMFCStatusBar::DoesAllowDynInsertBefore  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="enablepanedoubleclick"></a>CMFCStatusBar::EnablePaneDoubleClick  
 Habilita ou desabilita a manipulação de mouse clica duas vezes na barra de status.  
  
```  
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `bEnable`  
 Se `TRUE`, habilitar o processamento do mouse duas vezes. Caso contrário, desabilite o processamento do duplo clique do mouse.  
  
### <a name="remarks"></a>Comentários  
 Se a barra de status é habilitada para processar os cliques duplos, o Windows envia o `WM_COMMAND` notificação junto com uma ID de recurso para o proprietário da barra toda vez que o usuário clicar duas vezes no painel de barra de status de status.  
  
##  <a name="enablepaneprogressbar"></a>CMFCStatusBar::EnablePaneProgressBar  
 Exiba uma barra de progresso no painel especificado.  
  
```  
void EnablePaneProgressBar(
    int nIndex,  
    long nTotal=100,  
    BOOL bDisplayText=FALSE,  
    COLORREF clrBar=-1,  
    COLORREF clrBarDest=-1,  
    COLORREF clrProgressText=-1);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 Especifica o índice do painel cuja barra de progresso para habilitar.  
  
 [in] `nTotal`  
 Especifica o valor máximo para a barra de progresso.  
  
 [in] `bDisplayText`  
 Especifica se a barra de progresso deve exibir o valor atual do progresso.  
  
 [in] `clrBar`  
 Especifica a cor de plano de fundo da barra de progresso.  
  
 [in] `clrBarDest`  
 Especifica a cor secundária do plano de fundo de barra de progresso. Use um valor diferente de `clrBar` para preencher uma cor combinada em um gradiente.  
  
 [in] `clrProgressText`  
 Especifica a cor do texto da barra de progresso.  
  
### <a name="remarks"></a>Comentários  
 Se você quiser desabilitar a chamada de barra de progresso `EnablePaneProgressBar` com `nTotal` definido como -1. Por padrão `nTotal` é definido como 100. Portanto, não é necessário qualquer cálculos adicionais para exibir o andamento como porcentagem.  
  
 Você deve passar valores diferentes `clrBar` e `clrBarDest` para que a cor de plano de fundo da barra de progresso exibe uma cor combinada em um gradiente. .  
  
 Para definir o progresso atual, chame o [CMFCStatusBar::SetPaneProgress](#setpaneprogress) método.  
  
##  <a name="getcount"></a>CMFCStatusBar::GetCount  
 Recupera o número de painéis na barra de status.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 O número de painéis na barra de status.  
  
##  <a name="getdrawextendedarea"></a>CMFCStatusBar::GetDrawExtendedArea  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL GetDrawExtendedArea() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="getextendedarea"></a>CMFCStatusBar::GetExtendedArea  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL GetExtendedArea(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `rect`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="getitemid"></a>CMFCStatusBar::GetItemID  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="getitemrect"></a>CMFCStatusBar::GetItemRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 [in] `lpRect`  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="getpaneinfo"></a>CMFCStatusBar::GetPaneInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void GetPaneInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& cxWidth) const;  
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 [in] `nID`  
 [in] `nStyle`  
 [in] `cxWidth`  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="getpaneprogress"></a>CMFCStatusBar::GetPaneProgress  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
long GetPaneProgress(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="getpanestyle"></a>CMFCStatusBar::GetPaneStyle  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
UINT GetPaneStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="getpanetext"></a>CMFCStatusBar::GetPaneText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void GetPaneText(
    int nIndex,  
    CString& s) const;  
  
CString GetPaneText(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 [in] `s`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="getpanewidth"></a>CMFCStatusBar::GetPaneWidth  
 Recupera a largura do painel de uma barra de status.  
  
```  
int GetPaneWidth(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 Especifica o índice do painel da barra de status.  
  
### <a name="return-value"></a>Valor de retorno  
 A largura do painel da barra de status que `nIndex` Especifica; caso contrário, zero se não existir um painel da barra de status.  
  
##  <a name="gettiptext"></a>CMFCStatusBar::GetTipText  
 Recupere o texto de dica de ferramenta do painel da barra de status.  
  
```  
CString GetTipText(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 Especifica o índice do painel para o qual recuperar o texto da dica de ferramenta.  
  
### <a name="return-value"></a>Valor de retorno  
 O texto de dica de ferramenta do painel de barra de status que `nIndex` especifica. Caso contrário, a sequência vazia de caracteres se não existir um painel da barra de status especificado `nIndex` ou se o texto de dica de ferramenta está vazio.  
  
##  <a name="invalidatepanecontent"></a>CMFCStatusBar::InvalidatePaneContent  
 Invalidar o painel da barra de status e redesenhar o seu conteúdo.  
  
```  
void InvalidatePaneContent(int nIndex);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 Especifica o índice do painel cujo conteúdo é invalidado e redesenhado.  
  
### <a name="remarks"></a>Comentários  
 Quando a barra de status é invalidada, ela é marcada para redesenhar. Windows redesenha-quando o `UpdateWindow` método envia uma `WM_PAINT` a mensagem para o `OnPaint` método.  
  
##  <a name="ondrawpane"></a>CMFCStatusBar::OnDrawPane  
 Redesenhe o painel da barra de status.  
  
```  
virtual void OnDrawPane(
    CDC* pDC,  
    CMFCStatusBarPaneInfo* pPane);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pDC`  
 Um ponteiro para um contexto de dispositivo para o desenho.  
  
 [in] `pPane`  
 Um ponteiro para um `CMFCStatusBarPaneInfo` estrutura que contém as informações sobre o painel para ser redesenhado.  
  
### <a name="remarks"></a>Comentários  
 Por padrão, `OnDrawPane` redesenha o painel usando o contexto de dispositivo `pDC` acordo com o estilo e o conteúdo do painel.  
  
 Substitua esse método em um `CMFCStatusBar`-derivado da classe para personalizar a aparência de um painel.  
  
##  <a name="precreatewindow"></a>CMFCStatusBar::PreCreateWindow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `cs`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="setdrawextendedarea"></a>CMFCStatusBar::SetDrawExtendedArea  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetDrawExtendedArea(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `bSet`  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="setindicators"></a>CMFCStatusBar::SetIndicators  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL SetIndicators(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `lpIDArray`  
 [in] `nIDCount`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="setpaneanimation"></a>CMFCStatusBar::SetPaneAnimation  
 Atribui uma animação para o painel especificado.  
  
```  
void SetPaneAnimation(
    int nIndex,  
    HIMAGELIST hImageList,  
    UINT nFrameRate=500,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 Especifica o índice do painel ao qual você deseja atribuir a ela uma animação.  
  
 [in] `hImageList`  
 Especifica um identificador para a lista de imagens que contêm os quadros de animação.  
  
 [in] `nFrameRate`  
 Especifica a taxa de quadros, em milissegundos, para a animação.  
  
 [in] `bUpdate`  
 Se `TRUE`, atualizar o conteúdo do painel imediatamente. Caso contrário, o conteúdo do painel é atualizado quando são invalidado.  
  
### <a name="remarks"></a>Comentários  
 Se você quiser desabilitar a animação atual, chame `SetPaneAnimation` com `hImageList` definida como `NULL`.  
  
##  <a name="setpanebackgroundcolor"></a>CMFCStatusBar::SetPaneBackgroundColor  
 Define a cor de plano de fundo do painel da barra de status.  
  
```  
void SetPaneBackgroundColor(
    int nIndex,  
    COLORREF clrBackground=(COLORREF)-1,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 Especifica o índice do painel para o qual definir uma nova cor de plano de fundo.  
  
 [in] `clrBackground`  
 Especifica a nova cor do plano de fundo.  
  
 [in] `bUpdate`  
 Se `TRUE`, atualizar o conteúdo do painel imediatamente. Caso contrário, não atualize o conteúdo do painel até o painel é invalidado por outro método.  
  
##  <a name="setpaneicon"></a>CMFCStatusBar::SetPaneIcon  
 Defina o ícone do painel de barra de status.  
  
```  
void SetPaneIcon(
    int nIndex,  
    HICON hIcon,  
    BOOL bUpdate=TRUE);

 
void SetPaneIcon(
    int nIndex,  
    HBITMAP hBmp,  
    COLORREF clrTransparent=RGB(255, 0, 255),  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 Especifica o índice do painel para o qual definir a imagem.  
  
 [in] `hIcon`  
 Especifica um identificador para o ícone a ser definido como a imagem do painel.  
  
 [in] `bUpdate`  
 Especifica se deve atualizar o conteúdo do painel imediatamente.  
  
 [in] `hBmp`  
 Especifica um identificador para o bitmap a ser definido como a imagem do painel.  
  
 [in] `clrTransparent`  
 Especifica a cor transparente do bitmap que o `hBmp` indica.  
  
### <a name="remarks"></a>Comentários  
 Você pode passar um `HICON` ou `HBITMAP` junto com a cor transparente para definir a imagem do painel. Se você não deseja exibir a imagem mais, passe o `NULL` valor como a alça da imagem.  
  
 Se houver qualquer animação em execução que [CMFCStatusBar::SetPaneAnimation](#setpaneanimation) foi definida, a animação será interrompida.  
  
##  <a name="setpaneinfo"></a>CMFCStatusBar::SetPaneInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetPaneInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int cxWidth);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 [in] `nID`  
 [in] `nStyle`  
 [in] `cxWidth`  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="setpaneprogress"></a>CMFCStatusBar::SetPaneProgress  
 Defina o indicador de progresso atual da barra de progresso para o painel especificado.  
  
```  
void SetPaneProgress(
    int nIndex,  
    long nCurr,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 Especifica o índice do painel para o qual o indicador de progresso de atualização.  
  
 [in] `nCurr`  
 Especifica o valor atual do indicador de progresso.  
  
 [in] `bUpdate`  
 Especifica se o painel deve ser atualizado imediatamente.  
  
### <a name="remarks"></a>Comentários  
 Chame esse método quando desejar atualizar o indicador de progresso para a barra de progresso no painel especificado.  
  
 Para usar essa função para o painel específico, você deve chamar [CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar) primeiro.  
  
##  <a name="setpanestyle"></a>CMFCStatusBar::SetPaneStyle  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetPaneStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 [in] `nStyle`  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="setpanetext"></a>CMFCStatusBar::SetPaneText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL SetPaneText(
    int nIndex,  
    LPCTSTR lpszNewText,  
    BOOL bUpdate = TRUE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 [in] `lpszNewText`  
 [in] `bUpdate`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="setpanetextcolor"></a>CMFCStatusBar::SetPaneTextColor  
 Define a cor do texto do painel especificado.  
  
```  
void SetPaneTextColor(
    int nIndex,  
    COLORREF clrText=(COLORREF)-1,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 Especifica o índice do painel ao qual você deseja atribuir uma nova cor do texto.  
  
 [in] `clrText`  
 Especifica a cor do texto.  
  
 [in] `bUpdate`  
 Se `TRUE`, atualizar o conteúdo do painel imediatamente. Caso contrário, não atualize o conteúdo do painel até o painel é invalidado por outro método.  
  
##  <a name="setpanewidth"></a>CMFCStatusBar::SetPaneWidth  
 Defina a largura do painel da barra de status.  
  
```  
void SetPaneWidth(
    int nIndex,  
    int cx);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 O índice do painel de barra de status para o qual definir uma nova largura.  
  
 [in] `cx`  
 A nova largura do painel da barra de status, em pixels.  
  
##  <a name="settiptext"></a>CMFCStatusBar::SetTipText  
 Defina o texto de dica de ferramenta de um painel da barra de status.  
  
```  
void SetTipText(
    int nIndex,  
    LPCTSTR pszTipText);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nIndex`  
 O índice do painel ao qual você deseja atribuir o texto de dica de ferramenta.  
  
 [in] `pszTipText`  
 O novo texto de dica de ferramenta.  
  
## <a name="see-also"></a>Consulte também  
 [Gráfico de hierarquia](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe CPane](../../mfc/reference/cpane-class.md)   
 [Classe CStatusBar](../../mfc/reference/cstatusbar-class.md)
