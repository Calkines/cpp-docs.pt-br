---
title: Classe CAtlComModule | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
dev_langs:
- C++
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0600476df22c3d87bc5694e9ffe2af09f4542439
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063257"
---
# <a name="catlcommodule-class"></a>Classe CAtlComModule

Essa classe implementa um módulo de servidor COM.

## <a name="syntax"></a>Sintaxe

```
class CAtlComModule : public _ATL_COM_MODULE
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|[CAtlComModule::CAtlComModule](#catlcommodule)|O construtor.|
|[CAtlComModule:: ~ CAtlComModule](#dtor)|O destruidor.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CAtlComModule::RegisterServer](#registerserver)|Chame esse método para atualizar o registro do sistema para cada objeto no mapa de objetos.|
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Chame esse método para registrar uma biblioteca de tipos.|
|[CAtlComModule::UnregisterServer](#unregisterserver)|Chame esse método para cancelar o registro de cada objeto no mapa de objetos.|
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Chame esse método para cancelar o registro de uma biblioteca de tipos.|

## <a name="remarks"></a>Comentários

`CAtlComModule` implementa um módulo de servidor COM, permitindo que um cliente acessar os componentes do módulo.

Essa classe substitui o obsoletos [CComModule](../../atl/reference/ccommodule-class.md) classe usado em versões anteriores do ATL. Ver [Classes de módulo ATL](../../atl/atl-module-classes.md) para obter mais detalhes.

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)

`CAtlComModule`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atlbase. h

##  <a name="catlcommodule"></a>  CAtlComModule::CAtlComModule

O construtor.

```
CAtlComModule() throw();
```

### <a name="remarks"></a>Comentários

Inicializa o módulo.

##  <a name="dtor"></a>  CAtlComModule:: ~ CAtlComModule

O destruidor.

```
~CAtlComModule();
```

### <a name="remarks"></a>Comentários

Libera todas as fábricas de classe.

##  <a name="registerserver"></a>  CAtlComModule::RegisterServer

Chame esse método para atualizar o registro do sistema para cada objeto no mapa de objetos.

```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parâmetros

*bRegTypeLib*<br/>
TRUE se a biblioteca de tipos deve ser registrado. O valor padrão é FALSE.

*pCLSID*<br/>
Aponta para o CLSID do objeto a ser registrado. Se NULL (o valor padrão), todos os objetos no mapa de objetos será registrado.

### <a name="return-value"></a>Valor de retorno

Retorna S_OK no êxito ou um erro HRESULT em caso de falha.

### <a name="remarks"></a>Comentários

Chama a função global [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver).

##  <a name="registertypelib"></a>  CAtlComModule::RegisterTypeLib

Chame esse método para registrar uma biblioteca de tipos.

```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```

### <a name="parameters"></a>Parâmetros

*lpszIndex*<br/>
Cadeia de caracteres no formato "\\\N", onde N é o índice de inteiro do recurso TYPELIB.

### <a name="return-value"></a>Valor de retorno

Retorna S_OK no êxito ou um erro HRESULT em caso de falha.

### <a name="remarks"></a>Comentários

Adiciona informações sobre uma biblioteca de tipos para o registro do sistema. Se a instância de módulo contém várias bibliotecas de tipos, use a primeira versão desse método para especificar qual biblioteca de tipo deve ser usada.

##  <a name="unregisterserver"></a>  CAtlComModule::UnregisterServer

Chame esse método para cancelar o registro de cada objeto no mapa de objetos.

```
HRESULT UnregisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL);
```

### <a name="parameters"></a>Parâmetros

*bRegTypeLib*<br/>
TRUE se a biblioteca de tipos deve ser cancelado. O valor padrão é FALSE.

*pCLSID*<br/>
Aponta para o CLSID do objeto a ser cancelado. Se NULL (o valor padrão), todos os objetos no mapa de objetos será cancelado.

### <a name="return-value"></a>Valor de retorno

Retorna S_OK no êxito ou um erro HRESULT em caso de falha.

### <a name="remarks"></a>Comentários

Chama a função global [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).

##  <a name="unregistertypelib"></a>  CAtlComModule::UnRegisterTypeLib

Chame esse método para cancelar o registro de uma biblioteca de tipos.

```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```

### <a name="parameters"></a>Parâmetros

*lpszIndex*<br/>
Cadeia de caracteres no formato "\\\N", onde N é o índice de inteiro do recurso TYPELIB.

### <a name="remarks"></a>Comentários

Remove informações sobre uma biblioteca de tipos do registro do sistema. Se a instância de módulo contém várias bibliotecas de tipos, use a primeira versão desse método para especificar qual biblioteca de tipo deve ser usada.

### <a name="return-value"></a>Valor de retorno

Retorna S_OK no êxito ou um erro HRESULT em caso de falha.

## <a name="see-also"></a>Consulte também

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)<br/>
[Visão geral da classe](../../atl/atl-class-overview.md)
