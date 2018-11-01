---
title: Classe IRunnableObjectImpl
ms.date: 11/04/2016
f1_keywords:
- IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl::GetRunningClass
- ATLCTL/ATL::IRunnableObjectImpl::IsRunning
- ATLCTL/ATL::IRunnableObjectImpl::LockRunning
- ATLCTL/ATL::IRunnableObjectImpl::Run
- ATLCTL/ATL::IRunnableObjectImpl::SetContainedObject
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
ms.openlocfilehash: ebee914ffb9caea905b9bf2daab87dc379ab20e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646496"
---
# <a name="irunnableobjectimpl-class"></a>Classe IRunnableObjectImpl

Essa classe implementa `IUnknown` e fornece uma implementação padrão do [IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject) interface.

> [!IMPORTANT]
>  Essa classe e seus membros não podem ser usados em aplicativos executados no tempo de execução do Windows.

## <a name="syntax"></a>Sintaxe

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>Parâmetros

*T*<br/>
Sua classe, derivada de `IRunnableObjectImpl`.

## <a name="members"></a>Membros

### <a name="public-methods"></a>Métodos Públicos

|Nome|Descrição|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Retorna o CLSID do controle em execução. A implementação de ATL define o CLSID para GUID_NULL e retornará E_UNEXPECTED.|
|[IRunnableObjectImpl::IsRunning](#isrunning)|Determina se o controle está em execução. A implementação de ATL retorna TRUE.|
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Bloqueia o controle para o estado de execução. A implementação de ATL Retorna S_OK.|
|[IRunnableObjectImpl::Run](#run)|Força a execução do controle. A implementação de ATL Retorna S_OK.|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Indica que o controle é inserido. A implementação de ATL Retorna S_OK.|

## <a name="remarks"></a>Comentários

O [IRunnableObject](/windows/desktop/api/objidl/nn-objidl-irunnableobject) interface permite que um contêiner determinar se um controle está em execução, forçá-lo a executar ou bloqueá-la em estado de execução. Classe `IRunnableObjectImpl` fornece uma implementação padrão dessa interface e implementa `IUnknown` enviando informações para o despejo de compilações de dispositivo na depuração.

**Artigos relacionados** [Tutorial da ATL](../../atl/active-template-library-atl-tutorial.md), [criando um projeto ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atlctl.h

##  <a name="getrunningclass"></a>  IRunnableObjectImpl::GetRunningClass

Retorna o CLSID do controle em execução.

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>Valor de retorno

Os conjuntos de implementação de ATL \* *lpClsid* GUID_NULL e retornará E_UNEXPECTED.

### <a name="remarks"></a>Comentários

Ver [IRunnableObject::GetRunningClass](/windows/desktop/api/objidl/nf-objidl-irunnableobject-getrunningclass) no Windows SDK.

##  <a name="isrunning"></a>  IRunnableObjectImpl::IsRunning

Determina se o controle está em execução.

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>Valor de retorno

A implementação de ATL retorna TRUE.

### <a name="remarks"></a>Comentários

Ver [IRunnableObject::IsRunning](/windows/desktop/api/objidl/nf-objidl-irunnableobject-isrunning) no Windows SDK.

##  <a name="lockrunning"></a>  IRunnableObjectImpl::LockRunning

Bloqueia o controle para o estado de execução.

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>Valor de retorno

A implementação de ATL Retorna S_OK.

### <a name="remarks"></a>Comentários

Ver [IRunnableObject::LockRunning](/windows/desktop/api/objidl/nf-objidl-irunnableobject-lockrunning) no Windows SDK.

##  <a name="run"></a>  IRunnableObjectImpl::Run

Força a execução do controle.

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>Valor de retorno

A implementação de ATL Retorna S_OK.

### <a name="remarks"></a>Comentários

Ver [IRunnableObject::Run](/windows/desktop/api/objidl/nf-objidl-irunnableobject-run) no Windows SDK.

##  <a name="setcontainedobject"></a>  IRunnableObjectImpl::SetContainedObject

Indica que o controle é inserido.

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>Valor de retorno

A implementação de ATL Retorna S_OK.

### <a name="remarks"></a>Comentários

Ver [IRunnableObject::SetContainedObject](/windows/desktop/api/objidl/nf-objidl-irunnableobject-setcontainedobject) no Windows SDK.

## <a name="see-also"></a>Consulte também

[Classe CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Visão geral da classe](../../atl/atl-class-overview.md)
