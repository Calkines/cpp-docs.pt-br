---
title: Classe CComPolyObject | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
dev_langs:
- C++
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
caps.latest.revision: 19
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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: ee44fcec146ef8a8c68b917020ae52e2300eed5e
ms.lasthandoff: 03/31/2017

---
# <a name="ccompolyobject-class"></a>Classe CComPolyObject
Essa classe implementa **IUnknown** para um objeto agregado ou agregado.  
  
## <a name="syntax"></a>Sintaxe  
  
```
template<class contained>  
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```  
  
#### <a name="parameters"></a>Parâmetros  
 `contained`  
 A classe derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), bem como qualquer outra interface desejar dar suporte ao objeto.  
  
## <a name="members"></a>Membros  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CComPolyObject::CComPolyObject](#ccompolyobject)|O construtor.|  
|[CComPolyObject:: ~ CComPolyObject](#dtor)|O destruidor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CComPolyObject::AddRef](#addref)|Incrementa a contagem de referência do objeto.|  
|[CComPolyObject::CreateInstance](#createinstance)|(Estático) Permite que você crie um novo **CComPolyObject** `contained` **>** objeto sem a sobrecarga de [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).|  
|[CComPolyObject::FinalConstruct](#finalconstruct)|Executa a inicialização final de `m_contained`.|  
|[CComPolyObject::FinalRelease](#finalrelease)|Executa a destruição de final de `m_contained`.|  
|[CComPolyObject::QueryInterface](#queryinterface)|Recupera um ponteiro para a interface solicitada.|  
|[CComPolyObject::Release](#release)|Contagem de referência do objeto diminui.|  
  
### <a name="public-data-members"></a>Membros de Dados Públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CComPolyObject::m_contained](#m_contained)|Delegados **IUnknown** chamadas para o externo desconhecido se o objeto é agregado ou para o **IUnknown** do objeto se o objeto não é agregado.|  
  
## <a name="remarks"></a>Comentários  
 `CComPolyObject`implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para um objeto agregado ou agregado.  
  
 Quando uma instância de `CComPolyObject` é criado, o valor de externo desconhecido é verificado. Se for **nulo**, **IUnknown** é implementada por um objeto agregado. Se o desconhecido externo não é **nulo**, **IUnknown** é implementada por um objeto agregado.  
  
 A vantagem de usar `CComPolyObject` é evitar ter dois [CComAggObject](../../atl/reference/ccomaggobject-class.md) e [CComObject](../../atl/reference/ccomobject-class.md) em seu módulo para lidar com casos agregados e agregados. Um único `CComPolyObject` objeto lida com ambos os casos. Isso significa que apenas uma cópia do vtable e uma cópia das funções existem em seu módulo. Se seu vtable for grande, isso pode diminuir significativamente o tamanho do módulo. No entanto, se seu vtable for pequeno, usando `CComPolyObject` pode resultar em um tamanho ligeiramente maior do módulo porque ele não é otimizado para um objeto agregado ou agregado, assim como `CComAggObject` e `CComObject`.  
  
 Se o `DECLARE_POLY_AGGREGATABLE` macro é especificada na definição de classe do objeto, `CComPolyObject` será usado para criar o objeto. `DECLARE_POLY_AGGREGATABLE`serão automaticamente declarados se você usar o Assistente de projeto de ATL para criar um controle de Internet Explorer ou controle total.  
  
 Se agregados, o `CComPolyObject` objeto tem seu próprio **IUnknown**separado do objeto externo **IUnknown**e mantém seu próprio contagem de referência. `CComPolyObject`usa [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) delegue externo desconhecido.  
  
 Para obter mais informações sobre a agregação, consulte o artigo [Fundamentals de ATL COM objetos](../../atl/fundamentals-of-atl-com-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComPolyObject`  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** atlcom.h  
  
##  <a name="addref"></a>CComPolyObject::AddRef  
 Incrementa a contagem de referência no objeto.  
  
```
STDMETHOD_(ULONG, AddRef)();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um valor que pode ser útil para um diagnóstico ou teste.  
  
##  <a name="ccompolyobject"></a>CComPolyObject::CComPolyObject  
 O construtor.  
  
```
CComPolyObject(void* pv);
```  
  
### <a name="parameters"></a>Parâmetros  
 `pv`  
 [in] Um ponteiro para externo desconhecido se o objeto é agregada, ou **nulo** se o objeto se o objeto não é agregado.  
  
### <a name="remarks"></a>Comentários  
 Inicializa o `CComContainedObject` membro de dados, [m_contained](#m_contained)e incrementa a contagem de bloqueios do módulo.  
  
 Decrementa o destruidor a módulo contagem de bloqueio.  
  
##  <a name="dtor"></a>CComPolyObject:: ~ CComPolyObject  
 O destruidor.  
  
```
~CComPolyObject();
```  
  
### <a name="remarks"></a>Comentários  
 Libera todos os recursos alocados, chamadas [FinalRelease](#finalrelease), e diminui a módulo contagem de bloqueio.  
  
##  <a name="createinstance"></a>CComPolyObject::CreateInstance  
 Permite que você crie um novo **CComPolyObject** `contained` **>** objeto sem a sobrecarga de [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).  
  
```
static HRESULT WINAPI CreateInstance(  
    LPUNKNOWN pUnkOuter, 
    CComPolyObject<contained>** pp);
```  
  
### <a name="parameters"></a>Parâmetros  
 `pp`  
 [out] Um ponteiro para um **CComPolyObject** `contained` **>** ponteiro. Se `CreateInstance` for bem-sucedido, `pp` é definido como **nulo**.  
  
### <a name="return-value"></a>Valor de retorno  
 Um padrão `HRESULT` valor.  
  
### <a name="remarks"></a>Comentários  
 O objeto retornado tem uma contagem de referência igual a zero, portanto, chame `AddRef` imediatamente, em seguida, use **versão** para liberar a referência no ponteiro de objeto quando estiver pronto.  
  
 Se você não precisa de acesso ao objeto direto, mas ainda deseja criar um novo objeto sem a sobrecarga de `CoCreateInstance`, use [CComCoClass::CreateInstance](../../atl/reference/ccomcoclass-class.md#createinstance) em vez disso.  
  
##  <a name="finalconstruct"></a>CComPolyObject::FinalConstruct  
 Chamado durante os estágios finais da construção do objeto, esse método executa qualquer inicialização final sobre o [m_contained](#m_contained) membro de dados.  
  
```
HRESULT FinalConstruct();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um padrão `HRESULT` valor.  
  
##  <a name="finalrelease"></a>CComPolyObject::FinalRelease  
 Chamado durante a destruição do objeto, esse método libera o [m_contained](#m_contained) membro de dados.  
  
```
void FinalRelease();
```  
  
##  <a name="m_contained"></a>CComPolyObject::m_contained  
 Um [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) objeto derivado de sua classe.  
  
```
CComContainedObject<contained> m_contained;
```  
  
### <a name="parameters"></a>Parâmetros  
 `contained`  
 [in] A classe derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) ou [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), bem como qualquer outra interface desejar dar suporte ao objeto.  
  
### <a name="remarks"></a>Comentários  
 **IUnknown** chamadas por meio de `m_contained` são delegadas a externo desconhecido se o objeto é agregado ou para o **IUnknown** deste objeto, se o objeto não é agregado.  
  
##  <a name="queryinterface"></a>CComPolyObject::QueryInterface  
 Recupera um ponteiro para a interface solicitada.  
  
```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>  
HRESULT QueryInterface(Q** pp);
```  
  
### <a name="parameters"></a>Parâmetros  
 `Q`  
 A interface COM.  
  
 `iid`  
 [in] O identificador da interface que está sendo solicitado.  
  
 `ppvObject`  
 [out] Um ponteiro para o ponteiro de interface identificado por `iid`. Se o objeto não oferece suporte a essa interface, `ppvObject` é definido como **nulo**.  
  
 `pp`  
 [out] Um ponteiro para a interface identificado por **__uuidof(Q)**.  
  
### <a name="return-value"></a>Valor de retorno  
 Um padrão `HRESULT` valor.  
  
### <a name="remarks"></a>Comentários  
 Para um objeto agregado, se a interface solicitada é **IUnknown**, `QueryInterface` retorna um ponteiro para o agregado do objeto próprio **IUnknown** e incrementa a contagem de referência. Caso contrário, esse método de consulta para a interface por meio de `CComContainedObject` membro de dados, [m_contained](#m_contained).  
  
##  <a name="release"></a>CComPolyObject::Release  
 Diminui a contagem de referência no objeto.  
  
```
STDMETHOD_(ULONG, Release)();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Em compilações de depuração, **versão** retorna um valor que pode ser útil para um diagnóstico ou teste. Em compilações de nondebug **versão** sempre retorna 0.  
  
## <a name="see-also"></a>Consulte também  
 [Classe CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)   
 [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)   
 [Visão geral da classe](../../atl/atl-class-overview.md)
