---
title: Classe CMFCColorDialog | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
dev_langs:
- C++
helpviewer_keywords:
- CMFCColorDialog::m_CurrentColor data member
- CMFCColorDialog::m_pPropSheet data member
- CMFCColorDialog::m_btnColorSelect data member
- CMFCColorDialog class
- CMFCColorDialog::m_wndColors data member
- CMFCColorDialog::m_bIsMyPalette data member
- CMFCColorDialog::m_pColourSheetTwo data member
- CMFCColorDialog::m_NewColor data member
- CMFCColorDialog::m_pPalette data member
- CMFCColorDialog::m_wndStaticPlaceHolder data member
- CMFCColorDialog::m_pColourSheetOne data member
- CMFCColorDialog::m_hcurPicker data member
- CMFCColorDialog::PreTranslateMessage method
- CMFCColorDialog::m_bPickerMode data member
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
caps.latest.revision: 30
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
ms.openlocfilehash: ac621157e0fcb5bcabef2ae8f367a1b141b4ace0
ms.lasthandoff: 02/25/2017

---
# <a name="cmfccolordialog-class"></a>Classe CMFCColorDialog
O `CMFCColorDialog` classe representa uma caixa de diálogo de seleção de cor.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class CMFCColorDialog : public CDialogEx  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|Constrói um objeto `CMFCColorDialog`.|  
|`CMFCColorDialog::~CMFCColorDialog`|Destruidor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CMFCColorDialog::GetColor](#getcolor)|Retorna a cor selecionada atual.|  
|[CMFCColorDialog::GetPalette](#getpalette)|Retorna a paleta de cores.|  
|`CMFCColorDialog::PreTranslateMessage`|Converte as mensagens de janela antes de serem distribuídos para o [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) e [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funções do Windows. Para sintaxe e obter mais informações, consulte [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Substitui `CDialogEx::PreTranslateMessage`.)|  
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Uma paleta deriva da paleta do sistema.|  
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Define a cor selecionada atual.|  
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Define a cor mais equivalente a um valor RGB especificado.|  
|[CMFCColorDialog::SetPageOne](#setpageone)|Seleciona um valor RGB para a primeira página de propriedade.|  
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Seleciona um valor RGB para a segunda página de propriedade.|  
  
### <a name="protected-data-members"></a>Membros de dados protegidos  
  
|Nome|Descrição|  
|----------|-----------------|  
|`m_bIsMyPalette`|`TRUE`Se a caixa de diálogo de seleção de cor usa sua própria paleta de cores, ou `FALSE` se a caixa de diálogo usa uma paleta especificada no `CMFCColorDialog` construtor.|  
|`m_bPickerMode`|`TRUE`enquanto o usuário está selecionando uma cor da caixa de diálogo de seleção; Caso contrário, `FALSE`.|  
|`m_btnColorSelect`|O botão de cor que o usuário tiver selecionado.|  
|`m_CurrentColor`|A cor selecionada atualmente.|  
|`m_hcurPicker`|O cursor é usado para selecionar uma cor.|  
|`m_NewColor`|O potencial cor selecionada, que pode ser selecionado permanentemente ou revertido para a cor original.|  
|`m_pColourSheetOne`|Um ponteiro para a primeira página de propriedade da folha de propriedade de seleção de cor.|  
|`m_pColourSheetTwo`|Um ponteiro para a segunda página de propriedade da folha de propriedade de seleção de cor.|  
|`m_pPalette`|A paleta lógica atual.|  
|`m_pPropSheet`|Um ponteiro para a folha de propriedades para a caixa de diálogo de seleção de cor.|  
|`m_wndColors`|Um objeto de controle de seletor de cores.|  
|`m_wndStaticPlaceHolder`|Um controle estático é um espaço reservado para a folha de propriedades de selecionador de cores.|  
  
## <a name="remarks"></a>Comentários  
 A caixa de diálogo de seleção de cor é exibida como uma folha de propriedades com duas páginas. Na primeira página, você deve selecionar uma cor padrão da paleta do sistema; na segunda página, você deve selecionar uma cor personalizada.  
  
 Você pode construir um `CMFCColorDialog` do objeto na pilha e, em seguida, chame `DoModal`, passando a cor inicial como um parâmetro para o `CMFCColorDialog` construtor. A caixa de diálogo de seleção de cor, em seguida, cria várias [CMFCColorPickerCtrl classe](../../mfc/reference/cmfccolorpickerctrl-class.md) objetos para lidar com cada paleta de cores.  
  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CDialogEx](../../mfc/reference/cdialogex-class.md)  
  
 [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como configurar uma caixa de diálogo de cor usando vários métodos na `CMFCColorDialog` classe. O exemplo mostra como definir o atual e as novas cores da caixa de diálogo e como definir os componentes vermelhos, verde e azuis de uma cor selecionada nas páginas de duas propriedades da caixa de diálogo de cor. Este exemplo é parte do [exemplo novos controles](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_NewControls n º&3;](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** afxcolordialog.h  
  
##  <a name="cmfccolordialog"></a>CMFCColorDialog::CMFCColorDialog  
 Constrói um objeto `CMFCColorDialog`.  
  
```  
CMFCColorDialog(
    COLORREF clrInit=0,  
    DWORD dwFlags=0,  
    CWnd* pParentWnd=NULL,  
    HPALETTE hPal=NULL);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `clrInit`  
 A seleção de cor padrão. Se nenhum valor for especificado, o padrão é RGB(0,0,0) (preto).  
  
 [in] `dwFlags`  
 (Reservado).  
  
 [in] `pParentWnd`  
 Um ponteiro para a janela do pai ou o proprietário da caixa de diálogo.  
  
 [in] `hPal`  
 Um identificador para uma paleta de cores.  
  
### <a name="return-value"></a>Valor de retorno  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="getcolor"></a>CMFCColorDialog::GetColor  
 Recupera a cor selecionada pelo usuário na caixa de diálogo cor.  
  
```  
COLORREF GetColor() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que contém informações para a cor selecionada na caixa de diálogo de cor RGB.  
  
### <a name="remarks"></a>Comentários  
 Chame essa função depois de chamar o `DoModal` método.  
  
##  <a name="getpalette"></a>CMFCColorDialog::GetPalette  
 Recupera a paleta de cores que está disponível na caixa de diálogo de cor atual.  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um ponteiro para o `CPalette` que foi especificado no objeto de `CMFCColorDialog` construtor.  
  
### <a name="remarks"></a>Comentários  
 A paleta de cores Especifica as cores que o usuário pode escolher.  
  
##  <a name="rebuildpalette"></a>CMFCColorDialog::RebuildPalette  
 Uma paleta deriva da paleta do sistema.  
  
```  
void RebuildPalette();
```  
  
##  <a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor  
 Define a cor atual da caixa de diálogo.  
  
```  
void SetCurrentColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `rgb`  
 Um valor de cor RGB  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="setnewcolor"></a>CMFCColorDialog::SetNewColor  
 Define a cor atual para a cor na paleta atual mais semelhante.  
  
```  
void SetNewColor(COLORREF rgb);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `rgb`  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) que especifica uma cor RGB.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="setpageone"></a>CMFCColorDialog::SetPageOne  
 Especifica explicitamente os componentes vermelhos, verde e azuis de uma cor selecionada na primeira página de propriedade de uma caixa de diálogo de cor.  
  
```  
void SetPageOne(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `R`  
 Especifica o componente vermelho do valor RGB.  
  
 [in] `G`  
 Especifica o componente verde do valor RGB.  
  
 [in] `B`  
 Especifica o componente azul do valor RGB.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="setpagetwo"></a>CMFCColorDialog::SetPageTwo  
 Especifica explicitamente os componentes vermelhos, verde e azuis de uma cor selecionada na segunda página de propriedade de uma caixa de diálogo de cor.  
  
```  
void SetPageTwo(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `R`  
 Especifica um componente vermelho do valor RGB  
  
 [in] `G`  
 Especifica um componente verde de um valor RGB  
  
 [in] `B`  
 Especifica um componente azul de um valor RGB  
  
### <a name="remarks"></a>Comentários  
  
## <a name="see-also"></a>Consulte também  
 [Gráfico de hierarquia](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)
