---
title: Classe CAnimationSize | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCX
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCY
- AFXANIMATIONCONTROLLER/CAnimationSize::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetValue
- AFXANIMATIONCONTROLLER/CAnimationSize::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cxValue
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cyValue
dev_langs:
- C++
helpviewer_keywords:
- CAnimationSize class
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
caps.latest.revision: 17
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
ms.sourcegitcommit: 73410ae17465880f455e5b15026f6cc010803c19
ms.openlocfilehash: 84b9ae3b81f72f6c0ae8e88f78357c29e8d82ffd
ms.lasthandoff: 02/25/2017

---
# <a name="canimationsize-class"></a>Classe CAnimationSize
Implementa a funcionalidade de um objeto size cujas dimensões podem ser animadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class CAnimationSize : public CAnimationBaseObject;  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CAnimationSize::CAnimationSize](#canimationsize)|Sobrecarregado. Constrói um objeto de tamanho de animação.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CAnimationSize::AddTransition](#addtransition)|Adiciona as transições de largura e altura.|  
|[CAnimationSize::GetCX](#getcx)|Fornece acesso a CAnimationVariable que representa a largura.|  
|[CAnimationSize::GetCY](#getcy)|Fornece acesso a CAnimationVariable que representa a altura.|  
|[CAnimationSize::GetDefaultValue](#getdefaultvalue)|Retorna os valores padrão para largura e altura.|  
|[CAnimationSize::GetValue](#getvalue)|Retorna o valor atual.|  
|[CAnimationSize::SetDefaultValue](#setdefaultvalue)|Define o valor padrão.|  
  
### <a name="protected-methods"></a>Métodos Protegidos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CAnimationSize::GetAnimationVariableList](#getanimationvariablelist)|Coloca as variáveis de animação encapsulado em uma lista. (Substitui [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CAnimationSize::operator CSize](#operator_csize)|Converte uma CAnimationSize uma CSize.|  
|[CAnimationSize::operator =](#operator_eq)|Atribui szSrc a CAnimationSize.|  
  
### <a name="protected-data-members"></a>Membros de dados protegidos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CAnimationSize::m_cxValue](#m_cxvalue)|A variável de animação encapsulado que representa a largura do tamanho da animação.|  
|[CAnimationSize::m_cyValue](#m_cyvalue)|A variável de animação encapsulado que representa a altura do tamanho da animação.|  
  
## <a name="remarks"></a>Comentários  
 A classe CAnimationSize encapsula os dois objetos CAnimationVariable e pode representar em aplicativos de um tamanho. Por exemplo, você pode usar esta classe para animar um tamanho de quaisquer dois objeto tridimensional na tela (como um retângulo, controlar etc). Para usar essa classe no aplicativo, simplesmente instanciar um objeto dessa classe, adicioná-lo ao controlador de animação usando CAnimationController::AddAnimationObject e chamar AddTransition para cada transição a ser aplicado à largura e/ou altura.  
  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)  
  
 `CAnimationSize` 
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** afxanimationcontroller.h  
  
##  <a name="addtransition"></a>CAnimationSize::AddTransition  
 Adiciona as transições de largura e altura.  
  
```  
void AddTransition(
    CBaseTransition* pCXTransition,  
    CBaseTransition* pCYTransition);
```  
  
### <a name="parameters"></a>Parâmetros  
 `pCXTransition`  
 Um ponteiro para fazer a transição para a largura.  
  
 `pCYTransition`  
 Um ponteiro para fazer a transição para a altura.  
  
### <a name="remarks"></a>Comentários  
 Chame essa função para adicionar as transições especificadas para a lista interna de transições a ser aplicado às variáveis de animação para largura e altura. Ao adicionar transições, eles não são aplicados imediatamente e armazenados em uma lista interna. As transições são aplicadas (adicionadas a um storyboard para um determinado valor) quando você chamar CAnimationController::AnimateGroup. Se você não precisa aplicar uma transição de dimensões, é possível passar NULL.  
  
##  <a name="canimationsize"></a>CAnimationSize::CAnimationSize  
 Constrói um objeto de tamanho de animação.  
  
```  
CAnimationSize();

 
CAnimationSize(
    const CSize& szDefault,  
    UINT32 nGroupID,  
    UINT32 nObjectID = (UINT32)-1,  
    DWORD dwUserData = 0);
```  
  
### <a name="parameters"></a>Parâmetros  
 `szDefault`  
 Especifica o tamanho padrão.  
  
 `nGroupID`  
 Especifica a ID do grupo.  
  
 `nObjectID`  
 Especifica a ID do objeto.  
  
 `dwUserData`  
 Especifica os dados definidos pelo usuário.  
  
### <a name="remarks"></a>Comentários  
 O objeto é criado com valores padrão para largura, altura, objeto ID e a ID de grupo, que será definido como 0. Eles podem ser alterados posteriormente em tempo de execução usando SetDefaultValue e SetID.  
  
##  <a name="getanimationvariablelist"></a>CAnimationSize::GetAnimationVariableList  
 Coloca as variáveis de animação encapsulado em uma lista.  
  
```  
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*, 
    CAnimationVariable*>& lst);
```  
  
### <a name="parameters"></a>Parâmetros  
 `lst`  
 Quando a função retorna, contém ponteiros para os dois objetos CAnimationVariable que representa a largura e altura.  
  
##  <a name="getcx"></a>CAnimationSize::GetCX  
 Fornece acesso a CAnimationVariable que representa a largura.  
  
```  
CAnimationVariable& GetCX();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Uma referência a CAnimationVariable encapsulado que representa a largura.  
  
### <a name="remarks"></a>Comentários  
 Você pode chamar esse método para obter acesso direto ao CAnimationVariable subjacente que representa a largura.  
  
##  <a name="getcy"></a>CAnimationSize::GetCY  
 Fornece acesso a CAnimationVariable que representa a altura.  
  
```  
CAnimationVariable& GetCY();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Uma referência a CAnimationVariable encapsulado que representa a altura.  
  
### <a name="remarks"></a>Comentários  
 Você pode chamar esse método para obter acesso direto ao CAnimationVariable subjacente que representa a altura.  
  
##  <a name="getdefaultvalue"></a>CAnimationSize::GetDefaultValue  
 Retorna os valores padrão para largura e altura.  
  
```  
CSize GetDefaultValue();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um objeto de CSize que contém valores padrão.  
  
### <a name="remarks"></a>Comentários  
 Chame essa função para recuperar o valor padrão, que foi definida anteriormente pelo construtor ou SetDefaultValue.  
  
##  <a name="getvalue"></a>CAnimationSize::GetValue  
 Retorna o valor atual.  
  
```  
BOOL GetValue(CSize& szValue);
```  
  
### <a name="parameters"></a>Parâmetros  
 `szValue`  
 Saída. Quando este método retorna, contém o valor atual.  
  
### <a name="return-value"></a>Valor de retorno  
 TRUE se o valor atual foi recuperado com êxito. Caso contrário, FALSE.  
  
### <a name="remarks"></a>Comentários  
 Chame essa função para recuperar o valor atual de tamanho de animação. Se esse método falhar ou objetos subjacentes para a largura e o tamanho não foram inicializados, szValue contém o valor padrão, que foi anteriormente definido no construtor ou por SetDefaultValue.  
  
##  <a name="m_cxvalue"></a>CAnimationSize::m_cxValue  
 A variável de animação encapsulado que representa a largura do tamanho da animação.  
  
```  
CAnimationVariable m_cxValue;  
```  
  
##  <a name="m_cyvalue"></a>CAnimationSize::m_cyValue  
 A variável de animação encapsulado que representa a altura do tamanho da animação.  
  
```  
CAnimationVariable m_cyValue;  
```  
  
##  <a name="operator_csize"></a>CAnimationSize::operator CSize  
 Converte uma CAnimationSize uma CSize.  
  
```  
operator CSize();
```   
  
### <a name="return-value"></a>Valor de retorno  
 Valor atual do tamanho da animação como CSize.  
  
### <a name="remarks"></a>Comentários  
 Essa função chama internamente GetValue. Se falhar GetValue por algum motivo, o tamanho retornado conterá valores padrão para largura e altura.  
  
##  <a name="operator_eq"></a>CAnimationSize::operator =  
 Atribui szSrc a CAnimationSize.  
  
```  
void operator=(const CSize& szSrc);
```  
  
### <a name="parameters"></a>Parâmetros  
 `szSrc`  
 Refere-se ao CSize ou tamanho.  
  
### <a name="remarks"></a>Comentários  
 Atribui szSrc a CAnimationSize. Recomenda-se para fazer isso antes do início da animação, porque esse operador chama SetDefaultValue, que recria os objetos subjacentes para largura e altura, se eles tiverem sido criados. Se você se inscreveu nesse objeto de animação para eventos (ValueChanged ou IntegerValueChanged), você precisa habilitar novamente esses eventos.  
  
##  <a name="setdefaultvalue"></a>CAnimationSize::SetDefaultValue  
 Define o valor padrão.  
  
```  
void SetDefaultValue(const CSize& szDefault);
```  
  
### <a name="parameters"></a>Parâmetros  
 `szDefault`  
 Especifica o novo tamanho padrão.  
  
### <a name="remarks"></a>Comentários  
 Use esta função para definir um valor padrão para o objeto de animação. Este métodos atribui valores padrão para largura e altura do tamanho da animação. Ele também recria os objetos subjacentes se eles foram criados. Se você se inscreveu nesse objeto de animação para eventos (ValueChanged ou IntegerValueChanged), você precisa habilitar novamente esses eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Classes](../../mfc/reference/mfc-classes.md)
