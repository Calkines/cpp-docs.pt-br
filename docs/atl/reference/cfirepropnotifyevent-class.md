---
title: Classe CFirePropNotifyEvent
ms.date: 11/04/2016
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
ms.openlocfilehash: 694127ceccc1d1b55e5da9abca799dff77dcfc60
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496946"
---
# <a name="cfirepropnotifyevent-class"></a>Classe CFirePropNotifyEvent

Essa classe fornece métodos para notificar o coletor do contêiner sobre as alterações de propriedade de controle.

> [!IMPORTANT]
>  Essa classe e seus membros não podem ser usados em aplicativos que são executados no Windows Runtime.

## <a name="syntax"></a>Sintaxe

```
class CFirePropNotifyEvent
```

## <a name="members"></a>Membros

### <a name="public-methods"></a>Métodos Públicos

|Nome|Descrição|
|----------|-----------------|
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|Auto-estática Notifica o coletor do contêiner de que uma propriedade de controle foi alterada.|
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|Auto-estática Notifica o coletor do contêiner que uma propriedade de controle está prestes a ser alterada.|

## <a name="remarks"></a>Comentários

`CFirePropNotifyEvent`tem dois métodos que notificam o coletor do contêiner de que uma propriedade de controle foi alterada ou está prestes a ser alterada.

Se a classe que implementa seu controle for derivada `IPropertyNotifySink`de, `CFirePropNotifyEvent` os métodos serão invocados quando `FireOnRequestEdit` você `FireOnChanged`chamar ou. Se a classe de controle não for derivada `IPropertyNotifySink`de, as chamadas para essas funções retornam S_OK.

Para obter mais informações sobre como criar controles, consulte o [tutorial do ATL](../../atl/active-template-library-atl-tutorial.md).

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atlctl. h

##  <a name="fireonchanged"></a>  CFirePropNotifyEvent::FireOnChanged

Notifica todas as interfaces de [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) conectadas (em cada ponto de conexão do objeto) que a propriedade de objeto especificada alterou.

```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parâmetros

*pUnk*<br/>
no Ponteiro para o `IUnknown` do objeto que envia a notificação.

*dispID*<br/>
no Identificador da propriedade que foi alterada.

### <a name="return-value"></a>Valor de retorno

Um dos valores de HRESULT padrão.

### <a name="remarks"></a>Comentários

Essa função é segura para chamar mesmo que o controle não dê suporte a pontos de conexão.

##  <a name="fireonrequestedit"></a>  CFirePropNotifyEvent::FireOnRequestEdit

Notifica todas as interfaces de [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) conectadas (em cada ponto de conexão do objeto) que a propriedade de objeto especificada está prestes a ser alterada.

```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```

### <a name="parameters"></a>Parâmetros

*pUnk*<br/>
no Ponteiro para o `IUnknown` do objeto que envia a notificação.

*dispID*<br/>
no Identificador da propriedade prestes a ser alterado.

### <a name="return-value"></a>Valor de retorno

Um dos valores de HRESULT padrão.

### <a name="remarks"></a>Comentários

Essa função é segura para chamar mesmo que o controle não dê suporte a pontos de conexão.

## <a name="see-also"></a>Consulte também

[Visão geral da classe](../../atl/atl-class-overview.md)
