---
title: Usando IDispEventSimpleImpl (ATL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- IDispEventSimpleImpl
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class, using
ms.assetid: 8640ad1a-4bd0-40a5-b5e4-7322685d7aab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 635edd00fbb7126b9d4d87615321387867b2978c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063192"
---
# <a name="using-idispeventsimpleimpl"></a>Usando IDispEventSimpleImpl

Ao usar `IDispEventSimpleImpl` para manipular eventos, você precisará:

- Derive sua classe de [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md).

- Adicione um mapa de coletor de eventos à sua classe.

- Definir [atl_func_info](../atl/reference/atl-func-info-structure.md) estruturas que descrevem os eventos.

- Adicionar entradas para o mapa de coletor de eventos usando o [SINK_ENTRY_INFO](reference/composite-control-macros.md#sink_entry_info) macro.

- Implemente os métodos que você está interessado em tratamento.

- Avisar e não recomendar a origem do evento.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como lidar com o `DocumentChange` eventos acionados por do Word **aplicativo** objeto. Esse evento é definido como um método no `ApplicationEvents` dispinterface.

O exemplo é do [ATLEventHandling exemplo](../visual-cpp-samples.md).

```cpp
[ uuid(000209F7-0000-0000-C000-000000000046), hidden ]
dispinterface ApplicationEvents {
properties:
methods:
    [id(0x00000001), restricted, hidden]
    void Startup();

    [id(0x00000002)]
    void Quit();

    [id(0x00000003)]
    void DocumentChange();
};
```

O exemplo usa `#import` para gerar os arquivos de cabeçalho necessários da biblioteca de tipos do Word. Se você quiser usar este exemplo com outras versões do Word, você deve especificar o arquivo de dll do mso correto. Por exemplo, o Office 2000 fornece Mso9 e OfficeXP fornece Mso. dll. Esse código é simplificado do Stdafx. h:

[!code-cpp[NVC_ATL_EventHandlingSample#1](../atl/codesnippet/cpp/using-idispeventsimpleimpl_1.h)]

As únicas informações da biblioteca de tipos, na verdade, usada neste exemplo é o CLSID da palavra `Application` objeto e o IID do `ApplicationEvents` interface. Essas informações são usadas somente em tempo de compilação.

O código a seguir aparece no Simple.h. O código relevante é indicado por comentários:

[!code-cpp[NVC_ATL_EventHandlingSample#3](../atl/codesnippet/cpp/using-idispeventsimpleimpl_2.h)]

O código a seguir é de Simple.cpp:

[!code-cpp[NVC_ATL_EventHandlingSample#4](../atl/codesnippet/cpp/using-idispeventsimpleimpl_3.cpp)]

## <a name="see-also"></a>Consulte também

[Manipulação de eventos](../atl/event-handling-and-atl.md)<br/>
[Exemplo de ATLEventHandling](../visual-cpp-samples.md)

