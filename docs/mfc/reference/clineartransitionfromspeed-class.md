---
title: Classe CLinearTransitionFromSpeed
ms.date: 11/04/2016
f1_keywords:
- CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::Create
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblSpeed
helpviewer_keywords:
- CLinearTransitionFromSpeed [MFC], CLinearTransitionFromSpeed
- CLinearTransitionFromSpeed [MFC], Create
- CLinearTransitionFromSpeed [MFC], m_dblFinalValue
- CLinearTransitionFromSpeed [MFC], m_dblSpeed
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
ms.openlocfilehash: 9ef461124321e5e8fff11c1c7be1d90246c411a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563963"
---
# <a name="clineartransitionfromspeed-class"></a>Classe CLinearTransitionFromSpeed

Encapsula uma transição de velocidade linear.

## <a name="syntax"></a>Sintaxe

```
class CLinearTransitionFromSpeed : public CBaseTransition;
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|[CLinearTransitionFromSpeed::CLinearTransitionFromSpeed](#clineartransitionfromspeed)|Constrói um objeto de transição de velocidade linear e o inicializa com velocidade e o valor final.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CLinearTransitionFromSpeed::Create](#create)|Chama a biblioteca de transição para criar o objeto encapsulado transição COM. (Substitui [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Membros de Dados Públicos

|Nome|Descrição|
|----------|-----------------|
|[CLinearTransitionFromSpeed::m_dblFinalValue](#m_dblfinalvalue)|O valor da variável de animação no final da transição.|
|[CLinearTransitionFromSpeed::m_dblSpeed](#m_dblspeed)|O valor absoluto da velocidade da variável.|

## <a name="remarks"></a>Comentários

Durante uma transição de velocidade linear, o valor da variável de animação é alterado a uma taxa especificada. A duração da transição é determinada pela diferença entre o valor inicial e o valor final especificado. Como todas as transições são limpas automaticamente, é recomendável para alocado-los usando o operador novo. O objeto de IUIAnimationTransition COM encapsulado é criado pelo CAnimationController::AnimateGroup, até então é NULL. Alterando as variáveis de membro após a criação deste objeto COM não tem nenhum efeito.

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CLinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxanimationcontroller.h

##  <a name="clineartransitionfromspeed"></a>  CLinearTransitionFromSpeed::CLinearTransitionFromSpeed

Constrói um objeto de transição de velocidade linear e o inicializa com velocidade e o valor final.

```
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>Parâmetros

*dblSpeed*<br/>
O valor absoluto da velocidade da variável.

*dblFinalValue*<br/>
O valor da variável de animação no final da transição.

##  <a name="create"></a>  CLinearTransitionFromSpeed::Create

Chama a biblioteca de transição para criar o objeto encapsulado transição COM.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parâmetros

*pLibrary*<br/>
Um ponteiro para um [IUIAnimationTransitionLibrary interface](/windows/desktop/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), que define uma biblioteca de transições padrão.

### <a name="return-value"></a>Valor de retorno

TRUE se a transição é criada com êxito; Caso contrário, FALSE.

##  <a name="m_dblfinalvalue"></a>  CLinearTransitionFromSpeed::m_dblFinalValue

O valor da variável de animação no final da transição.

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_dblspeed"></a>  CLinearTransitionFromSpeed::m_dblSpeed

O valor absoluto da velocidade da variável.

```
DOUBLE m_dblSpeed;
```

## <a name="see-also"></a>Consulte também

[Classes](../../mfc/reference/mfc-classes.md)
