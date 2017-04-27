---
title: Classe IOleObjectImpl | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl::Advise
- ATLCTL/ATL::IOleObjectImpl::Close
- ATLCTL/ATL::IOleObjectImpl::DoVerb
- ATLCTL/ATL::IOleObjectImpl::DoVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::DoVerbHide
- ATLCTL/ATL::IOleObjectImpl::DoVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::DoVerbOpen
- ATLCTL/ATL::IOleObjectImpl::DoVerbPrimary
- ATLCTL/ATL::IOleObjectImpl::DoVerbShow
- ATLCTL/ATL::IOleObjectImpl::DoVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::EnumAdvise
- ATLCTL/ATL::IOleObjectImpl::EnumVerbs
- ATLCTL/ATL::IOleObjectImpl::GetClientSite
- ATLCTL/ATL::IOleObjectImpl::GetClipboardData
- ATLCTL/ATL::IOleObjectImpl::GetExtent
- ATLCTL/ATL::IOleObjectImpl::GetMiscStatus
- ATLCTL/ATL::IOleObjectImpl::GetMoniker
- ATLCTL/ATL::IOleObjectImpl::GetUserClassID
- ATLCTL/ATL::IOleObjectImpl::GetUserType
- ATLCTL/ATL::IOleObjectImpl::InitFromData
- ATLCTL/ATL::IOleObjectImpl::IsUpToDate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::SetClientSite
- ATLCTL/ATL::IOleObjectImpl::SetColorScheme
- ATLCTL/ATL::IOleObjectImpl::SetExtent
- ATLCTL/ATL::IOleObjectImpl::SetHostNames
- ATLCTL/ATL::IOleObjectImpl::SetMoniker
- ATLCTL/ATL::IOleObjectImpl::Unadvise
- ATLCTL/ATL::IOleObjectImpl::Update
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
caps.latest.revision: 20
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: b0b471b997bfdb4062f00b40864c347db78b114a
ms.lasthandoff: 02/25/2017

---
# <a name="ioleobjectimpl-class"></a>Classe IOleObjectImpl
Essa classe implementa **IUnknown** e é a principal interface através da qual um contêiner se comunica com um controle.  
  
> [!IMPORTANT]
>  Essa classe e seus membros não podem ser usados em aplicativos que são executados a [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## <a name="syntax"></a>Sintaxe  
  
```
template<class T>  
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```  
  
#### <a name="parameters"></a>Parâmetros  
 `T`  
 Sua classe derivada de `IOleObjectImpl`.  
  
## <a name="members"></a>Membros  
  
### <a name="public-methods"></a>Métodos Públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[IOleObjectImpl::Advise](#advise)|Estabelece uma conexão comunicado com o controle.|  
|[IOleObjectImpl::Close](#close)|Altera o estado de controle de execução para carregar.|  
|[IOleObjectImpl::DoVerb](#doverb)|Informa o controle para executar uma das suas ações enumeradas.|  
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|Informa o controle para descartar qualquer estado de desfazer é manter.|  
|[IOleObjectImpl::DoVerbHide](#doverbhide)|Informa o controle para remover sua interface do usuário da exibição.|  
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|Executa o controle e instala sua janela, mas não instalar a interface do usuário do controle.|  
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|Faz com que o controle a ser editado para abrir em uma janela separada.|  
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|Executa a ação especificada quando o usuário clica duas vezes no controle. O controle define a ação, normalmente para ativar o controle no local.|  
|[IOleObjectImpl::DoVerbShow](#doverbshow)|Mostra um controle recentemente inserido para o usuário.|  
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|Ativa o controle no local e mostra a interface do usuário do controle, como menus e barras de ferramentas.|  
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Enumera conexões de consultoria do controle.|  
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Enumera as ações do controle.|  
|[IOleObjectImpl::GetClientSite](#getclientsite)|Recupera um site do cliente do controle.|  
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Recupera dados da área de transferência. Retorna a implementação de ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::GetExtent](#getextent)|Recupera a extensão da área de exibição do controle.|  
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Recupera o status do controle.|  
|[IOleObjectImpl::GetMoniker](#getmoniker)|Recupera o identificador de origem do controle. Retorna a implementação de ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Recupera o identificador de classe do controle.|  
|[IOleObjectImpl::GetUserType](#getusertype)|Recupera o nome do tipo de usuário do controle.|  
|[IOleObjectImpl::InitFromData](#initfromdata)|Inicializa o controle de dados selecionada. Retorna a implementação de ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::IsUpToDate](#isuptodate)|Verifica se o controle é atualizado. Retorna a implementação de ATL `S_OK`.|  
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Chamado por [DoVerbDiscardUndo](#doverbdiscardundo) depois que o estado de desfazer é descartado.|  
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Chamado por [DoVerbHide](#doverbhide) depois que o controle está oculto.|  
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Chamado por [DoVerbInPlaceActivate](#doverbinplaceactivate) depois que o controle é ativado em vigor.|  
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|Chamado por [DoVerbOpen](#doverbopen) depois que o controle foi aberto para edição em uma janela separada.|  
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Chamado por [DoVerbShow](#doverbshow) depois que o controle foi feito visível.|  
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Chamado por [DoVerbUIActivate](#doverbuiactivate) após a ativação de interface do usuário do controle.|  
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Chamado por [DoVerbDiscardUndo](#doverbdiscardundo) antes de desfazer o estado é descartado.|  
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|Chamado por [DoVerbHide](#doverbhide) antes que o controle está oculto.|  
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|Chamado por [DoVerbInPlaceActivate](#doverbinplaceactivate) antes que o controle é ativado em vigor.|  
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|Chamado por [DoVerbOpen](#doverbopen) antes que o controle foi aberto para edição em uma janela separada.|  
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Chamado por [DoVerbShow](#doverbshow) antes que o controle foi feito visível.|  
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Chamado por [DoVerbUIActivate](#doverbuiactivate) antes de interface do usuário do controle foi ativado.|  
|[IOleObjectImpl::SetClientSite](#setclientsite)|Informa o controle sobre seu site do cliente no contêiner.|  
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Recomenda um esquema de cores para o aplicativo do controle, se houver. Retorna a implementação de ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::SetExtent](#setextent)|Define a extensão da área de exibição do controle.|  
|[IOleObjectImpl::SetHostNames](#sethostnames)|Informa o controle os nomes do aplicativo de contêiner e do documento contêiner.|  
|[IOleObjectImpl::SetMoniker](#setmoniker)|Informa ao controle qual é seu identificador de origem. Retorna a implementação de ATL **E_NOTIMPL**.|  
|[IOleObjectImpl::Unadvise](#unadvise)|Exclui um comunicado de conexão com o controle.|  
|[IOleObjectImpl::Update](#update)|Atualiza o controle. Retorna a implementação de ATL `S_OK`.|  
  
## <a name="remarks"></a>Comentários  
 O [IOleObject](http://msdn.microsoft.com/library/windows/desktop/dd542709) interface é a interface principal por meio do qual um contêiner se comunica com um controle. Classe `IOleObjectImpl` fornece uma implementação padrão dessa interface e implementa **IUnknown** enviando informações para o despejo de compilações de dispositivo no modo de depuração.  
  
 **Artigos relacionados** [Tutorial da ATL](../../atl/active-template-library-atl-tutorial.md), [criando um projeto do ATL](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 `IOleObject`  
  
 `IOleObjectImpl`  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** atlctl.h  
  
##  <a name="advise"></a>IOleObjectImpl::Advise  
 Estabelece uma conexão comunicado com o controle.  
  
```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>Comentários  
 Consulte [IOleObject::Advise](http://msdn.microsoft.com/library/windows/desktop/ms686573) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="close"></a>IOleObjectImpl::Close  
 Altera o estado de controle de execução para carregar.  
  
```
STDMETHOD(Close)(DWORD dwSaveOption);
```  
  
### <a name="remarks"></a>Comentários  
 Desativa o controle e destrói a janela de controle se ele existir. Se o controle de membro de dados da classe [CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) é **TRUE** e `dwSaveOption` parâmetro seja `OLECLOSE_SAVEIFDIRTY` ou `OLECLOSE_PROMPTSAVE`, as propriedades de controle são salvos antes de fechar.  
  
 Os ponteiros são mantidos nos membros de dados de classe de controle [CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) e [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) são lançadas e os membros de dados [CComControlBase::m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless), e [CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) são definidos como **FALSE**.  
  
 Consulte [IOleObject::Close](http://msdn.microsoft.com/library/windows/desktop/ms683922) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="doverb"></a>IOleObjectImpl::DoVerb  
 Informa o controle para executar uma das suas ações enumeradas.  
  
```
STDMETHOD(DoVerb)(
    LONG iVerb,
    LPMSG /* pMsg */,
    IOleClientSite* pActiveSite,
    LONG /* lindex */,
    HWND hwndParent,
    LPCRECT lprcPosRect);
```  
  
### <a name="remarks"></a>Comentários  
 Dependendo do valor de `iVerb`, um do ATL `DoVerb` funções auxiliares é chamado como segue:  
  
|*iVerb* valor|Função de auxiliar DoVerb chamada|  
|-------------------|-----------------------------------|  
|**OLEIVERB_DISCARDUNDOSTATE**|[DoVerbDiscardUndo](#doverbdiscardundo)|  
|`OLEIVERB_HIDE`|[DoVerbHide](#doverbhide)|  
|**OLEIVERB_INPLACEACTIVATE**|[DoVerbInPlaceActivate](#doverbinplaceactivate)|  
|`OLEIVERB_OPEN`|[DoVerbOpen](#doverbopen)|  
|`OLEIVERB_PRIMARY`|[DoVerbPrimary](#doverbprimary)|  
|**OLEIVERB_PROPERTIES**|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|  
|`OLEIVERB_SHOW`|[DoVerbShow](#doverbshow)|  
|`OLEIVERB_UIACTIVATE`|[DoVerbUIActivate](#doverbuiactivate)|  
  
 Consulte [IOleObject:: DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="doverbdiscardundo"></a>IOleObjectImpl::DoVerbDiscardUndo  
 Informa o controle para descartar qualquer estado de desfazer é manter.  
  
```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parâmetros  
 `prcPosRec`  
 [in] Ponteiro para o contêiner de retângulo deseja desenhar o controle.  
  
 *hwndParent*  
 [in] Identificador da janela que contém o controle.  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
##  <a name="doverbhide"></a>IOleObjectImpl::DoVerbHide  
 Desativa e remove a interface do usuário do controle e oculta o controle.  
  
```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parâmetros  
 `prcPosRec`  
 [in] Ponteiro para o contêiner de retângulo deseja desenhar o controle.  
  
 *hwndParent*  
 [in] Identificador da janela que contém o controle. Não usado na implementação do ATL.  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
##  <a name="doverbinplaceactivate"></a>IOleObjectImpl::DoVerbInPlaceActivate  
 Executa o controle e instala sua janela, mas não instalar a interface do usuário do controle.  
  
```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parâmetros  
 `prcPosRec`  
 [in] Ponteiro para o contêiner de retângulo deseja desenhar o controle.  
  
 *hwndParent*  
 [in] Identificador da janela que contém o controle. Não usado na implementação do ATL.  
  
### <a name="return-value"></a>Valor de retorno  
 Um dos padrão `HRESULT` valores.  
  
### <a name="remarks"></a>Comentários  
 Ativa o controle no lugar chamando [CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate). A menos que o membro de dados da classe de controle `m_bWindowOnly` é **TRUE**, `DoVerbInPlaceActivate` primeiro tenta ativar o controle como um controle sem janelas (possível somente se o contêiner oferece suporte a [IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300)). Se isso falhar, a função tenta ativar o controle com recursos estendidos (possível somente se o contêiner oferece suporte a [IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461)). Se isso falhar, a função tenta ativar o controle com nenhum recurso estendido (possível somente se o contêiner oferece suporte a [IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586)). Se a ativação for bem-sucedida, a função notifica o contêiner que de controle foi ativado.  
  
##  <a name="doverbopen"></a>IOleObjectImpl::DoVerbOpen  
 Faz com que o controle a ser editado para abrir em uma janela separada.  
  
```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parâmetros  
 `prcPosRec`  
 [in] Ponteiro para o contêiner de retângulo deseja desenhar o controle.  
  
 *hwndParent*  
 [in] Identificador da janela que contém o controle.  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
##  <a name="doverbprimary"></a>IOleObjectImpl::DoVerbPrimary  
 Define a ação executada quando o usuário clica duas vezes no controle.  
  
```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```  
  
### <a name="parameters"></a>Parâmetros  
 `prcPosRec`  
 [in] Ponteiro para o contêiner de retângulo deseja desenhar o controle.  
  
 *hwndParent*  
 [in] Identificador da janela que contém o controle.  
  
### <a name="return-value"></a>Valor de retorno  
 Um dos padrão `HRESULT` valores.  
  
### <a name="remarks"></a>Comentários  
 Por padrão, definido para exibir as páginas de propriedades. Você pode substituí-lo em sua classe de controle para invocar um comportamento diferente ao clicar duas vezes; Por exemplo, reproduzir um vídeo ou vá ativo no local.  
  
##  <a name="doverbshow"></a>IOleObjectImpl::DoVerbShow  
 Informa o contêiner para tornar o controle visível.  
  
```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parâmetros  
 `prcPosRec`  
 [in] Ponteiro para o contêiner de retângulo deseja desenhar o controle.  
  
 *hwndParent*  
 [in] Identificador da janela que contém o controle. Não usado na implementação do ATL.  
  
### <a name="return-value"></a>Valor de retorno  
 Um dos padrão `HRESULT` valores.  
  
##  <a name="doverbuiactivate"></a>IOleObjectImpl::DoVerbUIActivate  
 Ativa a interface do usuário do controle e notifica o contêiner que seus menus estão sendo substituídos por menus compostos.  
  
```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>Parâmetros  
 `prcPosRec`  
 [in] Ponteiro para o contêiner de retângulo deseja desenhar o controle.  
  
 *hwndParent*  
 [in] Identificador da janela que contém o controle. Não usado na implementação do ATL.  
  
### <a name="return-value"></a>Valor de retorno  
 Um dos padrão `HRESULT` valores.  
  
##  <a name="enumadvise"></a>IOleObjectImpl::EnumAdvise  
 Fornece uma enumeração das conexões de consultoria registradas para este controle.  
  
```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```  
  
### <a name="remarks"></a>Comentários  
 Consulte [IOleObject::EnumAdvise](http://msdn.microsoft.com/library/windows/desktop/ms682355) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="enumverbs"></a>IOleObjectImpl::EnumVerbs  
 Fornece uma enumeração de ações registradas (verbos) para este controle chamando **OleRegEnumVerbs**.  
  
```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```  
  
### <a name="remarks"></a>Comentários  
 Você pode adicionar verbos ao arquivo rgs do seu projeto. Por exemplo, consulte CIRCCTL. RGS no [c](../../visual-cpp-samples.md) exemplo.  
  
 Consulte [IOleObject::EnumVerbs](http://msdn.microsoft.com/library/windows/desktop/ms692781) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getclientsite"></a>IOleObjectImpl::GetClientSite  
 Coloca o ponteiro em membro de dados da classe de controle [CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) em *ppClientSite* e incrementa a contagem de referência no ponteiro.  
  
```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```  
  
### <a name="remarks"></a>Comentários  
 Consulte [IOleObject::GetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms692603) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData  
 Recupera dados da área de transferência.  
  
```
STDMETHOD(GetClipboardData)(    
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentários  
 Consulte [IOleObject::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/ms682288) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getextent"></a>IOleObjectImpl::GetExtent  
 Recupera o tamanho da exibição do controle de uma execução em unidades HIMETRIC (0,01 milímetro por unidade).  
  
```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>Comentários  
 O tamanho é armazenado no membro de dados da classe de controle [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).  
  
 Consulte [IOleObject::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms692325) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus  
 Retorna um ponteiro para informações de status registrado para o controle chamando **OleRegGetMiscStatus**.  
  
```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>Comentários  
 As informações de status incluem comportamentos suportados pelo controle e apresentação de dados. Você pode adicionar informações de status para o arquivo rgs do seu projeto.  
  
 Consulte [IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getmoniker"></a>IOleObjectImpl::GetMoniker  
 Recupera o identificador de origem do controle.  
  
```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentários  
 Consulte [IOleObject::GetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms686576) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID  
 Retorna o identificador de classe do controle.  
  
```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```  
  
### <a name="remarks"></a>Comentários  
 Consulte [IOleObject::GetUserClassID](http://msdn.microsoft.com/library/windows/desktop/ms682313) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getusertype"></a>IOleObjectImpl::GetUserType  
 Retorna o nome do tipo de usuário do controle chamando **OleRegGetUserType**.  
  
```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```  
  
### <a name="remarks"></a>Comentários  
 O nome do tipo de usuário é usado para exibição em elementos de interfaces do usuário, como menus e caixas de diálogo. Você pode alterar o nome do tipo de usuário no arquivo rgs do seu projeto.  
  
 Consulte [IOleObject::GetUserType](http://msdn.microsoft.com/library/windows/desktop/ms688643) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="initfromdata"></a>IOleObjectImpl::InitFromData  
 Inicializa o controle de dados selecionada.  
  
```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentários  
 Consulte [IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="isuptodate"></a>IOleObjectImpl::IsUpToDate  
 Verifica se o controle é atualizado.  
  
```
STDMETHOD(IsUpToDate)(void);
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
### <a name="remarks"></a>Comentários  
 Consulte [IOleObject::IsUpToDate](http://msdn.microsoft.com/library/windows/desktop/ms686624) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo  
 Chamado por [DoVerbDiscardUndo](#doverbdiscardundo) depois que o estado de desfazer é descartado.  
  
```
HRESULT OnPostVerbDiscardUndo();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
### <a name="remarks"></a>Comentários  
 Substitua esse método com o código a que ser executado depois que o estado de desfazer é descartado.  
  
##  <a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide  
 Chamado por [DoVerbHide](#doverbhide) depois que o controle está oculto.  
  
```
HRESULT OnPostVerbHide();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
### <a name="remarks"></a>Comentários  
 Substitua esse método com o código a que ser executado depois que o controle está oculto.  
  
##  <a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate  
 Chamado por [DoVerbInPlaceActivate](#doverbinplaceactivate) depois que o controle é ativado em vigor.  
  
```
HRESULT OnPostVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
### <a name="remarks"></a>Comentários  
 Substitua esse método com o código a que ser executado depois que o controle é ativado em vigor.  
  
##  <a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbOpen  
 Chamado por [DoVerbOpen](#doverbopen) depois que o controle foi aberto para edição em uma janela separada.  
  
```
HRESULT OnPostVerbOpen();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
### <a name="remarks"></a>Comentários  
 Substitua esse método com o código a que ser executado depois que o controle foi aberto para edição em uma janela separada.  
  
##  <a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow  
 Chamado por [DoVerbShow](#doverbshow) depois que o controle foi feito visível.  
  
```
HRESULT OnPostVerbShow();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
### <a name="remarks"></a>Comentários  
 Substitua esse método com o código a que ser executado depois que o controle foi feito visível.  
  
##  <a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate  
 Chamado por [DoVerbUIActivate](#doverbuiactivate) após a ativação de interface do usuário do controle.  
  
```
HRESULT OnPostVerbUIActivate();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
### <a name="remarks"></a>Comentários  
 Substitua esse método com o código a que ser executado após a ativação de interface do usuário do controle.  
  
##  <a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo  
 Chamado por [DoVerbDiscardUndo](#doverbdiscardundo) antes de desfazer o estado é descartado.  
  
```
HRESULT OnPreVerbDiscardUndo();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
### <a name="remarks"></a>Comentários  
 Para impedir que o estado de desfazer está sendo descartado, substitua este método para retornar um erro HRESULT.  
  
##  <a name="onpreverbhide"></a>IOleObjectImpl::OnPreVerbHide  
 Chamado por [DoVerbHide](#doverbhide) antes que o controle está oculto.  
  
```
HRESULT OnPreVerbHide();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
### <a name="remarks"></a>Comentários  
 Para impedir que o controle oculto, ignore este método para retornar um erro HRESULT.  
  
##  <a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreVerbInPlaceActivate  
 Chamado por [DoVerbInPlaceActivate](#doverbinplaceactivate) antes que o controle é ativado em vigor.  
  
```
HRESULT OnPreVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
### <a name="remarks"></a>Comentários  
 Para impedir que o controle está sendo ativado no local, substitua este método para retornar um erro HRESULT.  
  
##  <a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbOpen  
 Chamado por [DoVerbOpen](#doverbopen) antes que o controle foi aberto para edição em uma janela separada.  
  
```
HRESULT OnPreVerbOpen();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
### <a name="remarks"></a>Comentários  
 Para impedir que o controle que está sendo aberto para edição em uma janela separada, substitua este método para retornar um erro HRESULT.  
  
##  <a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow  
 Chamado por [DoVerbShow](#doverbshow) antes que o controle foi feito visível.  
  
```
HRESULT OnPreVerbShow();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
### <a name="remarks"></a>Comentários  
 Para impedir que o controle está sendo feita visível, ignore este método para retornar um erro HRESULT.  
  
##  <a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate  
 Chamado por [DoVerbUIActivate](#doverbuiactivate) antes de interface do usuário do controle foi ativado.  
  
```
HRESULT OnPreVerbUIActivate();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
### <a name="remarks"></a>Comentários  
 Para impedir a interface do usuário do controle que está sendo ativado, substitua este método para retornar um erro HRESULT.  
  
##  <a name="setclientsite"></a>IOleObjectImpl::SetClientSite  
 Informa o controle sobre seu site do cliente no contêiner.  
  
```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```  
  
### <a name="remarks"></a>Comentários  
 O método retorna `S_OK`.  
  
 Consulte [IOleObject::SetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms684013) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme  
 Recomenda um esquema de cores para o aplicativo do controle, se houver.  
  
```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentários  
 Consulte [IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setextent"></a>IOleObjectImpl::SetExtent  
 Define a extensão da área de exibição do controle.  
  
```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>Comentários  
 Caso contrário, `SetExtent` armazena o valor apontado por `psizel` no membro de dados da classe de controle [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent). Esse valor é em unidades HIMETRIC (0,01 milímetro por unidade).  
  
 Se o controle de membro de dados da classe [CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) é **TRUE**, `SetExtent` também armazena o valor apontado por `psizel` no membro de dados da classe de controle [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural).  
  
 Se o controle de membro de dados da classe [CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) é **TRUE**, `SetExtent` chamadas `SendOnDataChange` e `SendOnViewChange` para notificar o comunicado de todos os coletores registrados com o proprietário de aviso que o tamanho do controle foi alterado.  
  
 Consulte [IOleObject::SetExtent](http://msdn.microsoft.com/library/windows/desktop/ms694330) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="sethostnames"></a>IOleObjectImpl::SetHostNames  
 Informa o controle os nomes do aplicativo de contêiner e do documento contêiner.  
  
```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
### <a name="remarks"></a>Comentários  
 Consulte [IOleObject::SetHostNames](http://msdn.microsoft.com/library/windows/desktop/ms680642) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setmoniker"></a>IOleObjectImpl::SetMoniker  
 Informa ao controle qual é seu identificador de origem.  
  
```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna **E_NOTIMPL**.  
  
### <a name="remarks"></a>Comentários  
 Consulte [IOleObject::SetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679671) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="unadvise"></a>IOleObjectImpl::Unadvise  
 Exclui a conexão de consultoria armazenado na classe de controle `m_spOleAdviseHolder` membro de dados.  
  
```
STDMETHOD(Unadvise)(DWORD dwConnection);
```  
  
### <a name="remarks"></a>Comentários  
 Consulte [IOleObject::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms693749) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="update"></a>IOleObjectImpl::Update  
 Atualiza o controle.  
  
```
STDMETHOD(Update)(void);
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna `S_OK`.  
  
### <a name="remarks"></a>Comentários  
 Consulte [IOleObject::Update](http://msdn.microsoft.com/library/windows/desktop/ms679699) no [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Classe CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Interfaces de controles ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Visão geral da classe](../../atl/atl-class-overview.md)
