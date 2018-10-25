---
title: Funções globais de mapa COM | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5c158e5b59decd751340f87d5c29c572d6972d8e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077901"
---
# <a name="com-map-global-functions"></a>Funções globais de mapa COM

Essas funções fornecem suporte para o mapa COM `IUnknown` implementações.

|||
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Delega para o `IUnknown` de um objeto não agregado.|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Gera um código eficiente para comparar as interfaces com `IUnknown`.|

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atlbase. h

##  <a name="atlinternalqueryinterface"></a>  AtlInternalQueryInterface

Recupera um ponteiro para a interface solicitada.

```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>Parâmetros

*pEsse*<br/>
[in] Um ponteiro para o objeto que contém o mapa COM interfaces expostas a `QueryInterface`.

*pEntries*<br/>
[in] Uma matriz de `_ATL_INTMAP_ENTRY` estruturas que acessam um mapa das interfaces disponíveis.

*IID*<br/>
[in] O GUID da interface que está sendo solicitado.

*ppvObject*<br/>
[out] Um ponteiro para o ponteiro de interface especificado na *iid*, ou nulo se a interface não foi encontrada.

### <a name="return-value"></a>Valor de retorno

Um dos valores HRESULT padrão.

### <a name="remarks"></a>Comentários

`AtlInternalQueryInterface` somente lida com interfaces na tabela de mapa COM. Se o objeto for agregado, `AtlInternalQueryInterface` não delegar para o externo desconhecido. Você pode inserir interfaces na tabela de mapa COM a macro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) ou uma de suas variantes.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

##  <a name="inlineisequaliunknown"></a>  InlineIsEqualIUnknown

Chame essa função, para o caso especial de teste para `IUnknown`.

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>Parâmetros

*rguid1*<br/>
[in] O GUID a ser comparado com `IID_IUnknown`.

## <a name="see-also"></a>Consulte também

[Funções](../../atl/reference/atl-functions.md)<br/>
[Macros de mapa COM](../../atl/reference/com-map-macros.md)
