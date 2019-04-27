---
title: Classe CAnimationGroup
ms.date: 03/27/2019
f1_keywords:
- CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::Animate
- AFXANIMATIONCONTROLLER/CAnimationGroup::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationGroup::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::Schedule
- AFXANIMATIONCONTROLLER/CAnimationGroup::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutoclearTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstKeyFrames
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pStoryboard
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pParentController
helpviewer_keywords:
- CAnimationGroup [MFC], CAnimationGroup
- CAnimationGroup [MFC], Animate
- CAnimationGroup [MFC], ApplyTransitions
- CAnimationGroup [MFC], FindAnimationObject
- CAnimationGroup [MFC], GetGroupID
- CAnimationGroup [MFC], RemoveKeyframes
- CAnimationGroup [MFC], RemoveTransitions
- CAnimationGroup [MFC], Schedule
- CAnimationGroup [MFC], SetAutodestroyTransitions
- CAnimationGroup [MFC], AddKeyframes
- CAnimationGroup [MFC], AddTransitions
- CAnimationGroup [MFC], CreateTransitions
- CAnimationGroup [MFC], m_bAutoclearTransitions
- CAnimationGroup [MFC], m_bAutodestroyAnimationObjects
- CAnimationGroup [MFC], m_bAutodestroyKeyframes
- CAnimationGroup [MFC], m_lstAnimationObjects
- CAnimationGroup [MFC], m_lstKeyFrames
- CAnimationGroup [MFC], m_pStoryboard
- CAnimationGroup [MFC], m_nGroupID
- CAnimationGroup [MFC], m_pParentController
ms.assetid: 8bc18ceb-33a2-41d0-9731-71811adacab7
ms.openlocfilehash: 32b2adfee2a36139a11caa12fa98bd240b0732dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152059"
---
# <a name="canimationgroup-class"></a>Classe CAnimationGroup

Implementa um grupo de animação, que combina um storyboard de animação, objetos de animação e faz a transição para definir uma animação.

## <a name="syntax"></a>Sintaxe

```
class CAnimationGroup;
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|Constrói um grupo de animação.|
|[CAnimationGroup::~CAnimationGroup](#_dtorcanimationgroup)|O destruidor. Chamado quando um grupo de animação está sendo destruído.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CAnimationGroup::Animate](#animate)|Anima um grupo.|
|[CAnimationGroup::ApplyTransitions](#applytransitions)|Aplica-se as transições para objetos de animação.|
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|Localiza um objeto de animação que contém a variável de animação especificado.|
|[CAnimationGroup::GetGroupID](#getgroupid)|Retorna a ID do grupo.|
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|Remove e, opcionalmente, destrói todos os quadros-chave que pertencem a um grupo de animação.|
|[CAnimationGroup::RemoveTransitions](#removetransitions)|Remove as transições de objetos de animação que pertencem a um grupo de animação.|
|[CAnimationGroup::Schedule](#schedule)|Agenda uma animação no momento especificado.|
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|Direciona as transições de destruir todos os objetos de animação que pertencem ao grupo automaticamente.|

### <a name="protected-methods"></a>Métodos Protegidos

|Nome|Descrição|
|----------|-----------------|
|[CAnimationGroup::AddKeyframes](#addkeyframes)|Um auxiliar que adiciona os quadros-chave a um storyboard.|
|[CAnimationGroup::AddTransitions](#addtransitions)|Um auxiliar que adiciona as transições para um storyboard.|
|[CAnimationGroup::CreateTransitions](#createtransitions)|Um auxiliar que cria objetos de transição de COM.|

### <a name="public-data-members"></a>Membros de Dados Públicos

|Nome|Descrição|
|----------|-----------------|
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|Especifica como limpar transições de objetos de animação que pertencem ao grupo. Se esse membro for TRUE, as transições são removidas automaticamente quando uma animação foi agendada. Caso contrário, você precisará remover as transições manualmente.|
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|Especifica como destruir objetos de animação. Se esse parâmetro for TRUE, os objetos de animação serão destruídos automaticamente quando o grupo é destruído. Caso contrário, os objetos de animação devem ser destruídos manualmente. O valor padrão é FALSE. Defina esse valor como TRUE somente se todos os objetos de animação que pertencem ao grupo são alocados dinamicamente com o novo operador.|
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|Especifica como destruir quadros-chave. Se esse valor for TRUE, todos os quadros chave são removidos e destruídos; Caso contrário, eles serão removidos da lista apenas. O valor padrão é TRUE.|
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|Contém uma lista de objetos de animação.|
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|Contém uma lista de quadros-chave.|
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|Aponta para o storyboard de animação. Esse ponteiro é válido somente após a chamada de animar.|

### <a name="protected-data-members"></a>Membros de dados protegidos

|Nome|Descrição|
|----------|-----------------|
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|Um identificador exclusivo do grupo de animação.|
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|Um ponteiro para o controlador de animação, que esse grupo pertence.|

## <a name="remarks"></a>Comentários

Grupos de animação são criados automaticamente pelo controlador de animação (CAnimationController) quando você adiciona objetos de animação usando CAnimationController::AddAnimationObject. Um grupo de animação é identificado pela ID do grupo, que normalmente é usado como um parâmetro para manipular grupos de animação. ID do grupo é obtido do primeiro objeto de animação que está sendo adicionado a um novo grupo de animação. Um storyboard de animação encapsulado é criado depois de chamar CAnimationController::AnimateGroup e podem ser acessados via m_pStoryboard membro público.

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`CAnimationGroup`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxanimationcontroller.h

##  <a name="_dtorcanimationgroup"></a>  CAnimationGroup::~CAnimationGroup

O destruidor. Chamado quando um grupo de animação está sendo destruído.

```
~CAnimationGroup();
```

##  <a name="addkeyframes"></a>  CAnimationGroup::AddKeyframes

Um auxiliar que adiciona os quadros-chave a um storyboard.

```
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```

### <a name="parameters"></a>Parâmetros

*pStoryboard*<br/>
Um ponteiro para um objeto storyboard COM.

*bAddDeep*<br/>
Especifica se esse método deve adicionar para os quadros-chave do storyboard que dependem de outros quadros chave.

##  <a name="addtransitions"></a>  CAnimationGroup::AddTransitions

Um auxiliar que adiciona as transições para um storyboard.

```
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parâmetros

*pStoryboard*<br/>
Um ponteiro para um objeto storyboard COM.

*bDependOnKeyframes*

##  <a name="animate"></a>  CAnimationGroup::Animate

Anima um grupo.

```
BOOL Animate(
    IUIAnimationManager* pManager,
    IUIAnimationTimer* pTimer,
    BOOL bScheduleNow);
```

### <a name="parameters"></a>Parâmetros

*pManager*<br/>
*pTimer*
*bScheduleNow*

### <a name="return-value"></a>Valor de retorno

TRUE se o método for bem-sucedido; Caso contrário, FALSE.

### <a name="remarks"></a>Comentários

Esse método cria um storyboard interno, cria e aplica as transições e agenda uma animação se bScheduleNow for TRUE. Se bScheduleNow for FALSE, você precisará chamar o agendamento para iniciar a animação na hora especificada.

##  <a name="applytransitions"></a>  CAnimationGroup::ApplyTransitions

Aplica-se as transições para objetos de animação.

```
void ApplyTransitions();
```

### <a name="remarks"></a>Comentários

Esse método declara no modo de depuração se storyboard não foi criado. Ele cria todas as transições pela primeira vez, e em seguida, adiciona os quadros-chave "estáticos" (quadros-chave que dependem de deslocamentos), adiciona as transições que não dependem de quadros-chave, adiciona quadros-chave, dependendo de transições e outros quadros chave e finalmente adiciona as transições que dependem de quadros-chave .

##  <a name="canimationgroup"></a>  CAnimationGroup::CAnimationGroup

Constrói um grupo de animação.

```
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```

### <a name="parameters"></a>Parâmetros

*pParentController*<br/>
Um ponteiro para o controlador de animação que cria um grupo.

*nGroupID*<br/>
Especifica a ID do grupo.

##  <a name="createtransitions"></a>  CAnimationGroup::CreateTransitions

Um auxiliar que cria objetos de transição de COM.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Valor de retorno

VERDADEIRO se o método for bem-sucedido, caso contrário, FALSE.

##  <a name="findanimationobject"></a>  CAnimationGroup::FindAnimationObject

Localiza um objeto de animação que contém a variável de animação especificado.

```
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parâmetros

*pVariable*<br/>
Um ponteiro para a variável de animação.

### <a name="return-value"></a>Valor de retorno

Um ponteiro para o objeto de animação ou nulo se o objeto de animação não for encontrado.

##  <a name="getgroupid"></a>  CAnimationGroup::GetGroupID

Retorna a ID do grupo.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Valor de retorno

Um identificador de grupo.

##  <a name="m_bautocleartransitions"></a>  CAnimationGroup::m_bAutoclearTransitions

Especifica como limpar transições de objetos de animação que pertencem ao grupo. Se esse membro for TRUE, as transições são removidas automaticamente quando uma animação foi agendada. Caso contrário, você precisará remover as transições manualmente.

```
BOOL m_bAutoclearTransitions;
```

##  <a name="m_bautodestroyanimationobjects"></a>  CAnimationGroup::m_bAutodestroyAnimationObjects

Especifica como destruir objetos de animação. Se esse parâmetro for TRUE, os objetos de animação serão destruídos automaticamente quando o grupo é destruído. Caso contrário, os objetos de animação devem ser destruídos manualmente. O valor padrão é FALSE. Defina esse valor como TRUE somente se todos os objetos de animação que pertencem ao grupo são alocados dinamicamente com o novo operador.

```
BOOL m_bAutodestroyAnimationObjects;
```

##  <a name="m_bautodestroykeyframes"></a>  CAnimationGroup::m_bAutodestroyKeyframes

Especifica como destruir quadros-chave. Se esse valor for TRUE, todos os quadros chave são removidos e destruídos; Caso contrário, eles serão removidos da lista apenas. O valor padrão é TRUE.

```
BOOL m_bAutodestroyKeyframes;
```

##  <a name="m_lstanimationobjects"></a>  CAnimationGroup::m_lstAnimationObjects

Contém uma lista de objetos de animação.

```
CObList m_lstAnimationObjects;
```

##  <a name="m_lstkeyframes"></a>  CAnimationGroup::m_lstKeyFrames

Contém uma lista de quadros-chave.

```
CObList m_lstKeyFrames;
```

##  <a name="m_ngroupid"></a>  CAnimationGroup::m_nGroupID

Um identificador exclusivo do grupo de animação.

```
UINT32 m_nGroupID;
```

##  <a name="m_pparentcontroller"></a>  CAnimationGroup::m_pParentController

Um ponteiro para o controlador de animação, que esse grupo pertence.

```
CAnimationController* m_pParentController;
```

##  <a name="m_pstoryboard"></a>  CAnimationGroup::m_pStoryboard

Aponta para o storyboard de animação. Esse ponteiro é válido somente após a chamada de animar.

```
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;
```

##  <a name="removekeyframes"></a>  CAnimationGroup::RemoveKeyframes

Remove e, opcionalmente, destrói todos os quadros-chave que pertencem a um grupo de animação.

```
void RemoveKeyframes();
```

### <a name="remarks"></a>Comentários

Se o membro m_bAutodestroyKeyframes for TRUE, os quadros-chave são removidos e destruídos, caso contrário, quadros-chave apenas são removidos da lista interna de quadros-chave.

##  <a name="removetransitions"></a>  CAnimationGroup::RemoveTransitions

Remove as transições de objetos de animação que pertencem a um grupo de animação.

```
void RemoveTransitions();
```

### <a name="remarks"></a>Comentários

Se o sinalizador m_bAutoclearTransitions é definido como TRUE, esse método faz um loop sobre todos os objetos de animação que pertencem ao grupo e chama CAnimationObject::ClearTransitions(FALSE).

##  <a name="schedule"></a>  CAnimationGroup::Schedule

Agenda uma animação no momento especificado.

```
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```

### <a name="parameters"></a>Parâmetros

*pTimer*<br/>
Um ponteiro para o temporizador de animação.

*time*<br/>
Especifica a hora de agendar a animação.

### <a name="return-value"></a>Valor de retorno

TRUE se o método for bem-sucedido; FALSE se o método falhar ou se animar não foi chamado com bScheduleNow definido como FALSE.

### <a name="remarks"></a>Comentários

Chame essa função para agendar uma animação no momento especificado. Você deve chamar Animate com bScheduleNow definido como FALSE, pela primeira vez.

##  <a name="setautodestroytransitions"></a>  CAnimationGroup::SetAutodestroyTransitions

Direciona as transições de destruir todos os objetos de animação que pertencem ao grupo automaticamente.

```
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parâmetros

*bAutoDestroy*<br/>
Especifica como as transições de destruir.

### <a name="remarks"></a>Comentários

Defina esse valor como FALSE apenas se você alocar transições na pilha. O valor padrão é TRUE, portanto, é altamente recomendável para alocar objetos de transição, usando o operador novo.

## <a name="see-also"></a>Consulte também

[Classes](../../mfc/reference/mfc-classes.md)
