---
title: Classe CBaseTabbedPane | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::AddTab
- AFXBASETABBEDPANE/CBaseTabbedPane::AllowDestroyEmptyTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::ApplyRestoredTabInfo
- AFXBASETABBEDPANE/CBaseTabbedPane::CanFloat
- AFXBASETABBEDPANE/CBaseTabbedPane::CanSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::ConvertToTabbedDocument
- AFXBASETABBEDPANE/CBaseTabbedPane::DetachPane
- AFXBASETABBEDPANE/CBaseTabbedPane::EnableSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::FillDefaultTabsOrderArray
- AFXBASETABBEDPANE/CBaseTabbedPane::FindBarByTabNumber
- AFXBASETABBEDPANE/CBaseTabbedPane::FindPaneByID
- AFXBASETABBEDPANE/CBaseTabbedPane::FloatTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetDefaultTabsOrder
- AFXBASETABBEDPANE/CBaseTabbedPane::GetFirstVisibleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetMinSize
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneIcon
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneList
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabArea
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::GetUnderlyingWindow
- AFXBASETABBEDPANE/CBaseTabbedPane::GetVisibleTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::HasAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::IsHideSingleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::RecalcLayout
- AFXBASETABBEDPANE/CBaseTabbedPane::RemovePane
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoDestroy
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::ShowTab
dev_langs:
- C++
helpviewer_keywords:
- CBaseTabbedPane class
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b72804dd8b2ca2253caff4cebf5b0631ae6040c6
ms.lasthandoff: 02/25/2017

---
# <a name="cbasetabbedpane-class"></a>Classe CBaseTabbedPane
Estende a funcionalidade do [CDockablePane classe](../../mfc/reference/cdockablepane-class.md) oferece suporte à criação de janelas com guias.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class CBaseTabbedPane : public CDockablePane  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|`CBaseTabbedPane::CBaseTabbedPane`|Construtor padrão.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CBaseTabbedPane::AddTab](#addtab)|Adiciona uma nova guia a um painel com guias.|  
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Especifica se um painel com guias vazia pode ser destruído.|  
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|Aplica as configurações de guia, que são carregadas do registro, um painel com guias.|  
|[CBaseTabbedPane::CanFloat](#canfloat)|Determina se o painel pode flutuar. (Substitui [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|  
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Determina se a legenda para o painel com guias deve exibir o mesmo texto como a guia ativa.|  
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(Substitui [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|  
|[CBaseTabbedPane::DetachPane](#detachpane)|Converte um ou mais painéis encaixáveis documentos MDI com guias.|  
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Habilita ou desabilita a capacidade do painel com guias para sincronizar o texto de legenda com o texto do rótulo na guia ativa.|  
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Restaura a ordem de tabulação interno para um estado padrão.|  
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|Retorna um painel que reside em uma guia quando a guia é identificada por um índice de tabulação com base em zero.|  
|||  
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|Retorna um painel que é identificado pela ID do painel.|  
|[CBaseTabbedPane::FloatTab](#floattab)|Flutua um painel, mas apenas se o painel estiver atualmente em uma guia destacáveis.|  
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|Retorna a ordem padrão das guias no painel.|  
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|Recupera um ponteiro para a primeira guia exibida.|  
|[CBaseTabbedPane::GetMinSize](#getminsize)|Recupera o mínimo permitido de tamanho para o painel. (Substitui [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|  
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|Retorna um identificador para o ícone do painel. (Substitui [CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|  
|[CBaseTabbedPane::GetPaneList](#getpanelist)|Retorna uma lista de painéis que estão contidos no painel com guias.|  
|[CBaseTabbedPane::GetTabArea](#gettabarea)|Retorna os retângulos delimitadores para as áreas de guia superior e inferior.|  
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|Retorna a contagem de guias em uma janela de guia.|  
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|Obtém a janela de guia (encapsulado) subjacente.|  
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|Retorna a contagem de guias exibidas.|  
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|Determina se o painel com guias pode ser alternado para o modo de ocultar automaticamente.|  
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|Determina se o painel com guias está oculto se apenas um guia é exibida.|  
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Usado internamente durante a serialização.|  
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|Recalcula as informações de layout para o painel. (Substitui [CPane::RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|  
|[CBaseTabbedPane::RemovePane](#removepane)|Remove um painel do painel com guias.|  
|`CBaseTabbedPane::SaveSiblingBarIDs`|Usado internamente durante a serialização.|  
|`CBaseTabbedPane::Serialize`|(Substitui [CDockablePane::Serialize](http://msdn.microsoft.com/en-us/09787e59-e446-4e76-894b-206d303dcfd6).)|  
|`CBaseTabbedPane::SerializeTabWindow`|Usado internamente durante a serialização.|  
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|Determina se a barra de controle com guias será destruída automaticamente.|  
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|Alterna o painel de encaixe entre exibido e o modo de ocultar automaticamente. (Substitui [CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|  
|[CBaseTabbedPane::ShowTab](#showtab)|Mostra ou oculta uma guia.|  
  
## <a name="remarks"></a>Comentários  
 Essa classe é uma classe abstrata e não pode ser instanciada. Ele implementa os serviços que são comuns a todos os tipos de painéis com guias.  
  
 Atualmente, a biblioteca inclui duas classes derivadas painel com guias: [CTabbedPane classe](../../mfc/reference/ctabbedpane-class.md) e [CMFCOutlookBar classe](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 A `CBaseTabbedPane` objeto encapsula um ponteiro para um [CMFCBaseTabCtrl classe](../../mfc/reference/cmfcbasetabctrl-class.md) objeto. [Classe CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) torna-se uma janela filho do painel com guias.  
  
 Para obter mais informações sobre como criar painéis com guias, consulte [CDockablePane classe](../../mfc/reference/cdockablepane-class.md), [CTabbedPane classe](../../mfc/reference/ctabbedpane-class.md), e [CMFCOutlookBar classe](../../mfc/reference/cmfcoutlookbar-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 `CBaseTabbedPane`  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** afxBaseTabbedPane.h  
  
##  <a name="addtab"></a>CBaseTabbedPane::AddTab  
 Adiciona uma nova guia a um painel com guias.  
  
```  
virtual BOOL AddTab(
    CWnd* pNewBar,  
    BOOL bVisible = TRUE,  
    BOOL bSetActive = TRUE,  
    BOOL bDetachable = TRUE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] [out]`pNewBar`  
 Um ponteiro para o painel para adicionar. Esse ponteiro pode se tornar inválido depois de chamar esse método. Para obter mais informações, consulte a seção Comentários.  
  
 [in] `bVisible`  
 `TRUE`Para tornar a guia visível; Caso contrário, `FALSE`.  
  
 [in] `bSetActive`  
 `TRUE`Para tornar a guia a guia ativa; Caso contrário, `FALSE`.  
  
 [in] `bDetachable`  
 `TRUE`Para tornar a guia destacáveis; Caso contrário, `FALSE`.  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se o painel foi adicionado com êxito como uma guia e não foi destruído no processo. `FALSE`Se o painel que está sendo adicionado é um objeto do tipo `CBaseTabbedPane`. Para obter mais informações, consulte a seção Comentários.  
  
### <a name="remarks"></a>Comentários  
 Chame esse método para adicionar um painel como uma nova guia em um painel com guias. Se `pNewBar` aponta para um objeto do tipo `CBaseTabbedPane`, todas as suas guias são copiados para o painel com guias e, em seguida, `pNewBar` é destruído. Portanto, `pNewBar` se torna um ponteiro inválido e não deve ser usado.  
  
##  <a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane::AllowDestroyEmptyTabbedPane  
 Especifica se um painel com guias vazia pode ser destruído.  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se um painel com guias vazia pode ser destruído; Caso contrário, `FALSE`. A implementação padrão sempre retorna `TRUE`.  
  
### <a name="remarks"></a>Comentários  
 Se um painel com guias vazia não é permitida a ser destruído, o framework oculta o painel.  
  
##  <a name="applyrestoredtabinfo"></a>CBaseTabbedPane::ApplyRestoredTabInfo  
 Carrega configurações da guia do registro e aplica-se a um painel com guias.  
  
```  
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `bUseTabIndexes`  
 Esse parâmetro é usado internamente pela estrutura.  
  
### <a name="remarks"></a>Comentários  
 Esse método é chamado pela estrutura quando ele recarrega as informações de estado de encaixe do registro. O método obtém informações sobre ordem de tabulação e nomes de guia de um painel com guias.  
  
##  <a name="canfloat"></a>CBaseTabbedPane::CanFloat  
 Especifica se o painel com guias pode flutuar.  
  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se o painel pode flutuar; Caso contrário, `FALSE`.  
  
##  <a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane::CanSetCaptionTextToTabName  
 Determina se a legenda para o painel com guias deve exibir o mesmo texto como a guia ativa.  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se o texto da legenda do painel com guias é definido como o texto da guia ativa; Caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 O método é usado para determinar se o texto exibido nas duplicatas de legenda com guias painel o rótulo da guia ativa. Você pode habilitar ou desabilitar essa funcionalidade chamando [CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname).  
  
##  <a name="converttotabbeddocument"></a>CBaseTabbedPane::ConvertToTabbedDocument  
 Converte um ou mais painéis encaixáveis documentos MDI com guias.  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `bActiveTabOnly`  
 Quando você converte um painel com guias, especifique `TRUE` para converter apenas a guia ativa. Especifique `FALSE` para converter todas as guias no painel.  
  
##  <a name="detachpane"></a>CBaseTabbedPane::DetachPane  
 Desconecta um painel no painel com guias.  
  
```  
virtual BOOL DetachPane(
    CWnd* pBar,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pBar`  
 Ponteiro para o painel para desanexar.  
  
 [in] `bHide`  
 Parâmetro booleano que especifica se a estrutura oculta o painel depois que ele é desanexado.  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se a estrutura desanexado com êxito o painel; `FALSE` se `pBar` é `NULL` ou se refere a um painel que não está no painel com guias.  
  
### <a name="remarks"></a>Comentários  
 O framework flutua painel desanexado se possível. Para obter mais informações, consulte [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).  
  
##  <a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane::EnableSetCaptionTextToTabName  
 Habilita ou desabilita a capacidade do painel com guias para sincronizar o texto de legenda com o texto do rótulo na guia ativa.  
  
```  
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `bEnable`  
 `TRUE`para sincronizar a legenda do painel com guias com a legenda da guia ativa; Caso contrário, `FALSE`.  
  
##  <a name="filldefaulttabsorderarray"></a>CBaseTabbedPane::FillDefaultTabsOrderArray  
 Restaura a ordem de tabulação interno para um estado padrão.  
  
```  
void FillDefaultTabsOrderArray();
```  
  
### <a name="remarks"></a>Comentários  
 Esse método é chamado quando o framework restaura uma barra do Outlook para um estado inicial.  
  
##  <a name="findpanebyid"></a>CBaseTabbedPane::FindPaneByID  
 Retorna um painel identificado pela ID do painel.  
  
```  
virtual CWnd* FindPaneByID(UINT uBarID);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `uBarID`  
 Especifica a ID do painel Localizar.  
  
### <a name="return-value"></a>Valor de retorno  
 Um ponteiro para o painel se ele foi encontrado; Caso contrário, `NULL`.  
  
### <a name="remarks"></a>Comentários  
 Este método compara todas as guias no painel e retorna com a ID especificada pelo `uBarID` parâmetro.  
  
##  <a name="findbarbytabnumber"></a>CBaseTabbedPane::FindBarByTabNumber  
 Retorna um painel que reside em uma guia.  
  
```  
virtual CWnd* FindBarByTabNumber(
    int nTabNum,  
    BOOL bGetWrappedBar = FALSE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nTabNum`  
 Especifica o índice baseado em zero da guia para recuperar.  
  
 [in] `bGetWrappedBar`  
 `TRUE`para retornar a janela subjacente (encapsulada) do painel, em vez de painel em si; Caso contrário, `FALSE`. Isso se aplica apenas aos painéis derivados de [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md).  
  
### <a name="return-value"></a>Valor de retorno  
 Se o painel for encontrado, será retornado um ponteiro válido para o painel que está sendo pesquisado; Caso contrário, `NULL`.  
  
### <a name="remarks"></a>Comentários  
 Chame esse método para recuperar o painel que residem na guia especificada pelo `nTabNum` parâmetro.  
  
##  <a name="floattab"></a>CBaseTabbedPane::FloatTab  
 Flutua um painel, mas apenas se o painel estiver atualmente em uma guia destacáveis.  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] [out]`pBar`  
 Um ponteiro para o painel para float.  
  
 [in] `nTabID`  
 Especifica o índice baseado em zero da guia para float.  
  
 [in] `dockMethod`  
 Especifica o método a ser usado para tornar o float de painel. Para obter mais informações, consulte a seção Comentários.  
  
 [in] `bHide`  
 `TRUE`Para ocultar o painel antes de flutuante; Caso contrário, `FALSE`.  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se o painel flutuante; Caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 Chame esse método para flutuar um painel que resida em uma guia destacáveis.  
  
 Especifique se você deseja desanexar um painel por meio de programação, `DM_SHOW` para o `dockMethod` parâmetro. Para flutuar um painel na mesma posição em que ele flutuar anteriormente, especifique `DM_DBL_CLICK` como o `dockMethod` parâmetro.  
  
##  <a name="getdefaulttabsorder"></a>CBaseTabbedPane::GetDefaultTabsOrder  
 Retorna a ordem padrão das guias no painel.  
  
```  
const CArray<int,int>& GetDefaultTabsOrder();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um `CArray` objeto que especifica a ordem padrão das guias no painel.  
  
### <a name="remarks"></a>Comentários  
 O framework chama esse método quando uma barra do Outlook é redefinida para um estado inicial.  
  
##  <a name="getfirstvisibletab"></a>CBaseTabbedPane::GetFirstVisibleTab  
 Recupera um ponteiro para a primeira guia exibida.  
  
```  
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `iTabNum`  
 Uma referência a um número inteiro. Esse método grava o índice baseado em zero da primeira guia exibida para esse parâmetro, ou -1 se não exibidos guia for encontrada.  
  
### <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, um ponteiro para a primeira guia exibida; Caso contrário, `NULL`.  
  
##  <a name="getminsize"></a>CBaseTabbedPane::GetMinSize  
 Recupera o mínimo permitido de tamanho para o painel.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parâmetros  
 [out] `size`  
 Um `CSize` objeto que é preenchido com o mínimo de tamanho permitido.  
  
### <a name="remarks"></a>Comentários  
 Se o tratamento consistente de tamanhos mínimo painel está ativo ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), `size` é preenchido com o mínimo permitido de tamanho para a guia ativa. Caso contrário, `size` é preenchido com o valor de retorno [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).  
  
##  <a name="getpaneicon"></a>CBaseTabbedPane::GetPaneIcon  
 Recupera o mínimo permitido de tamanho para o painel.  
  
```  
virtual void GetMinSize(CSize& size) const;  
```  
  
### <a name="parameters"></a>Parâmetros  
 [out] `size`  
 Um `CSize` objeto que é preenchido com o mínimo de tamanho permitido.  
  
### <a name="remarks"></a>Comentários  
 Se o tratamento consistente de tamanhos mínimo painel está ativo ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), `size` é preenchido com o mínimo permitido de tamanho para a guia ativa. Caso contrário, `size` é preenchido com o valor de retorno [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).  
  
##  <a name="getpanelist"></a>CBaseTabbedPane::GetPaneList  
 Retorna uma lista de painéis que estão contidos no painel com guias.  
  
```  
virtual void GetPaneList(
    CObList& lst,  
    CRuntimeClass* pRTCFilter = NULL);
```  
  
### <a name="parameters"></a>Parâmetros  
 [out] `lst`  
 Um `CObList` que é preenchido com os painéis que estão contidos no painel com guias.  
  
 [in] `pRTCFilter`  
 Se não for `NULL`, a lista retornada contém apenas os painéis de classe de tempo de execução especificado.  
  
##  <a name="gettabarea"></a>CBaseTabbedPane::GetTabArea  
 Retorna os retângulos delimitadores para as áreas de guia superior e inferior.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const = 0;  
```  
  
### <a name="parameters"></a>Parâmetros  
 [out] `rectTabAreaTop`  
 Recebe as coordenadas de tela da área de guia superior.  
  
 [out] `rectTabAreaBottom`  
 Recebe as coordenadas de tela da área inferior da guia.  
  
### <a name="remarks"></a>Comentários  
 Chame esse método para determinar os retângulos delimitadores, em coordenadas da tela, para as áreas de guia superior e inferior.  
  
##  <a name="gettabsnum"></a>CBaseTabbedPane::GetTabsNum  
 Retorna a contagem de guias em uma janela de guia.  
  
```  
virtual int GetTabsNum() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 O número de guias do painel com guias.  
  
##  <a name="getunderlyingwindow"></a>CBaseTabbedPane::GetUnderlyingWindow  
 Obtém a janela de guia (encapsulado) subjacente.  
  
```  
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um ponteiro para a janela de guia subjacente.  
  
##  <a name="getvisibletabsnum"></a>CBaseTabbedPane::GetVisibleTabsNum  
 Retorna a contagem de guias visíveis.  
  
```  
virtual int GetVisibleTabsNum() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 O número de guias visíveis, que será maior que ou igual a zero.  
  
### <a name="remarks"></a>Comentários  
 Chame esse método para determinar o número de guias visíveis no painel com guias.  
  
##  <a name="hasautohidemode"></a>CBaseTabbedPane::HasAutoHideMode  
 Determina se o painel com guias pode ser alternado para o modo de ocultar automaticamente.  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se o painel pode ser alternado para o modo de ocultar automaticamente; Caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 Se o modo de ocultar automaticamente estiver desabilitado, nenhum botão pin é exibido na legenda painel com guias.  
  
##  <a name="ishidesingletab"></a>CBaseTabbedPane::IsHideSingleTab  
 Determina se o painel com guias está oculto se apenas um guia é exibida.  
  
```  
virtual BOOL IsHideSingleTab() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se a janela de guia não é mostrada quando há apenas uma guia visível. Caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 Se o painel não é exibido porque há apenas uma guia aberta, você pode chamar esse método para determinar se o painel com guias está funcionando corretamente.  
  
##  <a name="removepane"></a>CBaseTabbedPane::RemovePane  
 Remove um painel do painel com guias.  
  
```  
virtual BOOL RemovePane(CWnd* pBar);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] [out]`pBar`  
 Um ponteiro para o painel para remover do painel com guias.  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se o painel foi removido com êxito do painel com guias e painel com guias ainda é válido. `FALSE`Se o último painel foi removido do painel com guias e painel com guias está prestes a ser destruído. Se o valor de retorno é `FALSE`, não usa mais o painel com guias.  
  
### <a name="remarks"></a>Comentários  
 Chame esse método para remover o painel especificado pelo `pBar` parâmetro do painel com guias.  
  
##  <a name="setautodestroy"></a>CBaseTabbedPane::SetAutoDestroy  
 Determina se a barra de controle com guias será destruída automaticamente.  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `bAutoDestroy`  
 `TRUE`Se o painel com guias foi criado dinamicamente e você não estiver controlando seu tempo de vida; Caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 Defina o destruir automaticamente de modo a `TRUE` se você criar um painel com guias dinamicamente e se você não estiver controlando seu tempo de vida. Se destruir automática é de modo `TRUE`, o painel com guias será destruído automaticamente pela estrutura.  
  
##  <a name="showtab"></a>CBaseTabbedPane::ShowTab  
 Mostra ou oculta uma guia.  
  
```  
virtual BOOL ShowTab(
    CWnd* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pBar`  
 Um ponteiro para o painel para mostrar ou ocultar.  
  
 [in] `bShow`  
 `TRUE`para mostrar o painel; `FALSE` para ocultar o painel.  
  
 [in] `bDelay`  
 `TRUE`Para atrasar o ajuste do layout do guia; Caso contrário, `FALSE`.  
  
 [in] `bActivate`  
 `TRUE`Para tornar a guia a guia ativa; Caso contrário, `FALSE`.  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se a guia foi mostrada ou oculta com êxito; Caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 Quando você chama esse método, um painel é mostrado ou oculto, dependendo do valor da `bShow` parâmetro. Se você ocultar uma guia e é a última guia visível na janela de guia subjacente, o painel com guias está oculto. Se você mostrar uma guia quando anteriormente não havia nenhuma guias visíveis, é mostrado o painel com guias.  
  
##  <a name="recalclayout"></a>CBaseTabbedPane::RecalcLayout  
 Recalcula as informações de layout para o painel.  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Comentários  
 Se o painel estiver flutuando, este método notifica a estrutura para redimensionar o painel para o tamanho atual do quadro simplificado.  
  
 Se o painel estiver encaixado, esse método não fará nada.  
  
##  <a name="setautohidemode"></a>CBaseTabbedPane::SetAutoHideMode  
 Define o modo de ocultar automaticamente para destacáveis painéis no painel com guias.  
  
```  
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,  
    DWORD dwAlignment,  
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `bMode`  
 `TRUE`Para habilitar o modo de ocultar automaticamente; `FALSE` para habilitar o modo de encaixe regular.  
  
 [in] `dwAlignment`  
 Especifica o alinhamento do painel de ocultação automática deve ser criado. Para obter uma lista dos valores possíveis, consulte [CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).  
  
 [in] [out]`pCurrAutoHideBar`  
 Um ponteiro para a barra de ferramentas de ocultar automaticamente atual. Pode ser `NULL`.  
  
 [in] `bUseTimer`  
 Especifica se deve usar o efeito de ocultar automaticamente quando o usuário alterna o painel para o modo de ocultar automaticamente ou ocultar o painel imediatamente.  
  
### <a name="return-value"></a>Valor de retorno  
 Um ponteiro para a barra de ferramentas de ocultar automaticamente é criado quando você alterna para o modo de ocultar automaticamente, ou `NULL` se nenhuma barra de ferramentas é criada.  
  
### <a name="remarks"></a>Comentários  
 O framework chama esse método quando um usuário escolhe o botão Fixar ao painel com guias, alterne para o modo de ocultar automaticamente ou para o modo normal de encaixe.  
  
 Modo de ocultar automaticamente está definido para cada painel destacáveis no painel com guias. Painéis são não-removíveis são ignorados. Para obter mais informações, consulte [CMFCBaseTabCtrl::EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).  
  
 Chame esse método para alternar programaticamente um painel com guias para o modo de ocultar automaticamente. O painel deve ser encaixado à janela principal do quadro ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) deve retornar um ponteiro válido para o [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).  
  
## <a name="see-also"></a>Consulte também  
 [Gráfico de hierarquia](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe CDockablePane](../../mfc/reference/cdockablepane-class.md)
