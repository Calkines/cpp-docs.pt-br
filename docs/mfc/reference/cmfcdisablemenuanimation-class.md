---
title: Classe CMFCDisableMenuAnimation
ms.date: 11/04/2016
f1_keywords:
- CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation
- AFXPOPUPMENU/CMFCDisableMenuAnimation::Restore
helpviewer_keywords:
- CMFCDisableMenuAnimation [MFC], Restore
ms.assetid: c6eb07da-c382-43d6-8028-007f2320e50e
ms.openlocfilehash: 0b0df30d48b2f77d620b00f67d40743445981b66
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665030"
---
# <a name="cmfcdisablemenuanimation-class"></a>Classe CMFCDisableMenuAnimation

Desabilita a animação do menu pop-up.

## <a name="syntax"></a>Sintaxe

```
class CMFCDisableMenuAnimation
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|||
|-|-|
|Nome|Descrição|
|`CMFCDisableMenuAnimation::CMFCDisableMenuAnimation`|Constrói um objeto `CMFCDisableMenuAnimation`.|
|`CMFCDisableMenuAnimation::~CMFCDisableMenuAnimation`|Destruidor.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nome|Descrição|
|[CMFCDisableMenuAnimation::Restore](#restore)|Restaura a animação anterior que a estrutura usada para exibir um menu pop-up.|

### <a name="data-members"></a>Membros de Dados

|||
|-|-|
|Nome|Descrição|
|`CMFCDisableMenuAnimation::m_animType`|Armazena o tipo de animação anterior do menu pop-up.|

### <a name="remarks"></a>Comentários

Use esta classe auxiliar para desabilitar temporariamente a animação do menu pop-up (por exemplo, quando você processar comandos de mouse ou teclado).

Um `CMFCDisableMenuAnimation` desabilita o objeto de animação do menu pop-up durante seu ciclo de vida. O construtor armazena o tipo de animação do menu pop-up atual na `m_animType` campo e define o tipo de animação atual a `CMFCPopupMenu::NO_ANIMATION`. O destruidor restaura o tipo de animação anterior.

Você pode criar um `CMFCDisableMenuAnimation` objeto na pilha para desabilitar a animação do menu pop-up ao longo de uma única função. Se você quiser desabilitar a animação do menu pop-up entre as funções, crie um `CMFCDisableMenuAnimation` no heap de objeto e, em seguida, excluí-lo quando você deseja restaurar a animação do menu pop-up.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como usar a pilha para desabilitar temporariamente a animação de menus.

[!code-cpp[NVC_MFC_Misc#1](../../mfc/reference/codesnippet/cpp/cmfcdisablemenuanimation-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CMFCDisableMenuAnimation](../../mfc/reference/cmfcdisablemenuanimation-class.md)

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxpopupmenu.h

##  <a name="restore"></a>  CMFCDisableMenuAnimation::Restore

Restaura a animação anterior que a estrutura usada para exibir um menu pop-up.

```
void Restore ();
```

### <a name="remarks"></a>Comentários

Esse método é chamado pelo `CMFCDisableMenuAnimation` destruidor para restaurar a animação anterior que a estrutura usada para exibir um menu pop-up.

## <a name="see-also"></a>Consulte também

[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)<br/>
[Classe CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)
