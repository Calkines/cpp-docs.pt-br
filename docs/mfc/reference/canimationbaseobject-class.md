---
title: Classe CAnimationBaseObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ContainsVariable
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::DetachFromController
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetParentAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_dwUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_pParentController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationBaseObject [MFC], CAnimationBaseObject
- CAnimationBaseObject [MFC], ApplyTransitions
- CAnimationBaseObject [MFC], ClearTransitions
- CAnimationBaseObject [MFC], ContainsVariable
- CAnimationBaseObject [MFC], CreateTransitions
- CAnimationBaseObject [MFC], DetachFromController
- CAnimationBaseObject [MFC], EnableIntegerValueChangedEvent
- CAnimationBaseObject [MFC], EnableValueChangedEvent
- CAnimationBaseObject [MFC], GetAutodestroyTransitions
- CAnimationBaseObject [MFC], GetGroupID
- CAnimationBaseObject [MFC], GetObjectID
- CAnimationBaseObject [MFC], GetUserData
- CAnimationBaseObject [MFC], SetAutodestroyTransitions
- CAnimationBaseObject [MFC], SetID
- CAnimationBaseObject [MFC], SetUserData
- CAnimationBaseObject [MFC], GetAnimationVariableList
- CAnimationBaseObject [MFC], SetParentAnimationObjects
- CAnimationBaseObject [MFC], m_bAutodestroyTransitions
- CAnimationBaseObject [MFC], m_dwUserData
- CAnimationBaseObject [MFC], m_nGroupID
- CAnimationBaseObject [MFC], m_nObjectID
- CAnimationBaseObject [MFC], m_pParentController
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d6b1f9ebaa68538486d698204e6d09d39d0bfb0b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062243"
---
# <a name="canimationbaseobject-class"></a>Classe CAnimationBaseObject

A classe base para todos os objetos de animação.

## <a name="syntax"></a>Sintaxe

```
class CAnimationBaseObject : public CObject;
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|[CAnimationBaseObject::CAnimationBaseObject](#canimationbaseobject)|Sobrecarregado. Constrói um objeto de animação.|
|[CAnimationBaseObject:: ~ CAnimationBaseObject](#canimationbaseobject__~canimationbaseobject)|O destruidor. Chamado quando um objeto de animação está sendo destruído.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|Adiciona as transições ao storyboard com variável de animação encapsulado.|
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|Remove todas as transições relacionadas.|
|[CAnimationBaseObject::ContainsVariable](#containsvariable)|Determina se um objeto de animação contém uma variável de animação em particular.|
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|Cria as transições associadas a um objeto de animação.|
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|Desanexa um objeto de animação do controlador de animação do pai.|
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Define um manipulador de eventos alterada do valor de inteiro.|
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|Define um manipulador de eventos de valor alterado.|
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|Informa se a transição relacionada são destruídos automaticamente.|
|[CAnimationBaseObject::GetGroupID](#getgroupid)|Retorna a ID do grupo atual.|
|[CAnimationBaseObject::GetObjectID](#getobjectid)|Retorna a ID do objeto atual.|
|[CAnimationBaseObject::GetUserData](#getuserdata)|Retorna os dados definidos pelo usuário.|
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|Define um sinalizador que ordena automaticamente destruir as transições.|
|[CAnimationBaseObject::SetID](#setid)|Define as IDs de novo.|
|[CAnimationBaseObject::SetUserData](#setuserdata)|Define os dados definidos pelo usuário.|

### <a name="protected-methods"></a>Métodos Protegidos

|Nome|Descrição|
|----------|-----------------|
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|Coleta os ponteiros para variáveis independentes de animação.|
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|Estabelece a relação entre variáveis de animação, contidas em um objeto de animação e seus contêineres.|

### <a name="protected-data-members"></a>Membros de dados protegidos

|Nome|Descrição|
|----------|-----------------|
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Especifica se as transições relacionadas devem ser destruídas automaticamente.|
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|Armazena dados definidos pelo usuário.|
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|Especifica a ID do grupo do objeto de animação.|
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|Especifica a ID de objeto do objeto de animação.|
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|Um ponteiro para o controlador de animação do pai.|

## <a name="remarks"></a>Comentários

Essa classe implementa os métodos básicos para todos os objetos de animação. Um objeto de animação pode representar um valor, a ponto, o tamanho, o retângulo ou a cor em um aplicativo, bem como qualquer entidade personalizada. Objetos de animação são armazenados nos grupos de animação (consulte CAnimationGroup). Cada grupo pode ser animado separadamente e pode ser tratado como um análogo do storyboard. Um objeto de animação encapsula uma ou mais animação variáveis (consulte CAnimationVariable), dependendo de sua representação lógica. Por exemplo, CAnimationRect contém quatro variáveis de animação - uma variável para cada lado do retângulo. Cada classe de objeto de animação expõe um método sobrecarregado AddTransition, que deve ser usado para aplicar as transições para variáveis de animação encapsulado. Um objeto de animação pode ser identificado pela ID de objeto (opcionalmente) e por ID de grupo. Uma ID de grupo é necessária para colocar um objeto de animação para o grupo correto, mas se uma ID de grupo não for especificada, um objeto é colocado no grupo padrão com ID 0. Se você chamar SetID com GroupID diferente, um objeto de animação será movido para outro grupo (um novo grupo é criado se necessário).

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationBaseObject`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxanimationcontroller.h

##  <a name="_dtorcanimationbaseobject"></a>  CAnimationBaseObject:: ~ CAnimationBaseObject

O destruidor. Chamado quando um objeto de animação está sendo destruído.

```
virtual ~CAnimationBaseObject();
```

##  <a name="applytransitions"></a>  CAnimationBaseObject::ApplyTransitions

Adiciona as transições ao storyboard com variável de animação encapsulado.

```
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parâmetros

*pStoryboard*<br/>
Um ponteiro para um storyboard.

*bDependOnKeyframes*<br/>
Com falso, este método adiciona somente as transições que não dependem de quadros-chave.

### <a name="return-value"></a>Valor de retorno

TRUE se as transições foram adicionados com êxito.

### <a name="remarks"></a>Comentários

Adiciona as transições relacionadas, que foram adicionadas com AddTransition (métodos sobrecarregados em classes derivadas), para executar o storyboard.

##  <a name="canimationbaseobject"></a>  CAnimationBaseObject::CAnimationBaseObject

Constrói um objeto de animação.

```
CAnimationBaseObject();

CAnimationBaseObject(
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parâmetros

*nGroupID*<br/>
Especifica a ID do grupo.

*nObjectID*<br/>
Especifica a ID de objeto.

*dwUserData*<br/>
Definido pelo usuário dados, que podem ser associados ao objeto de animação e recuperados posteriormente em tempo de execução.

### <a name="remarks"></a>Comentários

Constrói um objeto de animação e atribui a ID de objeto padrão (0) e a ID de grupo (0).

##  <a name="cleartransitions"></a>  CAnimationBaseObject::ClearTransitions

Remove todas as transições relacionadas.

```
virtual void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Parâmetros

*bAutodestroy*<br/>
Especifica se deve destruir objetos de transição automaticamente, ou apenas removê-los da lista relacionada.

### <a name="remarks"></a>Comentários

Remove todas relacionadas transições e destruindo-os se sinalizador bAutodestroy ou m_bAutodestroyTransitions for TRUE. Faz a transição deve ser destruída automaticamente somente se eles não são alocados na pilha. Se os sinalizadores acima forem FALSO, as transições apenas são removidas da lista interna de transições relacionadas.

##  <a name="containsvariable"></a>  CAnimationBaseObject::ContainsVariable

Determina se um objeto de animação contém uma variável de animação em particular.

```
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parâmetros

*pVariable*<br/>
Um ponteiro para a variável de animação.

### <a name="return-value"></a>Valor de retorno

TRUE se a variável de animação está contida no objeto de animação; Caso contrário, FALSE.

### <a name="remarks"></a>Comentários

Esse método pode ser usado para determinar se uma variável de animação especificada pelo pVariable está contida dentro de um objeto de animação. Um objeto de animação, dependendo do seu tipo, pode conter diversas variáveis de animação. Por exemplo, CAnimationColor contém três variáveis, uma para cada componente de cor (vermelho, verde e azul). Quando um valor de variável de animação é alterado, a API de animação do Windows envia eventos ValueChanged ou IntegerValueChanged (se habilitado) e o parâmetro desse evento é um ponteiro para a interface IUIAnimationVariable de variável de animação. Este método ajuda a obter um ponteiro para a animação de um ponteiro para o objeto contido de COM.

##  <a name="createtransitions"></a>  CAnimationBaseObject::CreateTransitions

Cria as transições associadas a um objeto de animação.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Valor de retorno

TRUE se as transições foram criadas com êxito; Caso contrário, FALSE.

### <a name="remarks"></a>Comentários

Executa um loop pela lista de variáveis de animação encapsulado em um objeto derivado de animação e cria transições associadas a cada variável de animação.

##  <a name="detachfromcontroller"></a>  CAnimationBaseObject::DetachFromController

Desanexa um objeto de animação do controlador de animação do pai.

```
void DetachFromController();
```

### <a name="remarks"></a>Comentários

Esse método é usado internamente.

##  <a name="enableintegervaluechangedevent"></a>  CAnimationBaseObject::EnableIntegerValueChangedEvent

Define um manipulador de eventos alterada do valor de inteiro.

```
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parâmetros

*pController*<br/>
Um ponteiro para um controlador de pai.

*bAtivar*<br/>
Especifica se deve habilitar ou desabilitar o evento alterado do valor de inteiro.

### <a name="remarks"></a>Comentários

Se o manipulador de evento alterado do valor de inteiro é habilitado, você pode manipular esse evento no método CAnimationController::OnAnimationIntegerValueChanged, que deve ser substituído em uma classe derivada de CAnimationController. Esse método é chamado sempre que o valor de inteiro de animação é alterado.

##  <a name="enablevaluechangedevent"></a>  CAnimationBaseObject::EnableValueChangedEvent

Define um manipulador de eventos de valor alterado.

```
virtual void EnableValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parâmetros

*pController*<br/>
Um ponteiro para um controlador de pai.

*bAtivar*<br/>
Especifica se deve habilitar ou desabilitar o evento alterado do valor.

### <a name="remarks"></a>Comentários

Se o manipulador de eventos de valor alterado estiver habilitado, você pode manipular esse evento no método CAnimationController::OnAnimationValueChanged, que deve ser substituído em uma classe derivada de CAnimationController. Esse método é chamado sempre que o valor de animação é alterado.

##  <a name="getanimationvariablelist"></a>  CAnimationBaseObject::GetAnimationVariableList

Coleta os ponteiros para variáveis independentes de animação.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst) = 0;
```

### <a name="parameters"></a>Parâmetros

*lst*<br/>
Uma lista que deve ser preenchida com variáveis de animação contidas em um objeto de animação.

### <a name="remarks"></a>Comentários

Isso é um método virtual puro que deve ser substituído em uma classe derivada. Um objeto de animação, dependendo do seu tipo, contém uma ou mais variáveis de animação. Por exemplo, CAnimationPoint contém duas variáveis, para coordenadas X e Y, respectivamente. A classe base CAnimationBaseObject implementa alguns métodos genéricos, que atuam em uma lista de variáveis de animação: ApplyTransitions, ClearTransitions, EnableValueChangedEvent, EnableIntegerValueChangedEvent. Esses métodos chamar GetAnimationVariableList, que é preenchido em uma classe derivada com variáveis de animação reais contidas em um objeto de animação em particular, e em seguida, executar um loop através da lista e executam ações necessárias. Se você criar um objeto de animação personalizada, você deve adicionar a lst todas as variáveis de animação contidas nesse objeto.

##  <a name="getautodestroytransitions"></a>  CAnimationBaseObject::GetAutodestroyTransitions

Informa se a transição relacionada são destruídos automaticamente.

```
BOOL GetAutodestroyTransitions() const;
```

### <a name="return-value"></a>Valor de retorno

Se for TRUE, as transições relacionadas são destruídas automaticamente. Se for FALSE, objetos de transição devem ser desalocados pelo aplicativo de chamada.

### <a name="remarks"></a>Comentários

Por padrão, esse sinalizador é verdadeiro. Defina esse sinalizador apenas se você alocado transição na pilha de e/ou transições devem ser desalocadas pelo aplicativo de chamada.

##  <a name="getgroupid"></a>  CAnimationBaseObject::GetGroupID

Retorna a ID do grupo atual.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Valor de retorno

ID do grupo atual.

### <a name="remarks"></a>Comentários

Use esse método para recuperar a ID do grupo. É um 0 se a ID do grupo não tiver sido definida explicitamente no construtor ou com SetID.

##  <a name="getobjectid"></a>  CAnimationBaseObject::GetObjectID

Retorna a ID do objeto atual.

```
UINT32 GetObjectID() const;
```

### <a name="return-value"></a>Valor de retorno

ID do objeto atual.

### <a name="remarks"></a>Comentários

Use esse método para recuperar a ID de objeto. É um 0 se a ID de objeto não tiver sido definida explicitamente no construtor ou com SetID.

##  <a name="getuserdata"></a>  CAnimationBaseObject::GetUserData

Retorna os dados definidos pelo usuário.

```
DWORD GetUserData() const;
```

### <a name="return-value"></a>Valor de retorno

Um valor de dados personalizados.

### <a name="remarks"></a>Comentários

Chame esse método para recuperar os dados personalizados em tempo de execução. O valor retornado será 0 se não foi inicializada explicitamente no construtor ou com SetUserData.

##  <a name="m_bautodestroytransitions"></a>  CAnimationBaseObject::m_bAutodestroyTransitions

Especifica se as transições relacionadas devem ser destruídas automaticamente.

```
BOOL m_bAutodestroyTransitions;
```

##  <a name="m_dwuserdata"></a>  CAnimationBaseObject::m_dwUserData

Armazena dados definidos pelo usuário.

```
DWORD m_dwUserData;
```

##  <a name="m_ngroupid"></a>  CAnimationBaseObject::m_nGroupID

Especifica a ID do grupo do objeto de animação.

```
UINT32 m_nGroupID;
```

##  <a name="m_nobjectid"></a>  CAnimationBaseObject::m_nObjectID

Especifica a ID de objeto do objeto de animação.

```
UINT32 m_nObjectID;
```

##  <a name="m_pparentcontroller"></a>  CAnimationBaseObject::m_pParentController

Um ponteiro para o controlador de animação do pai.

```
CAnimationController* m_pParentController;
```

##  <a name="setautodestroytransitions"></a>  CAnimationBaseObject::SetAutodestroyTransitions

Define um sinalizador que ordena automaticamente destruir as transições.

```
void SetAutodestroyTransitions(BOOL bValue);
```

### <a name="parameters"></a>Parâmetros

*bValue*<br/>
Especifica o sinalizador de destruir o automaticamente.

### <a name="remarks"></a>Comentários

Defina esse sinalizador apenas se você alocada a objetos de transição, usando o operador novo. Se por algum motivo, os objetos de transição são alocados na pilha, destruir o auto sinalizador deve ser FALSE. Por padrão, esse sinalizador é verdadeiro.

##  <a name="setid"></a>  CAnimationBaseObject::SetID

Define as IDs de novo.

```
void SetID(
    UINT32 nObjectID,
    UINT32 nGroupID = 0);
```

### <a name="parameters"></a>Parâmetros

*nObjectID*<br/>
Especifica a nova ID de objeto.

*nGroupID*<br/>
Especifica a ID do novo grupo.

### <a name="remarks"></a>Comentários

Permite para alterar a ID de objeto e a ID do grupo. Se a nova ID de grupo for diferente da ID da atual, um objeto de animação é movido para outro grupo (um novo grupo será criado, se necessário).

##  <a name="setparentanimationobjects"></a>  CAnimationBaseObject::SetParentAnimationObjects

Estabelece a relação entre variáveis de animação, contidas em um objeto de animação e seus contêineres.

```
virtual void SetParentAnimationObjects();
```

### <a name="remarks"></a>Comentários

Isso é um auxiliar que pode ser usado para estabelecer a relação entre variáveis de animação, contidas em um objeto de animação e seus contêineres. Ele faz um loop sobre variáveis de animação e define um ponteiro para voltar a um objeto de animação de pai para cada variável de animação. Na implementação atual que a relação real é estabelecida na CAnimationBaseObject::ApplyTransitions, portanto ponteiros de back-não estão definidos até que você chame CAnimationGroup::Animate. Saber que a relação pode ser útil quando você o processamento de eventos e a necessidade de uma animação pai do objeto de CAnimationVariable (use CAnimationVariable::GetParentAnimationObject).

##  <a name="setuserdata"></a>  CAnimationBaseObject::SetUserData

Define os dados definidos pelo usuário.

```
void SetUserData (DWORD dwUserData);
```

### <a name="parameters"></a>Parâmetros

*dwUserData*<br/>
Especifica os dados personalizados.

### <a name="remarks"></a>Comentários

Use esse método para associar um dados personalizados um objeto de animação. Esses dados podem ser recuperados posteriormente em tempo de execução por GetUserData.

## <a name="see-also"></a>Consulte também

[Classes](../../mfc/reference/mfc-classes.md)
