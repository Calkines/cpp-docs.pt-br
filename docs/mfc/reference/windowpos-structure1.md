---
title: Estrutura WINDOWPOS&1; | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- WINDOWPOS
dev_langs:
- C++
helpviewer_keywords:
- WINDOWPOS structure
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
caps.latest.revision: 11
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 522b15d630c3a5a3593010250db0491601493c69
ms.lasthandoff: 02/25/2017

---
# <a name="windowpos-structure1"></a>Estrutura WINDOWPOS&1;
O `WINDOWPOS` estrutura contém informações sobre o tamanho e a posição de uma janela.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct tagWINDOWPOS { /* wp */  
    HWND hwnd;  
    HWND hwndInsertAfter;  
    int x;  
    int y;  
    int cx;  
    int cy;  
    UINT flags;  
} WINDOWPOS;  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *HWND*  
 Identifica a janela.  
  
 *hwndInsertAfter*  
 Identifica a janela ao qual essa janela é colocada.  
  
 *x*  
 Especifica a posição da borda esquerda da janela.  
  
 *y*  
 Especifica a posição da borda direita da janela.  
  
 `cx`  
 Especifica a largura da janela, em pixels.  
  
 `cy`  
 Especifica a altura da janela, em pixels.  
  
 `flags`  
 Especifica as opções de posicionamento de janela. Esse membro pode ser um dos seguintes valores:  
  
- **SWP_DRAWFRAME** desenha um quadro (definido na descrição de classe da janela) em torno de janela. A janela recebe um `WM_NCCALCSIZE` mensagem.  
  
- **SWP_FRAMECHANGED** envia um `WM_NCCALCSIZE` mensagem na janela, mesmo se o tamanho da janela não está sendo alterado. Se este sinalizador não for especificado, `WM_NCCALCSIZE` só é enviado quando o tamanho da janela está sendo alterado.  
  
- **SWP_HIDEWINDOW** oculta a janela.  
  
- `SWP_NOACTIVATE`Não ative a janela.  
  
- **SWP_NOCOPYBITS** descartará todo o conteúdo da área do cliente. Se este sinalizador não for especificado, o conteúdo válido da área do cliente é salvas e copiado de volta para a área do cliente depois que a janela é dimensionada ou reposicionada.  
  
- `SWP_NOMOVE`Retém a posição atual (ignora o **x** e **y** membros).  
  
- **SWP_NOOWNERZORDER** não altera a posição da janela do proprietário na ordem Z.  
  
- `SWP_NOSIZE`Mantém o tamanho atual (ignora o **cx** e **cy** membros).  
  
- **SWP_NOREDRAW** não atualiza as alterações.  
  
- **SWP_NOREPOSITION** igual **SWP_NOOWNERZORDER**.  
  
- **SWP_NOSENDCHANGING** impede que a janela de recebimento do `WM_WINDOWPOSCHANGING` mensagem.  
  
- `SWP_NOZORDER`Retém a ordenação atual (ignora o **hwndInsertAfter** membro).  
  
- **SWP_SHOWWINDOW** exibe a janela.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** WinUser. h  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas, estilos, retornos de chamada e mapas de mensagem](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)

