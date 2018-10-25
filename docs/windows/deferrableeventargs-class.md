---
title: Classe DeferrableEventArgs | Microsoft Docs
ms.custom: ''
ms.date: 10/03/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::DeferrableEventArgs
- event/Microsoft::WRL::DeferrableEventArgs::GetDeferral
- event/Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::DeferrableEventArgs class
- Microsoft::WRL::DeferrableEventArgs::GetDeferral method
- Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished method
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7f5c117d0d65f86e4f4b69011457e166b6440820
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081557"
---
# <a name="deferrableeventargs-class"></a>Classe DeferrableEventArgs

Uma classe de modelo usada para os tipos de argumento de evento para adiamentos.

## <a name="syntax"></a>Sintaxe

```cpp
template <typename TEventArgsInterface, typename TEventArgsClass>
class DeferrableEventArgs : public TEventArgsInterface;
```

### <a name="parameters"></a>Parâmetros

*TEventArgsInterface*<br/>
O tipo de interface que declara os argumentos para um evento adiado.

*TEventArgsClass*<br/>
A classe que implementa *TEventArgsInterface*.

## <a name="members"></a>Membros

### <a name="public-methods"></a>Métodos Públicos

Nome                                                         | Descrição
------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------
[Deferrableeventargs:: Getdeferral](#getdeferral)             | Obtém uma referência para o [adiamento](http://go.microsoft.com/fwlink/p/?linkid=526520) objeto que representa um evento adiado.
[Deferrableeventargs:: Invokeallfinished](#invokeallfinished) | Chamado para indicar que todo o processamento para manipular um evento adiado foi concluída.

## <a name="remarks"></a>Comentários

As instâncias dessa classe são passadas para manipuladores de eventos para eventos adiados. Os parâmetros de modelo representam uma interface que define os detalhes dos argumentos do evento para um tipo específico de evento adiado e uma classe que implementa a interface.

A classe é exibido como o primeiro argumento para um manipulador de eventos para um evento adiado. Você pode chamar o [GetDeferral](#getdeferral) método para obter o [adiamento](http://go.microsoft.com/fwlink/p/?linkid=526520) objeto do qual você pode obter todas as informações sobre o evento adiada. Depois de concluir a manipulação de eventos, você deve chamar Complete no objeto de adiamento. Em seguida, você deve chamar [InvokeAllFinished](#invokeallfinished) no final do método do manipulador de eventos, que garante que a conclusão de adiada todos os eventos é comunicada corretamente.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** Event. h

**Namespace:** Microsoft::WRL

## <a name="getdeferral"></a>Deferrableeventargs:: Getdeferral

Obtém uma referência para o [adiamento](http://go.microsoft.com/fwlink/p/?linkid=526520) objeto que representa um evento adiado.

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)
```

### <a name="parameters"></a>Parâmetros

*resultado*<br/>
Um ponteiro que fará referência a [adiamento](http://go.microsoft.com/fwlink/p/?linkid=526520) objeto quando a chamada é concluída.

### <a name="return-value"></a>Valor de retorno

S_OK se bem-sucedido; Caso contrário, um HRESULT que indica o erro.

## <a name="invokeallfinished"></a>Deferrableeventargs:: Invokeallfinished

Chamado para indicar que todo o processamento para manipular um evento adiado foi concluída.

```cpp
void InvokeAllFinished()
```

### <a name="remarks"></a>Comentários

Você deve chamar esse método após as chamadas de código-fonte do evento [InvokeAll](../windows/eventsource-invokeall-method.md). Chamar esse método impede que mais adiamentos de que está sendo feito e força a execução se nenhum adiamentos foram realizados do manipulador de conclusão.
