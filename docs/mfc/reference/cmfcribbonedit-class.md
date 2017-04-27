---
title: Classe CMFCRibbonEdit | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CanBeStretched
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CopyFrom
- AFXRIBBONEDIT/CMFCRibbonEdit::CreateEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::DestroyCtrl
- AFXRIBBONEDIT/CMFCRibbonEdit::DropDownList
- AFXRIBBONEDIT/CMFCRibbonEdit::EnableSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::GetCompactSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::GetIntermediateSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::GetWidth
- AFXRIBBONEDIT/CMFCRibbonEdit::HasCompactMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasFocus
- AFXRIBBONEDIT/CMFCRibbonEdit::HasLargeMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::IsHighlighted
- AFXRIBBONEDIT/CMFCRibbonEdit::OnAfterChangeRect
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDraw
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawLabelAndImage
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawOnList
- AFXRIBBONEDIT/CMFCRibbonEdit::OnEnable
- AFXRIBBONEDIT/CMFCRibbonEdit::OnHighlight
- AFXRIBBONEDIT/CMFCRibbonEdit::OnKey
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonDown
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonUp
- AFXRIBBONEDIT/CMFCRibbonEdit::OnRTLChanged
- AFXRIBBONEDIT/CMFCRibbonEdit::OnShow
- AFXRIBBONEDIT/CMFCRibbonEdit::Redraw
- AFXRIBBONEDIT/CMFCRibbonEdit::SetACCData
- AFXRIBBONEDIT/CMFCRibbonEdit::SetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::SetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::SetWidth
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonEdit class
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
caps.latest.revision: 25
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
ms.openlocfilehash: 03eb96bf971b53a2100e6f93bac2f0641f0298e1
ms.lasthandoff: 02/25/2017

---
# <a name="cmfcribbonedit-class"></a>Classe CMFCRibbonEdit
Implementa um controle de edição que está localizado em uma barra de faixa de opções.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class CMFCRibbonEdit : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Constrói um objeto `CMFCRibbonEdit`.|  
  
### <a name="public-methods"></a>Métodos Públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CMFCRibbonEdit::CanBeStretched](#canbestretched)|Indica se a altura do `CMFCRibbonEdit` controle pode aumentar verticalmente até a altura de uma linha de faixa de opções.|  
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|Constrói um objeto `CMFCRibbonEdit`.|  
|[CMFCRibbonEdit::CopyFrom](#copyfrom)|Copia o estado especificado `CMFCRibbonEdit` objeto atual `CMFCRibbonEdit` objeto.|  
|[CMFCRibbonEdit::CreateEdit](#createedit)|Cria uma nova caixa de texto para o `CMFCRibbonEdit` objeto.|  
|[CMFCRibbonEdit::DestroyCtrl](#destroyctrl)|Destrói o `CMFCRibbonEdit` objeto.|  
|[CMFCRibbonEdit::DropDownList](#dropdownlist)|Exibe uma caixa de listagem.|  
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|Habilita e define o intervalo do botão de rotação da caixa de texto.|  
|[CMFCRibbonEdit::GetCompactSize](#getcompactsize)|Recupera o tamanho compacto do `CFMCRibbonEdit` objeto.|  
|[CMFCRibbonEdit::GetEditText](#getedittext)|Recupera o texto na caixa de texto.|  
|[CMFCRibbonEdit::GetIntermediateSize](#getintermediatesize)|Recupera o tamanho intermediário do `CMFCRibbonEdit` objeto.|  
|[CMFCRibbonEdit::GetTextAlign](#gettextalign)|Recupera o alinhamento do texto na caixa de texto.|  
|[CMFCRibbonEdit::GetWidth](#getwidth)|Recupera a largura, em pixels, do `CMFCRibbonEdit` controle.|  
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|Indica se a exibição de tamanho para o `CMFCRibbonEdit` controle pode ser compacto.|  
|[CMFCRibbonEdit::HasFocus](#hasfocus)|Indica se o `CMFCRIbbonEdit` controle tem o foco.|  
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|Indica se a exibição de tamanho para o `CMFCRibbonEdit` controle pode ser grande.|  
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|Indica se a caixa de texto tem um botão de rotação.|  
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|Indica se o `CMFCRibbonEdit` controle é realçado.|  
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|Chamado pela estrutura quando as dimensões do retângulo de exibição para o `CMFCRibbonEdit` controlar alterações.|  
|[CMFCRibbonEdit::OnDraw](#ondraw)|Chamado pela estrutura para desenhar o `CMFCRibbonEdit` controle.|  
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|Chamado pela estrutura para desenhar o rótulo e a imagem para o `CMFCRibbonEdit` controle.|  
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|Chamado pela estrutura para desenhar o `CMFCRibbonEdit` controle em uma caixa de lista de comandos.|  
|[CMFCRibbonEdit::OnEnable](#onenable)|Chamado pela estrutura para habilitar ou desabilitar o `CMFCRibbonEdit` controle.|  
|[CMFCRibbonEdit::OnHighlight](#onhighlight)|Chamado pela estrutura quando o ponteiro entra ou sai dos limites do `CMFCRibbonEdit` controle.|  
|[CMFCRibbonEdit::OnKey](#onkey)|Chamado pela estrutura quando o usuário pressiona uma dica de tela e o `CMFCRibbonEdit` controle tem o foco.|  
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|Chamado pela estrutura para atualizar o `CMFCRibbonEdit` controlar quando o usuário pressiona o botão esquerdo do mouse no controle.|  
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|Chamado pela estrutura quando o usuário libera o botão esquerdo do mouse.|  
|[CMFCRibbonEdit::OnRTLChanged](#onrtlchanged)|Chamado pela estrutura para atualizar o `CMFCRibbonEdit` controlar quando o layout muda de direção.|  
|[CMFCRibbonEdit::OnShow](#onshow)|Chamado pela estrutura para mostrar ou ocultar o `CMFCRibbonEdit` controle.|  
|[CMFCRibbonEdit::Redraw](#redraw)|Atualiza a exibição do `CMFCRibbonEdit` controle.|  
|[CMFCRibbonEdit::SetACCData](#setaccdata)|Define os dados de acessibilidade para o `CMFCRibbonEdit` objeto.|  
|[CMFCRibbonEdit::SetEditText](#setedittext)|Define o texto na caixa de texto.|  
|[CMFCRibbonEdit::SetTextAlign](#settextalign)|Define o alinhamento do texto da caixa de texto.|  
|[CMFCRibbonEdit::SetWidth](#setwidth)|Define a largura da caixa de texto para o `CMFCRibbonEdit` controle.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como criar um `CMFCRibbonEdit` do objeto, Mostrar botões de rotação ao lado do controle de edição e defina o texto do controle de edição. Este trecho de código é parte do [exemplo MS Office 2007 demonstração](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo&#7;](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** afxRibbonEdit.h  
  
##  <a name="canbestretched"></a>CMFCRibbonEdit::CanBeStretched  
 Indica se a altura do [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controle pode aumentar verticalmente até a altura de uma linha de faixa de opções.  
  
```  
virtual BOOL CanBeStretched();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Sempre retorna `FALSE`.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="cmfcribbonedit"></a>CMFCRibbonEdit::CMFCRibbonEdit  
 Constrói uma [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.  
  
```  
CMFCRibbonEdit(
    UINT nID,  
    int nWidth,  
    LPCTSTR lpszLabel = NULL,  
    int nImage = -1);

CMFCRibbonEdit();
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nID`  
 Comando ID para o `CMFCRibbonEdit` controle.  
  
 [in] `nWidth`  
 A largura, em pixels, da caixa de texto para o `CMFCRibbonEdit` controle.  
  
 [in] `lpszLabel`  
 O rótulo para o `CMFCRibbonEdit` controle.  
  
 [in] `nImage`  
 Índice da imagem pequena a ser usado para o `CMFCRibbonEdit` controle. A coleção de imagens pequenas é mantida pela categoria de faixa de opções do pai.  
  
### <a name="remarks"></a>Comentários  
 O `CMFCRibbonEdit` controle não usa uma imagem grande.  
  
##  <a name="copyfrom"></a>CMFCRibbonEdit::CopyFrom  
 Copia o estado especificado [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto atual [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `src`  
 A fonte `CMFCRibbonEdit` objeto.  
  
### <a name="remarks"></a>Comentários  
 O `src` parâmetro deve ser do tipo `CMFCRibbonEdit`.  
  
##  <a name="createedit"></a>CMFCRibbonEdit::CreateEdit  
 Cria uma nova caixa de texto para o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.  
  
```  
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pWndParent`  
 Um ponteiro para a janela pai do `CMFCRibbonEdit` objeto.  
  
 [in] `dwEditStyle`  
 Especifica o estilo da caixa de texto. Você pode combinar os estilos de janela listados na seção de comentários com o [Editar estilos de controle](http://msdn.microsoft.com/library/windows/desktop/bb775464) que são descritas no SDK do Windows.  
  
### <a name="return-value"></a>Valor de retorno  
 Um ponteiro para a nova caixa de texto se o método teve êxito; Caso contrário, `NULL`.  
  
### <a name="remarks"></a>Comentários  
 Substitua esse método em uma classe derivada para criar uma caixa de texto personalizado.  
  
 Você pode aplicar o seguinte [estilos de janela](../../mfc/reference/window-styles.md) para uma caixa de texto:  
  
- **ESTILO**  
  
- **WS_VISIBLE**  
  
- **WS_DISABLED**  
  
- **WS_GROUP**  
  
- **WS_TABSTOP**  
  
##  <a name="destroyctrl"></a>CMFCRibbonEdit::DestroyCtrl  
 Destrói o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.  
  
```  
virtual void DestroyCtrl();
```  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="dropdownlist"></a>CMFCRibbonEdit::DropDownList  
 Exibe uma caixa de listagem.  
  
```  
virtual void DropDownList();
```  
  
### <a name="remarks"></a>Comentários  
 Por padrão, esse método não fará nada. Substitua este método para uma caixa de lista suspensa.  
  
##  <a name="enablespinbuttons"></a>CMFCRibbonEdit::EnableSpinButtons  
 Habilita e define o intervalo do botão de rotação da caixa de texto.  
  
```  
void EnableSpinButtons(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nMin`  
 O valor mínimo do botão de rotação.  
  
 [in] `nMax`  
 O valor máximo do botão de rotação.  
  
### <a name="remarks"></a>Comentários  
 Botões de rotação exibem ativo e seta para baixo e permitem aos usuários percorrer um conjunto fixo de valores.  
  
##  <a name="getcompactsize"></a>CMFCRibbonEdit::GetCompactSize  
 Recupera o tamanho compacto do [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.  
  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pDC`  
 Ponteiro para um contexto de dispositivo para o `CMFCRibbonEdit` objeto.  
  
### <a name="return-value"></a>Valor de retorno  
 O tamanho compacto do `CMFCRibbonEdit` objeto.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="getedittext"></a>CMFCRibbonEdit::GetEditText  
 Recupera o texto na caixa de texto.  
  
```  
CString GetEditText() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 O texto na caixa de texto.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="getintermediatesize"></a>CMFCRibbonEdit::GetIntermediateSize  
 Recupera o tamanho intermediário do [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.  
  
```  
virtual CSize GetIntermediateSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pDC`  
 Ponteiro para um contexto de dispositivo para o `CMFCRibbonEdit` objeto.  
  
### <a name="return-value"></a>Valor de retorno  
 O tamanho intermediário do `CMFCRibbonEdit` objeto.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="gettextalign"></a>CMFCRibbonEdit::GetTextAlign  
 Recupera o alinhamento do texto na caixa de texto.  
  
```  
int GetTextAlign() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um valor enumerado de alinhamento de texto. Consulte a seção comentários para os valores possíveis.  
  
### <a name="remarks"></a>Comentários  
 O valor retornado é um dos seguintes estilos de controle de edição:  
  
- **ES_LEFT** para alinhamento à esquerda  
  
- **ES_CENTER** para centralizar  
  
- **ES_RIGHT** para alinhamento à direita  
  
 Para obter mais informações sobre esses estilos, consulte [Editar estilos de controle](http://msdn.microsoft.com/library/windows/desktop/bb775464).  
  
##  <a name="getwidth"></a>CMFCRibbonEdit::GetWidth  
 Recupera a largura, em pixels, do [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controle.  
  
```  
int GetWidth(BOOL bInFloatyMode = FALSE) const;  
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `bInFloatyMode`  
 `TRUE`Se o `CMFCRibbonEdit` controle está no modo flutuante; caso contrário, `FALSE`.  
  
### <a name="return-value"></a>Valor de retorno  
 A largura, em pixels, do `CMFCRibbonEdit` controle.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="hascompactmode"></a>CMFCRibbonEdit::HasCompactMode  
 Indica se a exibição de tamanho para o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controle pode ser compacto.  
  
```  
virtual BOOL HasCompactMode() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 Sempre retorna `TRUE`.  
  
### <a name="remarks"></a>Comentários  
 Por padrão esse método sempre retornará `TRUE`. Substitua este método para indicar se o tamanho da exibição pode ser compacto.  
  
##  <a name="hasfocus"></a>CMFCRibbonEdit::HasFocus  
 Indica se o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controle tem o foco.  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se o `CMFCRibbonEdit` controle tem o foco; caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="haslargemode"></a>CMFCRibbonEdit::HasLargeMode  
 Indica se a exibição de tamanho para o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controle pode ser grande.  
  
```  
virtual BOOL HasLargeMode() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 Sempre retorna `FALSE`.  
  
### <a name="remarks"></a>Comentários  
 Por padrão esse método sempre retornará `FALSE`. Substitua este método para indicar se o tamanho de exibição pode ser grande.  
  
##  <a name="hasspinbuttons"></a>CMFCRibbonEdit::HasSpinButtons  
 Indica se a caixa de texto tem um botão de rotação.  
  
```  
virtual BOOL HasSpinButtons() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se a caixa de texto tem um botão de rotação. Caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="ishighlighted"></a>CMFCRibbonEdit::IsHighlighted  
 Indica se o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controle é realçado.  
  
```  
virtual BOOL IsHighlighted() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se o `CMFCRibbonEdit` controle é realçada; caso contrário `FALSE`.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="onafterchangerect"></a>CMFCRibbonEdit::OnAfterChangeRect  
 Chamado pela estrutura quando as dimensões do retângulo de exibição para o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controlar alterações.  
  
```  
virtual void OnAfterChangeRect(CDC* pDC);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pDC`  
 Ponteiro para um contexto de dispositivo para o `CMFCRibbonEdit` controle.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="ondraw"></a>CMFCRibbonEdit::OnDraw  
 Chamado pela estrutura para desenhar o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controle.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pDC`  
 Ponteiro para um contexto de dispositivo para o `CMFCRibbonEdit` controle.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="ondrawlabelandimage"></a>CMFCRibbonEdit::OnDrawLabelAndImage  
 Chamado pela estrutura para desenhar o rótulo e a imagem para o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controle.  
  
```  
virtual void OnDrawLabelAndImage(CDC* pDC);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pDC`  
 Ponteiro para um contexto de dispositivo para o `CMFCRibbonEdit` controle.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="ondrawonlist"></a>CMFCRibbonEdit::OnDrawOnList  
 Chamado pela estrutura para desenhar o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controle em uma caixa de lista de comandos.  
  
```  
virtual void OnDrawOnList(
    CDC* pDC,  
    CString strText,  
    int nTextOffset,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `pDC`  
 Ponteiro para um contexto de dispositivo para o `CMFCRibbonEdit` controle.  
  
 [in] `strText`  
 O texto de exibição [ ](../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit class").  
  
 [in] `nTextOffset`  
 Distância, em pixels, do lado esquerdo da caixa de listagem para o texto de exibição.  
  
 [in] `rect`  
 O retângulo de exibição para o `CMFCRibbonEdit` controle.  
  
 [in] `bIsSelected`  
 Este parâmetro não é usado.  
  
 [in] `bHighlighted`  
 Este parâmetro não é usado.  
  
### <a name="remarks"></a>Comentários  
 A caixa de lista de comandos exibe controles da faixa de opções para permitir que os usuários personalizem a barra de ferramentas de acesso rápido.  
  
##  <a name="onenable"></a>CMFCRibbonEdit::OnEnable  
 Chamado pela estrutura para habilitar ou desabilitar o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controle.  
  
```  
virtual void OnEnable(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `bEnable`  
 `TRUE`Para habilitar o controle; `FALSE` para desabilitar o controle.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="onhighlight"></a>CMFCRibbonEdit::OnHighlight  
 Chamado pela estrutura quando o ponteiro entra ou sai dos limites do [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controle.  
  
```  
virtual void OnHighlight(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `bHighlight`  
 `TRUE`Se o ponteiro estiver em limites do `CMFCRibbonEdit` controle; caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="onkey"></a>CMFCRibbonEdit::OnKey  
 Chamado pela estrutura quando o usuário pressiona uma dica de tela e o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controle tem o foco.  
  
```  
virtual BOOL OnKey(BOOL bIsMenuKey);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `bIsMenuKey`  
 `TRUE`Se a dica de tela exibe um menu pop-up. Caso contrário, `FALSE`.  
  
### <a name="return-value"></a>Valor de retorno  
 `TRUE`Se o evento foi tratado; Caso contrário, `FALSE`.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="onlbuttondown"></a>CMFCRibbonEdit::OnLButtonDown  
 Chamado pela estrutura para atualizar o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controlar quando o usuário pressiona o botão esquerdo do mouse no controle.  
  
```  
virtual void OnLButtonDown(CPoint point);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `point`  
 Este parâmetro não é usado.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="onlbuttonup"></a>CMFCRibbonEdit::OnLButtonUp  
 Chamado pela estrutura quando o usuário libera o botão esquerdo do mouse.  
  
```  
virtual void OnLButtonUp(CPoint point);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `point`  
 Este parâmetro não é usado.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="onrtlchanged"></a>CMFCRibbonEdit::OnRTLChanged  
 Chamado pela estrutura para atualizar o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controlar quando o layout muda de direção.  
  
```  
virtual void OnRTLChanged(BOOL bIsRTL);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `bIsRTL`  
 `TRUE`Se o layout é da direita para esquerda; `FALSE` se o layout é à esquerda para a direita.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="onshow"></a>CMFCRibbonEdit::OnShow  
 Chamado pela estrutura para mostrar ou ocultar o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controle.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `bShow`  
 `TRUE`para mostrar o controle. `FALSE` para ocultar o controle.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="redraw"></a>CMFCRibbonEdit::Redraw  
 Atualiza a exibição do [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controle.  
  
```  
virtual void Redraw();
```  
  
### <a name="remarks"></a>Comentários  
 Esse método redesenha o retângulo de exibição para o `CMFCRibbonEdit` indiretamente chamando [CWnd::RedrawWindow](http://msdn.microsoft.com/library/windows/desktop/dd162911) com o `RDW_INVALIDATE`, `RDW_ERASE`, e `RDW_UPDATENOW` sinalizadores de conjunto.  
  
##  <a name="setaccdata"></a>CMFCRibbonEdit::SetACCData  
 Define os dados de acessibilidade para o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) objeto.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parâmetros  
 `pParent`  
 Ponteiro para a janela pai para o `CMFCRibbonEdit` objeto.  
  
 `data`  
 Os dados de acessibilidade para o `CMFCRibbonEdit` objeto.  
  
### <a name="return-value"></a>Valor de retorno  
 Sempre retorna `TRUE`.  
  
### <a name="remarks"></a>Comentários  
  
##  <a name="setedittext"></a>CMFCRibbonEdit::SetEditText  
 Define o texto na caixa de texto.  
  
```  
void SetEditText(CString strText);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `strText`  
 O texto da caixa de texto.  
  
##  <a name="settextalign"></a>CMFCRibbonEdit::SetTextAlign  
 Define o alinhamento do texto da caixa de texto.  
  
```  
void SetTextAlign(int nAlign);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nAlign`  
 Um valor enumerado de alinhamento de texto. Consulte a seção comentários para os valores possíveis.  
  
### <a name="remarks"></a>Comentários  
 O parâmetro `nAlign` é um dos seguinte Editar estilos de controle:  
  
- **ES_LEFT** para alinhamento à esquerda  
  
- **ES_CENTER** para centralizar  
  
- **ES_RIGHT** para alinhamento à direita  
  
 Para obter mais informações sobre esses estilos, consulte [Editar estilos de controle](http://msdn.microsoft.com/library/windows/desktop/bb775464).  
  
##  <a name="setwidth"></a>CMFCRibbonEdit::SetWidth  
 Define a largura da caixa de texto para o [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md) controle.  
  
```  
void SetWidth(
    int nWidth,  
    BOOL bInFloatyMode = FALSE);
```  
  
### <a name="parameters"></a>Parâmetros  
 [in] `nWidth`  
 A largura, em pixels, da caixa de texto.  
  
 `bInFloatyMode`  
 `TRUE`Para definir a largura de modo flutuante; `FALSE` para definir a largura para o modo normal.  
  
### <a name="remarks"></a>Comentários  
 O `CMFCRibbonEdit` controle tem duas larguras dependendo de seu modo de exibição: flutuante modo e o modo normal.  
  
## <a name="see-also"></a>Consulte também  
 [Gráfico de hierarquia](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [Classe CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)   
 [Classe CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)