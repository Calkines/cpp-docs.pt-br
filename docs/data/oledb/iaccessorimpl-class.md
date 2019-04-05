---
title: Classe IAccessorImpl
ms.date: 11/04/2016
f1_keywords:
- IAccessorImpl
- ATL.IAccessorImpl.IAccessorImpl
- ATL::IAccessorImpl::IAccessorImpl
- IAccessorImpl::IAccessorImpl
- IAccessorImpl.IAccessorImpl
- IAccessorImpl
- ATL::IAccessorImpl::AddRefAccessor
- AddRefAccessor
- IAccessorImpl::AddRefAccessor
- IAccessorImpl.AddRefAccessor
- ATL.IAccessorImpl.AddRefAccessor
- IAccessorImpl::CreateAccessor
- CreateAccessor
- ATL::IAccessorImpl::CreateAccessor
- IAccessorImpl.CreateAccessor
- ATL.IAccessorImpl.CreateAccessor
- IAccessorImpl.GetBindings
- ATL::IAccessorImpl::GetBindings
- IAccessorImpl::GetBindings
- GetBindings
- ATL.IAccessorImpl.GetBindings
- ReleaseAccessor
- IAccessorImpl::ReleaseAccessor
- ATL.IAccessorImpl.ReleaseAccessor
- ATL::IAccessorImpl::ReleaseAccessor
- IAccessorImpl.ReleaseAccessor
helpviewer_keywords:
- IAccessorImpl class
- IAccessorImpl class, constructor
- IAccessorImpl constructor
- AddRefAccessor method
- CreateAccessor method
- GetBindings method
- ReleaseAccessor method
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
ms.openlocfilehash: a4f98cdfea9ea1e82ec0a3de09e292604a6c199f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032109"
---
# <a name="iaccessorimpl-class"></a>Classe IAccessorImpl

Fornece uma implementação de [IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85)) interface.

## <a name="syntax"></a>Sintaxe

```cpp
template <class T,
   class BindType = ATLBINDINGS,
   class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>
```

### <a name="parameters"></a>Parâmetros

*T*<br/>
Sua classe de objeto do conjunto de linhas ou de comando.

*BindType*<br/>
Unidade de armazenamento de informações de associação. O padrão é o `ATLBINDINGS` estrutura (consulte atldb.h).

*BindingVector*<br/>
Unidade de armazenamento para informações de coluna. O padrão é [CAtlMap](../../atl/reference/catlmap-class.md) onde o elemento-chave é um valor HACCESSOR e o elemento de valor é um ponteiro para um `BindType` estrutura.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atldb.h

## <a name="members"></a>Membros

### <a name="methods"></a>Métodos

|||
|-|-|
|[IAccessorImpl](#iaccessorimpl)|O construtor.|

### <a name="interface-methods"></a>Métodos de interface

|||
|-|-|
|[AddRefAccessor](#addrefaccessor)|Adiciona uma contagem de referência a acessador existente.|
|[CreateAccessor](#createaccessor)|Cria um acessador de um conjunto de associações.|
|[GetBindings](#getbindings)|Retorna as associações em um acessador.|
|[ReleaseAccessor](#releaseaccessor)|Libera um acessador.|

## <a name="remarks"></a>Comentários

Isso é obrigatório em conjuntos de linhas e comandos. OLE DB exige que os provedores implementar um HACCESSOR, que é uma marca para uma matriz de [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) estruturas. HACCESSORs fornecidos pelo `IAccessorImpl` são os endereços do `BindType` estruturas. Por padrão, `BindType` é definido como um `ATLBINDINGS` no `IAccessorImpl`da definição de modelo. `BindType` Fornece um mecanismo usado pelo `IAccessorImpl` para controlar o número de elementos no seu `DBBINDING` , bem como um sinalizadores de acessador e contagem de referência de matriz.

## <a name="iaccessorimpl"></a> IAccessorImpl::IAccessorImpl

O construtor.

### <a name="syntax"></a>Sintaxe

```cpp
IAccessorImpl();
```

## <a name="addrefaccessor"></a> IAccessorImpl::AddRefAccessor

Adiciona uma contagem de referência a acessador existente.

### <a name="syntax"></a>Sintaxe

```cpp
STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Parâmetros

Ver [IAccessor::AddRefAccessor](/previous-versions/windows/desktop/ms714978(v=vs.85)) na *referência do programador do OLE DB*.

## <a name="createaccessor"></a> IAccessorImpl::CreateAccessor

Cria um acessador de um conjunto de associações.

### <a name="syntax"></a>Sintaxe

```cpp
STDMETHOD(CreateAccessor)(DBACCESSORFLAGS dwAccessorFlags,
   DBCOUNTITEM cBindings,
   const DBBINDING rgBindings[],
   DBLENGTH cbRowSize,
   HACCESSOR* phAccessor,
   DBBINDSTATUS rgStatus[]);
```

#### <a name="parameters"></a>Parâmetros

Ver [IAccessor:: CreateAccessor](/previous-versions/windows/desktop/ms720969(v=vs.85)) na *referência do programador do OLE DB*.

## <a name="getbindings"></a> IAccessorImpl::GetBindings

Retorna as associações de colunas básico do consumidor em um acessador.

### <a name="syntax"></a>Sintaxe

```cpp
STDMETHOD(GetBindings)(HACCESSOR hAccessor,
   DBACCESSORFLAGS* pdwAccessorFlags,
   DBCOUNTITEM* pcBindings,
   DBBINDING** prgBindings);
```

#### <a name="parameters"></a>Parâmetros

Ver [IAccessor::GetBindings](/previous-versions/windows/desktop/ms721253(v=vs.85)) na *referência do programador do OLE DB*.

## <a name="releaseaccessor"></a> IAccessorImpl::ReleaseAccessor

Libera um acessador.

### <a name="syntax"></a>Sintaxe

```cpp
STDMETHOD(ReleaseAccessor)(HACCESSOR hAccessor,
   DBREFCOUNT* pcRefCount);
```

#### <a name="parameters"></a>Parâmetros

Ver [IAccessor:: Releaseaccessor](/previous-versions/windows/desktop/ms719717(v=vs.85)) na *referência do programador do OLE DB*.

## <a name="see-also"></a>Consulte também

[Modelos de provedor de banco de dados OLE](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitetura de modelo do provedor de banco de dados OLE](../../data/oledb/ole-db-provider-template-architecture.md)