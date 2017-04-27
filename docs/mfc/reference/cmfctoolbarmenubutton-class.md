---
title: Classe CMFCToolBarMenuButton | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarMenuButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CMFCToolBarMenuButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CompareWith
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CopyFrom
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CreateFromMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CreateMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::CreatePopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::EnableQuickCustomize
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetCommands
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetImageRect
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetPaletteRows
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::GetPopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::HasButton
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::HaveHotBorder
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsBorder
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsClickedOnMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsDroppedDown
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsEmptyMenuAllowed
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsExclusive
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsMenuPaletteMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsQuickMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::IsTearOffMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnAfterCreatePopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnBeforeDrag
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnCalculateSize
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnCancelMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnChangeParentWnd
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnClick
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnClickMenuItem
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnContextHelp
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnDraw
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OnDrawOnCustomizeList
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::OpenPopupMenu
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::ResetImageToDefault
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SaveBarState
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::Serialize
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetACCData
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetMenuOnly
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetMenuPaletteMode
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetMessageWnd
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetRadio
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::SetTearOff
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::DrawDocumentIcon
- AFXTOOLBARMENUBUTTON/CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw
dev_langs:
- C++
helpviewer_keywords:
- CMFCToolBarMenuButton class
ms.assetid: cfa50176-7e4b-4527-9904-86a1b48fc1bc
caps.latest.revision: 31
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
ms.openlocfilehash: a06fd323862c6869463b4db0977816b5707c3e18
ms.lasthandoff: 02/25/2017

---
# <a name="cmfctoolbarmenubutton-class"></a>Classe CMFCToolBarMenuButton
Um botão de barra de ferramentas que contém um menu pop-up.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class CMFCToolBarMenuButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::CMFCToolBarMenuButton](#cmfctoolbarmenubutton)|Constrói um objeto `CMFCToolBarMenuButton`.|  
  
### <a name="public-methods"></a>Métodos Públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::CompareWith](#comparewith)|Compara essa instância com fornecidas `CMFCToolBarButton` objeto. (Substitui [CMFCToolBarButton::CompareWith](../../mfc/reference/cmfctoolbarbutton-class.md#comparewith).)|  
|[CMFCToolBarMenuButton::CopyFrom](#copyfrom)|Copia as propriedades de outro botão de barra de ferramentas para o botão atual. (Substitui [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|[CMFCToolBarMenuButton::CreateFromMenu](#createfrommenu)|Inicializa o menu da barra de ferramentas de um identificador de menu do Windows.|  
|[CMFCToolBarMenuButton::CreateMenu](#createmenu)|Cria um menu do Windows que consiste em comandos no menu Ferramentas. Retorna um identificador para o menu do Windows.|  
|[CMFCToolBarMenuButton::CreatePopupMenu](#createpopupmenu)|Cria um objeto do menu pop-up ( [CMFCPopupMenu classe](../../mfc/reference/cmfcpopupmenu-class.md)) para exibir o menu da barra de ferramentas.|  
|[CMFCToolBarMenuButton::EnableQuickCustomize](#enablequickcustomize)||  
|[CMFCToolBarMenuButton::GetCommands](#getcommands)|Fornece acesso somente leitura para a lista de comandos no menu Ferramentas.|  
|[CMFCToolBarMenuButton::GetImageRect](#getimagerect)|Recupera o retângulo delimitador para a imagem do botão.|  
|[CMFCToolBarMenuButton::GetPaletteRows](#getpaletterows)|Retorna o número de linhas no menu pop-up quando o menu estiver no modo de paleta.|  
|[CMFCToolBarMenuButton::GetPopupMenu](#getpopupmenu)|Retorna um ponteiro para o objeto de menu pop-up que é associado ao botão.|  
|[CMFCToolBarMenuButton::HasButton](#hasbutton)||  
|[CMFCToolBarMenuButton::HaveHotBorder](#havehotborder)|Determina se uma borda do botão é exibida quando um usuário seleciona o botão. (Substitui [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|  
|[CMFCToolBarMenuButton::IsBorder](#isborder)||  
|[CMFCToolBarMenuButton::IsClickedOnMenu](#isclickedonmenu)||  
|[CMFCToolBarMenuButton::IsDroppedDown](#isdroppeddown)|Determina se o menu pop-up é exibido.|  
|[CMFCToolBarMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|Chamado pela estrutura para determinar se um usuário pode abrir um submenu do item de menu selecionado.|  
|[CMFCToolBarMenuButton::IsExclusive](#isexclusive)|Determina se o botão está no modo exclusivo, ou seja, se o menu pop-up permanece aberto mesmo quando o usuário move o ponteiro sobre outro botão ou barra de ferramentas.|  
|[CMFCToolBarMenuButton::IsMenuPaletteMode](#ismenupalettemode)|Determina se o menu pop-up está no modo de paleta.|  
|[CMFCToolBarMenuButton::IsQuickMode](#isquickmode)||  
|[CMFCToolBarMenuButton::IsTearOffMenu](#istearoffmenu)|Determina se o menu pop-up tem uma barra destacável.|  
|[CMFCToolBarMenuButton::OnAfterCreatePopupMenu](#onaftercreatepopupmenu)||  
|[CMFCToolBarMenuButton::OnBeforeDrag](#onbeforedrag)|Especifica se o botão pode ser arrastado. (Substitui [CMFCToolBarButton::OnBeforeDrag](../../mfc/reference/cmfctoolbarbutton-class.md#onbeforedrag).)|  
|[CMFCToolBarMenuButton::OnCalculateSize](#oncalculatesize)|Chamado pela estrutura para calcular o tamanho do botão para o contexto de dispositivo especificado e o estado de encaixe. (Substitui [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|[CMFCToolBarMenuButton::OnCancelMode](#oncancelmode)|Chamado pela estrutura para lidar com a [WM_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) mensagem. (Substitui [CMFCToolBarButton::OnCancelMode](../../mfc/reference/cmfctoolbarbutton-class.md#oncancelmode).)|  
|[CMFCToolBarMenuButton::OnChangeParentWnd](#onchangeparentwnd)|Chamado pela estrutura quando o botão é inserido em uma nova barra de ferramentas. (Substitui [CMFCToolBarButton::OnChangeParentWnd](cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCToolBarMenuButton::OnClick](#onclick)|Chamado pela estrutura quando o usuário clica no botão do mouse. (Substitui [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCToolBarMenuButton::OnClickMenuItem](#onclickmenuitem)|Chamado pela estrutura quando o usuário seleciona um item no menu pop-up.|  
|[CMFCToolBarMenuButton::OnContextHelp](#oncontexthelp)|Chamado pela estrutura quando a barra de ferramentas do pai manipula um `WM_HELPHITTEST` mensagem. (Substitui [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|  
|[CMFCToolBarMenuButton::OnDraw](#ondraw)|Chamado pela estrutura para desenhar o botão usando as opções e estilos especificados. (Substitui [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|[CMFCToolBarMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Chamado pela estrutura para desenhar o botão no **comandos** painel do **personalizar** caixa de diálogo. (Substitui [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCToolBarMenuButton::OpenPopupMenu](#openpopupmenu)|Chamado pela estrutura quando o usuário abre o menu pop-up.|  
|[CMFCToolBarMenuButton::ResetImageToDefault](#resetimagetodefault)|Define o valor padrão a imagem que está associada ao botão. (Substitui [CMFCToolBarButton::ResetImageToDefault](../../mfc/reference/cmfctoolbarbutton-class.md#resetimagetodefault).)|  
|[CMFCToolBarMenuButton::SaveBarState](#savebarstate)|Salva o estado do botão da barra de ferramentas. (Substitui [CMFCToolBarButton::SaveBarState](../../mfc/reference/cmfctoolbarbutton-class.md#savebarstate).)|  
|[CMFCToolBarMenuButton::Serialize](#serialize)|Lê esse objeto de um arquivo ou grava em um arquivo morto. (Substitui [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|[CMFCToolBarMenuButton::SetACCData](#setaccdata)|Preenche o fornecido `CAccessibilityData` objeto com dados de acessibilidade do botão da barra de ferramentas. (Substitui [CMFCToolBarButton::SetACCData](../../mfc/reference/cmfctoolbarbutton-class.md#setaccdata).)|  
|[CMFCToolBarMenuButton::SetMenuOnly](#setmenuonly)|Especifica se o botão pode ser adicionado à barra de ferramentas.|  
|[CMFCToolBarMenuButton::SetMenuPaletteMode](#setmenupalettemode)|Especifica se o menu pop-up está no modo de paleta.|  
|[CMFCToolBarMenuButton::SetMessageWnd](#setmessagewnd)||  
|[CMFCToolBarMenuButton::SetRadio](#setradio)|Força o botão de menu da barra de ferramentas para exibir um ícone indicando que ela está selecionada.|  
|[CMFCToolBarMenuButton::SetTearOff](#settearoff)|Especifica um destacável ID da barra do menu pop-up.|  
  
### <a name="protected-methods"></a>Métodos Protegidos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::DrawDocumentIcon](#drawdocumenticon)|Desenha um ícone no botão de menu.|  
  
### <a name="data-members"></a>Membros de Dados  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw](#m_balwayscallownerdraw)|Se `TRUE`, a estrutura chama sempre [CFrameWndEx::OnDrawMenuImage](../../mfc/reference/cframewndex-class.md#ondrawmenuimage) quando um botão é desenhado.|  
  
## <a name="remarks"></a>Comentários  
 Um `CMFCToolBarMenuButton` pode ser exibido como um menu, um item de menu com um submenu, um botão que executa um comando ou exibe um menu ou um botão que exibe apenas um menu. Determinar o comportamento e a aparência do botão de menu especificando parâmetros, como a imagem, texto, o identificador do menu e ID que está associado com o botão no construtor do comando `CMFCToolbarMenuButton::CMFCToolbarMenuButton`.  
  
 Uma classe personalizada derivada do `CMFCToolbarMenuButton` classe deve usar o [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) macro. O [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate) macro gera um erro quando o aplicativo é fechado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como configurar um `CMFCToolBarMenuButton` objeto. O código ilustra como especificar que o menu suspenso está no modo de paleta e especifique a ID para a barra destacável que é criada quando o usuário arrasta o botão de menu de uma barra de menus. Este trecho de código é parte do [exemplo Word Pad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad n º&10;](../../mfc/reference/codesnippet/cpp/cmfctoolbarmenubutton-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 [CObject](cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** afxtoolbarmenubutton.h  
  
##  <a name="cmfctoolbarmenubutton"></a>CMFCToolBarMenuButton::CMFCToolBarMenuButton  
 Constrói um objeto `CMFCToolBarMenuButton`.  
  
```  
CMFCToolBarMenuButton();
CMFCToolBarMenuButton(const CMFCToolBarMenuButton& src);

CMFCToolBarMenuButton(
    UINT uiID,  
    HMENU hMenu,  
    int iImage,  
    LPCTSTR lpszText=NULL,  
    BOOL bUserButton=FALSE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `src`  
 Existente `CMFCToolBarMenuButton` o objeto a ser copiado para isso `CMFCToolBarMenuButton` objeto.  
  
 [in] `uiID`  
 A ID do comando a ser executada quando um usuário clica no botão. ou ( `UINT`) -1 para um botão de menu que não executa um comando diretamente.  
  
 [in] `hMenu`  
 Um identificador para um menu. ou `NULL` se o botão não tem um menu.  
  
 [in] `iImage`  
 Índice da imagem do botão; ou -1 se esse botão não tem um ícone ou usa o ícone para o comando especificado por `uiID`. O índice é o mesmo para cada `CMFCToolBarImages` objeto em seu aplicativo.  
  
 [in] `lpszText`  
 O texto do botão de menu da barra de ferramentas.  
  
 [in] `bUserButton`  
 `TRUE`Se o botão exibe uma imagem definidas pelo usuário; `FALSE` se o botão exibe uma imagem predefinida associada com o comando especificado por `uiID`.  
  
### <a name="remarks"></a>Comentários  
 Se `uiID` é válido ID do comando, o botão executa esse comando quando o usuário clica nele. Se `hMenu` é um identificador válido do menu, o botão fornece um menu suspenso quando ele for exibido na barra de ferramentas ou um submenu quando ele for exibido em um menu. Se ambos os `uiID` e `hMenu` são válidas, o botão é um botão de divisão com uma parte que executará o comando quando o usuário clica nele e uma parte com uma seta para baixo que serão suspensos um menu quando o usuário clica nele. No entanto, se `hMenu` for válido, um usuário não será capaz de clicar no botão para executar um comando quando o botão é inserido em um menu.  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como criar um objeto de `CMFCToolBarMenuButton` classe. Este trecho de código é parte do [exemplo Word Pad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad n º&9;](../../mfc/reference/codesnippet/cpp/cmfctoolbarmenubutton-class_2.cpp)]  
  
##  <a name="comparewith"></a>CMFCToolBarMenuButton::CompareWith  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CompareWith(const CMFCToolBarButton& other) const;  
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `other`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="copyfrom"></a>CMFCToolBarMenuButton::CopyFrom  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `src`  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="createfrommenu"></a>CMFCToolBarMenuButton::CreateFromMenu  
 Inicializa o menu da barra de ferramentas de um identificador de menu do Windows.  
  
```  
virtual void CreateFromMenu(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `hMenu`  
 Um identificador para um menu.  
  
### <a name="remarks"></a>Comentários  
 Um botão de menu da barra de ferramentas pode exibir um submenu da lista suspensa.  
  
 O framework chama esse método para inicializar os comandos no submenu em um menu.  
  
##  <a name="createmenu"></a>CMFCToolBarMenuButton::CreateMenu  
 Cria um menu que consiste em comandos no menu Ferramentas. Retorna um identificador para o menu.  
  
```  
virtual HMENU CreateMenu() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um identificador para o menu se sucesso. `NULL`Se a lista de comandos associados com o botão de menu da barra de ferramentas está vazia.  
  
### <a name="remarks"></a>Comentários  
 Você pode substituir esse método em uma classe derivada para personalizar a maneira como o menu é gerado.  
  
##  <a name="createpopupmenu"></a>CMFCToolBarMenuButton::CreatePopupMenu  
 Cria um `CMFCPopupMenu` objeto para exibir o menu da barra de ferramentas.  
  
```  
virtual CMFCPopupMenu* CreatePopupMenu();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um ponteiro para um `CMFCPopupMenu` objeto que exibe o menu suspenso associado ao botão de menu da barra de ferramentas.  
  
### <a name="remarks"></a>Comentários  
 Este método é chamado pela estrutura para preparar a exibição do menu suspenso associado ao botão.  
  
 A implementação padrão simplesmente constrói e retorna um novo `CMFCPopupMenu` objeto. Substitua este método se você quiser usar um tipo derivado de [CMFCPopupMenu classe](cmfcpopupmenu-class.md) ou executar a inicialização adicional.  
  
##  <a name="drawdocumenticon"></a>CMFCToolBarMenuButton::DrawDocumentIcon  
 Desenha um ícone do documento no botão de menu.  
  
```  
void DrawDocumentIcon(
    CDC* pDC,  
    const CRect& rectImage,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pDC`  
 Um ponteiro para o contexto do dispositivo.  
  
 [in] `rectImage`  
 Coordenadas da imagem delimitadora retângulo.  
  
 [in] `hIcon`  
 Um identificador para o ícone.  
  
### <a name="remarks"></a>Comentários  
 Esse método usa um ícone de documento e desenha no botão de menu, centralizado na área especificada pelo `rectImage`.  
  
##  <a name="enablequickcustomize"></a>CMFCToolBarMenuButton::EnableQuickCustomize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void EnableQuickCustomize();
```  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="hasbutton"></a>CMFCToolBarMenuButton::HasButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasButton() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="havehotborder"></a>CMFCToolBarMenuButton::HaveHotBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="isborder"></a>CMFCToolBarMenuButton::IsBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsBorder() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="isclickedonmenu"></a>CMFCToolBarMenuButton::IsClickedOnMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsClickedOnMenu() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="isquickmode"></a>CMFCToolBarMenuButton::IsQuickMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsQuickMode();
```  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="getcommands"></a>CMFCToolBarMenuButton::GetCommands  
 Fornece acesso somente leitura para a lista de comandos no menu Ferramentas.  
  
```  
const CObList& GetCommands() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 Referência a uma constante para um [CObList classe](../../mfc/reference/coblist-class.md) objeto, que contém uma coleção de [CMFCToolBarButton classe](../../mfc/reference/cmfctoolbarbutton-class.md) objetos.  
  
### <a name="remarks"></a>Comentários  
 Um botão de menu da barra de ferramentas pode exibir um submenu. Você pode fornecer a lista de comandos no submenu no construtor ou em [CMFCToolBarMenuButton::CreateFromMenu](#createfrommenu) como um identificador para um menu ( `HMENU`). O menu é convertido em uma lista de objetos que são derivados de [CMFCToolBarButton classe](../../mfc/reference/cmfctoolbarbutton-class.md) e armazenados em interno `CObList` objeto. Você pode acessar essa lista, chamando esse método.  
  
##  <a name="getimagerect"></a>CMFCToolBarMenuButton::GetImageRect  
 Recupera o retângulo delimitador para a imagem do botão.  
  
```  
void GetImageRect(CRect& rectImage);
```  
  
### <a name="parameters"></a>Parâmetros  
 [out] `rectImage`  
 Uma referência a um `CRect` objeto que recebe as coordenadas da imagem delimitadora retângulo.  
  
##  <a name="getpaletterows"></a>CMFCToolBarMenuButton::GetPaletteRows  
 Retorna o número de linhas no menu suspenso quando o menu estiver no modo de paleta.  
  
```  
int GetPaletteRows() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 O número de linhas na paleta.  
  
### <a name="remarks"></a>Comentários  
 Quando o botão de menu é definido para o modo de paleta, itens de menu serão exibidos em várias colunas com apenas um número limitado de linhas. Chame esse método para obter o número de linhas. Você pode habilitar ou desabilitar o modo de paleta e especifique o número de linhas usando [CMFCToolBarMenuButton::SetMenuPaletteMode](#setmenupalettemode).  
  
##  <a name="getpopupmenu"></a>CMFCToolBarMenuButton::GetPopupMenu  
 Retorna um ponteiro para o [CMFCPopupMenu classe](../../mfc/reference/cmfcpopupmenu-class.md) objeto que representa a lista suspensa do botão.  
  
```  
CMFCPopupMenu* GetPopupMenu() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um ponteiro para um [CMFCPopupMenu classe](../../mfc/reference/cmfcpopupmenu-class.md) objeto que foi criado quando o framework desenhou o submenu do botão de menu da barra de ferramentas; `NULL` se nenhum submenu é exibido.  
  
### <a name="remarks"></a>Comentários  
 Quando um botão de menu exibe um menu suspenso, o botão cria uma [CMFCPopupMenu classe](../../mfc/reference/cmfcpopupmenu-class.md) objeto para representar o menu. Chame esse método para obter um ponteiro para o `CMFCPopupMenu` objeto. Você não deve armazenar o ponteiro retornado, porque ele é temporário e torna-se inválido quando o usuário fecha o menu suspenso.  
  
##  <a name="isdroppeddown"></a>CMFCToolBarMenuButton::IsDroppedDown  
 Indica se o menu pop-up é exibido no momento.  
  
```  
virtual BOOL IsDroppedDown() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se o botão de menu da barra de ferramentas exibe seu submenu; Caso contrário, `FALSE`.  
  
##  <a name="isemptymenuallowed"></a>CMFCToolBarMenuButton::IsEmptyMenuAllowed  
 Especifica se os itens de menu mostra submenus vazios.  
  
```  
virtual BOOL IsEmptyMenuAllowed() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se o framework abre um submenu do item de menu selecionado no momento, mesmo quando o submenu está vazio. Caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 O framework chama esse método quando um usuário tenta abrir o submenu do item de menu selecionado no momento. Se o submenu está vazio e `IsEmptyMenuAllowed` retorna `FALSE`, o submenu não será aberto.  
  
 Retorna a implementação padrão `FALSE`. Substitui esse método para personalizar esse comportamento.  
  
##  <a name="isexclusive"></a>CMFCToolBarMenuButton::IsExclusive  
 Indica se o botão está no modo exclusivo.  
  
```  
virtual BOOL IsExclusive() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se o botão estiver funcionando em modo exclusivo; Caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 Quando um usuário abre um menu pop-up para um botão e, em seguida, move o ponteiro do mouse sobre outro botão de barra de ferramentas ou menu, o menu pop-up é fechada, a menos que o botão está no modo exclusivo.  
  
 A implementação padrão sempre retorna `FALSE`. Substitua esse método em uma classe derivada se você quiser ativar o modo exclusivo.  
  
##  <a name="ismenupalettemode"></a>CMFCToolBarMenuButton::IsMenuPaletteMode  
 Determina se o menu suspenso está no modo de paleta.  
  
```  
BOOL IsMenuPaletteMode() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se o modo de paleta está habilitado, caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 Quando o botão de menu é definido para o modo de paleta, itens de menu aparecem em várias colunas com apenas um número limitado de linhas. Chame esse método para obter o número de linhas. Você pode habilitar ou desabilitar o modo de paleta chamando [CMFCToolBarMenuButton::SetMenuPaletteMode](#setmenupalettemode).  
  
##  <a name="istearoffmenu"></a>CMFCToolBarMenuButton::IsTearOffMenu  
 Indica se o menu suspenso tem uma barra destacável.  
  
```  
virtual BOOL IsTearOffMenu() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se o botão de menu da barra de ferramentas tem uma barra destacável; Caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 Para habilitar o recurso destacável e definir o destacável barra ID, chame [CMFCToolBarMenuButton::SetTearOff](#settearoff).  
  
##  <a name="m_balwayscallownerdraw"></a>CMFCToolBarMenuButton::m_bAlwaysCallOwnerDraw  
 Especifica se o framework chama sempre [CFrameWndEx::OnDrawMenuImage](../../mfc/reference/cframewndex-class.md#ondrawmenuimage) quando um botão é desenhado.  
  
```  
static BOOL m_bAlwaysCallOwnerDraw;  
```  
  
### <a name="remarks"></a>Comentários  
 Quando essa variável de membro é definido como `TRUE`, o botão sempre chama [CFrameWndEx::OnDrawMenuImage](../../mfc/reference/cframewndex-class.md#ondrawmenuimage) método para exibir a imagem do botão. Quando `m_bAlwaysCallOwnerDraw` é `FALSE`, no próprio botão desenha a imagem se a imagem é predefinida. Caso contrário, ele chama `OnDrawMenuImage`.  
  
##  <a name="onaftercreatepopupmenu"></a>CMFCToolBarMenuButton::OnAfterCreatePopupMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnAfterCreatePopupMenu();
```  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="onbeforedrag"></a>CMFCToolBarMenuButton::OnBeforeDrag  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnBeforeDrag() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="oncalculatesize"></a>CMFCToolBarMenuButton::OnCalculateSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pDC`  
 [in] `sizeDefault`  
 [in] `bHorz`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="oncancelmode"></a>CMFCToolBarMenuButton::OnCancelMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnCancelMode();
```  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarMenuButton::OnChangeParentWnd  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pWndParent`  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="onclick"></a>CMFCToolBarMenuButton::OnClick  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pWnd`  
 [in] `bDelay`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="onclickmenuitem"></a>CMFCToolBarMenuButton::OnClickMenuItem  
 Chamado pela estrutura quando o usuário seleciona um item no menu suspenso.  
  
```  
virtual BOOL OnClickMenuItem();
```  
  
### <a name="return-value"></a>Valor de retorno  
 `FALSE`Se a estrutura deve continuar menu padrão item processamento; Caso contrário, `TRUE`. A implementação padrão sempre retorna `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 Quando o usuário clica em um item de menu, o framework executa um comando que está associado esse item.  
  
 Para personalizar o processamento do item de menu, substitua `OnClickMenuItem` em uma classe derivada de `CMFCToolBarMenuButton` classe. Você também deve substituir [CFrameWndEx::OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu) e substitua os botões de menu que requerem processamento especial com instâncias da classe derivada.  
  
##  <a name="oncontexthelp"></a>CMFCToolBarMenuButton::OnContextHelp  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnContextHelp(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pWnd`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="ondraw"></a>CMFCToolBarMenuButton::OnDraw  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz = TRUE,  
    BOOL bCustomizeMode = FALSE,  
    BOOL bHighlight = FALSE,  
    BOOL bDrawBorder = TRUE,  
    BOOL bGrayDisabledButtons = TRUE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pDC`  
 [in] `rect`  
 [in] `pImages`  
 [in] `bHorz`  
 [in] `bCustomizeMode`  
 [in] `bHighlight`  
 [in] `bDrawBorder`  
 [in] `bGrayDisabledButtons`  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="ondrawoncustomizelist"></a>CMFCToolBarMenuButton::OnDrawOnCustomizeList  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pDC`  
 [in] `rect`  
 [in] `bSelected`  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="openpopupmenu"></a>CMFCToolBarMenuButton::OpenPopupMenu  
 Chamado pela estrutura quando o usuário abre o menu suspenso de um botão de menu da barra de ferramentas.  
  
```  
virtual BOOL OpenPopupMenu(CWnd* pWnd=NULL);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pWnd`  
 Especifica a janela que recebe os comandos do menu suspenso. Ele pode ser `NULL` somente se o botão de menu da barra de ferramentas tem uma janela pai.  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Quando um [CMFCPopupMenu classe](../../mfc/reference/cmfcpopupmenu-class.md) objeto foi criado e aberto com êxito; caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 Essa função é chamada pela estrutura quando o usuário abre um menu suspenso em um botão de menu da barra de ferramentas.  
  
##  <a name="resetimagetodefault"></a>CMFCToolBarMenuButton::ResetImageToDefault  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void ResetImageToDefault();
```  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="savebarstate"></a>CMFCToolBarMenuButton::SaveBarState  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SaveBarState();
```  
  
### <a name="remarks"></a>Comentários  
 O framework chama esse método quando ele cria um botão de barra de ferramentas como o resultado de uma operação de arrastar e soltar. Esse método chama o [CMFCPopupMenu::SaveState](../../mfc/reference/cmfcpopupmenu-class.md#savestate) método de nível superior menu pop-up, que faz com que o botão do pai do menu pop-up para recriar seu menu.  
  
##  <a name="serialize"></a>CMFCToolBarMenuButton::Serialize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `ar`  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="setaccdata"></a>CMFCToolBarMenuButton::SetACCData  
 Define os dados de acessibilidade para o elemento de faixa de opções.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parâmetros  
 `pParent`  
 A janela pai para o elemento de faixa de opções.  
  
 `data`  
 Os dados de acessibilidade para o elemento de faixa de opções.  
  
### <a name="return-value"></a>Valor de retorno  
 Sempre retorna `TRUE`.  
  
### <a name="remarks"></a>Comentários  
 Por padrão esse método define os dados de acessibilidade para o elemento de faixa de opções e sempre retornará `TRUE`. Substitua este método para definir os dados de acessibilidade e retornar um valor que indica êxito ou falha.  
  
##  <a name="setmenuonly"></a>CMFCToolBarMenuButton::SetMenuOnly  
 Especifica se o botão é desenhado como um botão de menu ou um botão de divisão quando ele tem uma ID de comando válido e um submenu.  
  
```  
void SetMenuOnly(BOOL bMenuOnly);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `bMenuOnly`  
 `TRUE`para mostrar esse botão como um botão de menu quando ele tem uma ID de comando válido e um submenu, `FALSE` para mostrar esse botão como um botão de divisão quando ele tem uma ID de comando válido e um submenu.  
  
### <a name="remarks"></a>Comentários  
 Normalmente, quando um botão de menu da barra de ferramentas tem um submenu e uma ID de comando, o menu parece ser um botão de divisão que tem um botão principal e um anexado botão de seta para baixo. Se você chamar esse método e `bMenuOnly` é `TRUE`, em vez disso, aparece o botão seja um botão de menu única com uma seta para baixo no botão. Quando o usuário clica na seta em qualquer modo, o submenu é aberto e quando o usuário clica a parte não seta do botão em qualquer modo, o framework executa o comando.  
  
##  <a name="setmenupalettemode"></a>CMFCToolBarMenuButton::SetMenuPaletteMode  
 Especifica se o menu suspenso está no modo de paleta.  
  
```  
void SetMenuPaletteMode(
    BOOL bMenuPaletteMode=TRUE,  
    int nPaletteRows=1);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `bMenuPaletteMode`  
 Especifica se o menu suspenso está no modo de paleta.  
  
 [in] `nPaletteRows`  
 Número de linhas na paleta.  
  
### <a name="remarks"></a>Comentários  
 No modo de paleta, todos os itens de menu são exibidos como uma paleta de várias colunas. Especifique o número de linhas usando `nPaletteRows`.  
  
##  <a name="setmessagewnd"></a>CMFCToolBarMenuButton::SetMessageWnd  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetMessageWnd(CWnd* pWndMessage);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pWndMessage`  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="setradio"></a>CMFCToolBarMenuButton::SetRadio  
 Define o botão de menu da barra de ferramentas para exibir um ícone de estilo de botão de opção quando estiver marcada.  
  
```  
virtual void SetRadio();
```  
  
### <a name="remarks"></a>Comentários  
 Quando o botão de menu é desenhado enquanto ele é verificado, ele chama [CMFCVisualManager::OnDrawMenuCheck](../../mfc/reference/cmfcvisualmanager-class.md#ondrawmenucheck) para desenhar um ícone de marca de seleção. Por padrão, `OnDrawMenuCheck` marca de seleção de estilo de solicitações que o Gerenciador visual atual desenha uma caixa de seleção do botão de menu. Depois de chamar esse método, o Gerenciador visual atual em vez disso, desenha uma marca de seleção de estilo de botão de opção no botão de menu. Essa alteração não pode ser desfeita.  
  
 Quando você chamar esse método e o botão de menu está sendo exibido atualmente, ela será atualizada.  
  
##  <a name="settearoff"></a>CMFCToolBarMenuButton::SetTearOff  
 Especifica a ID da barra destacável do menu suspenso.  
  
```  
virtual void SetTearOff(UINT uiBarID);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `uiBarID`  
 Especifica um destacável nova barra ID.  
  
### <a name="remarks"></a>Comentários  
 Chame esse método para especificar a ID para a barra destacável que é criada quando o usuário arrasta o botão de menu de uma barra de menus. Se o `uiBarID` for 0, o usuário não é possível separar o botão de menu.  
  
 Chamar [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus) para habilitar o recurso destacável menu em seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 [Gráfico de hierarquia](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Classe CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)   
 [Classe CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)