---
title: Funções globais de ponto de Conexão
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
ms.openlocfilehash: 0313e93ee82bb96f3bfe08e45f70ccfee30dbee6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62278262"
---
# <a name="connection-point-global-functions"></a>Funções globais de ponto de Conexão

Essas funções dão suporte a pontos de conexão e mapas de coletor.

> [!IMPORTANT]
>  As funções listadas na tabela a seguir não podem ser usadas em aplicativos executados no tempo de execução do Windows.

|||
|-|-|
|[AtlAdvise](#atladvise)|Cria uma conexão entre o ponto de conexão de um objeto e o coletor de um cliente.|
|[AtlUnadvise](#atlunadvise)|Encerra a conexão estabelecida por meio de `AtlAdvise`.|
|[AtlAdviseSinkMap](#atladvisesinkmap)|Aconselha ou unadvises entradas em um mapa coletor de evento.|

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atlbase. h

##  <a name="atladvise"></a>  AtlAdvise

Cria uma conexão entre o ponto de conexão de um objeto e o coletor de um cliente.

> [!IMPORTANT]
>  Essa função não pode ser usada em aplicativos executados no tempo de execução do Windows.

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>Parâmetros

*pUnkCP*<br/>
[in] Um ponteiro para o `IUnknown` do objeto cliente deseja se conectar com.

*pUnk*<br/>
[in] Um ponteiro para o cliente `IUnknown`.

*iid*<br/>
[in] O GUID do ponto de conexão. Normalmente, isso é o mesmo que a interface de saída gerenciada pelo ponto de conexão.

*pdw*<br/>
[out] Um ponteiro para o cookie que identifica exclusivamente a conexão.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

O coletor implementa a interface de saída com suporte pelo ponto de conexão. O cliente usa o *pdw* cookie para remover a conexão, passando-o para [AtlUnadvise](#atlunadvise).

### <a name="example"></a>Exemplo

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

##  <a name="atlunadvise"></a>  AtlUnadvise

Encerra a conexão estabelecida por meio [AtlAdvise](#atladvise).

> [!IMPORTANT]
>  Essa função não pode ser usada em aplicativos executados no tempo de execução do Windows.

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>Parâmetros

*pUnkCP*<br/>
[in] Um ponteiro para o `IUnknown` do objeto que o cliente está conectado com.

*iid*<br/>
[in] O GUID do ponto de conexão. Normalmente, isso é o mesmo que a interface de saída gerenciada pelo ponto de conexão.

*dw*<br/>
[in] O cookie que identifica exclusivamente a conexão.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

##  <a name="atladvisesinkmap"></a>  AtlAdviseSinkMap

Chame essa função para recomendar ou não recomendar todas as entradas no mapa de eventos do coletor do objeto.

> [!IMPORTANT]
>  Essa função não pode ser usada em aplicativos executados no tempo de execução do Windows.

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>Parâmetros

*pT*<br/>
[in] Um ponteiro para o objeto que contém o mapa de coletor.

*bAdvise*<br/>
[in] TRUE se todas as entradas de coletor devem ser avisado; FALSE se todas as entradas de coletor devem ser unadvised.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>Consulte também

[Funções](../../atl/reference/atl-functions.md)<br/>
[Macros de ponto de conexão](../../atl/reference/connection-point-macros.md)
