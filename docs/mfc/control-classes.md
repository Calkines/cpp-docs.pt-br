---
title: Classes de controle
ms.date: 11/04/2016
f1_keywords:
- vc.classes.control
helpviewer_keywords:
- static display controls [MFC]
- control classes [MFC]
- buttons, MFC control classes
- controls [MFC], MFC control classes
- controls [MFC]
- list boxes [MFC], MFC control classes
- control classes [MFC], MFC
- text, controls for input [MFC]
- user input [MFC], MFC control classes
ms.assetid: f9876606-9f5b-44cb-9135-213298d1df8f
ms.openlocfilehash: 79a71a4660cd49f85726d730c9fad0b2f10f83bb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300421"
---
# <a name="control-classes"></a>Classes de controle

Classes de controle encapsulam uma ampla variedade de controles padrão do Windows, variando de controles de texto estático a controles de árvore. Além disso, o MFC fornece alguns novos controles, incluindo botões com barras de controle e bitmaps.

Os controles cujos nomes de classe terminam em "**Ctrl**" foram introduzidas no Windows 95 e Windows NT versão 3.51.

## <a name="static-display-controls"></a>Controles de exibição estática

[CStatic](../mfc/reference/cstatic-class.md)<br/>
Uma janela de exibição estática. Controles estáticos são usados para rotular, caixa ou separar outros controles em uma janela ou caixa de diálogo. Eles também podem exibir imagens gráficas em vez de texto ou uma caixa.

## <a name="text-controls"></a>Controles de texto

[CEdit](../mfc/reference/cedit-class.md)<br/>
Uma janela de controle de texto editável. Editar controles são usados para aceitar entrada textual do usuário.

[CIPAddressCtrl](../mfc/reference/cipaddressctrl-class.md)<br/>
Dá suporte a uma caixa de edição para a manipulação de um endereço IP (Internet Protocol).

[CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)<br/>
Um controle no qual o usuário pode inserir e editar o texto. Ao contrário do controle encapsulado em `CEdit`, um controle rich edit dá suporte a caracteres e formatação de parágrafo e objetos OLE.

## <a name="controls-that-represent-numbers"></a>Controles que representam números

[CSliderCtrl](../mfc/reference/csliderctrl-class.md)<br/>
Um controle que contém um controle deslizante, que o usuário move para selecionar um valor ou conjunto de valores.

[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)<br/>
Um par de botões de seta para o usuário pode clicar para incrementar ou decrementar um valor.

[CProgressCtrl](../mfc/reference/cprogressctrl-class.md)<br/>
Exibe um retângulo que é preenchido da esquerda para direita para indicar o progresso de uma operação.

[CScrollBar](../mfc/reference/cscrollbar-class.md)<br/>
Uma janela de controle de barra de rolagem. A classe fornece a funcionalidade de uma barra de rolagem, para uso como um controle em uma caixa de diálogo ou janela, por meio do qual o usuário pode especificar uma posição dentro de um intervalo.

## <a name="buttons"></a>Botões

[CButton](../mfc/reference/cbutton-class.md)<br/>
Uma janela de controle de botão. A classe fornece uma interface programática para um botão de envio por push, caixa de seleção ou botão de opção em uma janela ou caixa de diálogo.

[CBitmapButton](../mfc/reference/cbitmapbutton-class.md)<br/>
Um botão com um bitmap em vez de uma legenda de texto.

## <a name="lists"></a>Listas

[CListBox](../mfc/reference/clistbox-class.md)<br/>
Uma janela de controle de caixa de listagem. Uma caixa de listagem exibe uma lista de itens que o usuário pode exibir e selecionar.

[CDragListBox](../mfc/reference/cdraglistbox-class.md)<br/>
Fornece a funcionalidade de uma caixa de listagem do Windows; permite que o usuário mova itens de caixa de lista, como nomes de arquivo e a cadeia de caracteres literais, dentro da caixa de lista. Caixas de listagem com esse recurso são úteis para uma lista de itens em uma ordem diferente de em ordem alfabética, tal como incluir nomes de caminho ou arquivos em um projeto.

[CComboBox](../mfc/reference/ccombobox-class.md)<br/>
Uma janela de controle de caixa de combinação. Uma caixa de combinação consiste em um controle de edição e uma caixa de listagem.

[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)<br/>
Estende a caixa de combinação controle de caixa, fornecendo suporte para listas de imagens.

[CCheckListBox](../mfc/reference/cchecklistbox-class.md)<br/>
Exibe uma lista de itens com caixas de seleção, o que o usuário pode verificar ou limpar, ao lado de cada item.

[CListCtrl](../mfc/reference/clistctrl-class.md)<br/>
Exibe uma coleção de itens, cada uma consistindo em um ícone e um rótulo, de maneira semelhante para o painel direito do Explorador de arquivos.

[CTreeCtrl](../mfc/reference/ctreectrl-class.md)<br/>
Exibe uma lista hierárquica de ícones e os rótulos organizados de maneira semelhante ao painel esquerdo do Explorador de arquivos.

## <a name="toolbars-and-status-bars"></a>Barras de ferramentas e barras de Status

[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)<br/>
Fornece a funcionalidade do controle de comum de barra de ferramentas do Windows. MFC a maioria dos programas que usam [CToolBar](../mfc/reference/ctoolbar-class.md) em vez dessa classe.

[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)<br/>
Uma janela horizontal, geralmente dividida em painéis, no qual um aplicativo pode exibir informações de status. MFC a maioria dos programas que usam [CStatusBar](../mfc/reference/cstatusbar-class.md) em vez dessa classe.

## <a name="miscellaneous-controls"></a>Diversos controles

[CAnimateCtrl](../mfc/reference/canimatectrl-class.md)<br/>
Exibe um clipe de vídeo simple.

[CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)<br/>
Uma pequena janela pop-up que exibe uma única linha de texto que descreve a finalidade de uma ferramenta em um aplicativo.

[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)<br/>
Dá suporte a um controle de edição estendido ou um controle de interface de calendário simples, que permite que o usuário escolha uma data específica ou um valor de tempo.

[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)<br/>
Exibe os títulos ou rótulos de colunas.

[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)<br/>
Dá suporte a um controle de interface de calendário simples que permite que um usuário selecione uma data.

[CTabCtrl](../mfc/reference/ctabctrl-class.md)<br/>
Um controle com guias no qual o usuário pode clicar, análogo aos divisores de um bloco de anotações.

[CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)<br/>
Permite que o usuário crie uma combinação de teclas quente, o usuário pode pressionar para executar uma ação rapidamente.

[CLinkCtrl](../mfc/reference/clinkctrl-class.md)<br/>
Renderiza o texto marcado para cima e inicia os aplicativos apropriados quando o usuário clica no link inserido.

[CHtmlEditCtrl](../mfc/reference/chtmleditctrl-class.md)<br/>
Fornece a funcionalidade do controle WebBrowser ActiveX em uma janela MFC.

## <a name="related-classes"></a>Classes relacionadas

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
Fornece a funcionalidade da lista de imagens do Windows. Listas de imagens são usadas com controles de árvore e controles de lista. Eles também podem ser usados para armazenar e arquivar um conjunto de bitmaps de mesmo tamanho.

[CCtrlView](../mfc/reference/cctrlview-class.md)<br/>
A classe base para todas as exibições associados a controles do Windows. Os modos de exibição com base nos controles são descritos abaixo.

[CEditView](../mfc/reference/ceditview-class.md)<br/>
Controle de edição de uma exibição que contém um padrão do Windows.

[CRichEditView](../mfc/reference/cricheditview-class.md)<br/>
Controle de edição de uma exibição que contém um avançado do Windows.

[CListView](../mfc/reference/clistview-class.md)<br/>
Uma exibição que contém um controle de lista do Windows.

[CTreeView](../mfc/reference/ctreeview-class.md)<br/>
Uma exibição que contém um controle de árvore do Windows.

## <a name="see-also"></a>Consulte também

[Visão geral da classe](../mfc/class-library-overview.md)
