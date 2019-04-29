---
title: Estilos de controle da ToolBar
ms.date: 11/04/2016
helpviewer_keywords:
- ToolBar control styles [MFC]
ms.assetid: 0f717eb9-fa32-4263-b852-809238863feb
ms.openlocfilehash: 9ad85ca19235478e6a5aa1d917ebe75e62308be5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309766"
---
# <a name="toolbar-control-styles"></a>Estilos de controle da ToolBar

[Classe CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) tem um conjunto de sinalizadores de estilo que determinam a aparência e comportamento do botão. Você pode definir uma combinação desses sinalizadores chamando [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle). Este tópico lista os valores de sinalizador de estilo e seus significados.

## <a name="property-values"></a>Valores de propriedade

Os valores a seguir determinam o tipo de botão que representa o controle:

|||
|-|-|
|TBBS_BUTTON|Botão de ação padrão (padrão).  |
|TBBS_CHECKBOX|Caixa de seleção.  |
|TBBS_CHECKGROUP|O início de um grupo de caixas de seleção.  |
|TBBS_GROUP|O início de um grupo de botões.  |
|TBBS_SEPARATOR|Separador.  |

Os valores a seguir representam o status atual do controle:

|||
|-|-|
|TBBS_CHECKED|Caixa de seleção está marcada.  |
|TBBS_DISABLED|Controle está desabilitado.  |
|TBBS_INDETERMINATE|Caixa de seleção está em um estado indeterminado.  |
|TBBS_PRESSED|Botão é pressionado.  |

O valor a seguir altera o layout do botão na barra de ferramentas:

|||
|-|-|
|TBBS_BREAK|Coloca o item em uma nova linha ou em uma nova coluna sem separar colunas.  |

## <a name="remarks"></a>Comentários

O estilo atual é armazenado no [CMFCToolBarButton::m_nStyle](../../mfc/reference/cmfctoolbarbutton-class.md#m_nstyle). Não defina um novo valor `m_nStyle` diretamente, porque algumas classes derivadas realizar processamento adicional quando você chamar `SetStyles`.

O Gerenciador visual determina a aparência dos botões em cada estado. Ver [Gerenciador de visualização](../../mfc/visualization-manager.md) para obter mais informações.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxtoolbarbutton.h

## <a name="see-also"></a>Consulte também

[Macros e globais](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[Classe CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Gerenciador de visualização](../../mfc/visualization-manager.md)
