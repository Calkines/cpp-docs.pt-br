---
title: Classe EventTargetArray
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
- event/Microsoft::WRL::Details::EventTargetArray::Begin
- event/Microsoft::WRL::Details::EventTargetArray::End
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
- event/Microsoft::WRL::Details::EventTargetArray::Length
- event/Microsoft::WRL::Details::EventTargetArray::~EventTargetArray
helpviewer_keywords:
- Microsoft::WRL::Details::EventTargetArray class
- Microsoft::WRL::Details::EventTargetArray::AddTail method
- Microsoft::WRL::Details::EventTargetArray::Begin method
- Microsoft::WRL::Details::EventTargetArray::End method
- Microsoft::WRL::Details::EventTargetArray::EventTargetArray, constructor
- Microsoft::WRL::Details::EventTargetArray::Length method
- Microsoft::WRL::Details::EventTargetArray::~EventTargetArray, destructor
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
ms.openlocfilehash: 1f3f8e299dba1f4b6ae5a5767f11989dc2fe8370
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398479"
---
# <a name="eventtargetarray-class"></a>Classe EventTargetArray

Oferece suporte a infraestrutura do WRL e não se destina a ser usado diretamente do seu código.

## <a name="syntax"></a>Sintaxe

```cpp
class EventTargetArray :
    public Microsoft::WRL::RuntimeClass<
        Microsoft::WRL::RuntimeClassFlags<ClassicCom>,
        IUnknown
    >;
```

## <a name="remarks"></a>Comentários

Representa uma matriz de manipuladores de eventos.

Os manipuladores de eventos que são associados com um [EventSource](eventsource-class.md) objeto são armazenadas em uma planilha protegida `EventTargetArray` membro de dados.

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

Nome                                                           | Descrição
-------------------------------------------------------------- | -----------------------------------------------------------
[EventTargetArray::EventTargetArray](#eventtargetarray)        | Inicializa uma nova instância da classe `EventTargetArray`.
[EventTargetArray::~EventTargetArray](#tilde-eventtargetarray) | Realiza o desligamento atual `EventTargetArray` classe.

### <a name="public-methods"></a>Métodos públicos

Nome                                  | Descrição
------------------------------------- | ---------------------------------------------------------------------------------------
[EventTargetArray::AddTail](#addtail) | Acrescenta o manipulador de eventos especificado ao final da matriz interna de manipuladores de eventos.
[EventTargetArray::Begin](#begin)     | Obtém o endereço do primeiro elemento da matriz interna de manipuladores de eventos.
[EventTargetArray::End](#end)         | Obtém o endereço do último elemento da matriz interna de manipuladores de eventos.
[EventTargetArray::Length](#length)   | Obtém o número atual de elementos na matriz interna de manipuladores de eventos.

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`EventTargetArray`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** Event. h

**Namespace:** Microsoft::WRL::Details

## <a name="tilde-eventtargetarray"></a>EventTargetArray::~EventTargetArray

Oferece suporte a infraestrutura do WRL e não se destina a ser usado diretamente do seu código.

```cpp
~EventTargetArray();
```

### <a name="remarks"></a>Comentários

Realiza o desligamento atual `EventTargetArray` classe.

## <a name="addtail"></a>EventTargetArray::AddTail

Oferece suporte a infraestrutura do WRL e não se destina a ser usado diretamente do seu código.

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>Parâmetros

*element*<br/>
Ponteiro para o manipulador de eventos para acrescentar.

### <a name="remarks"></a>Comentários

Acrescenta o manipulador de eventos especificado ao final da matriz interna de manipuladores de eventos.

`AddTail()` se destina a ser usado internamente pelo apenas o `EventSource` classe.

## <a name="begin"></a>EventTargetArray::Begin

Oferece suporte a infraestrutura do WRL e não se destina a ser usado diretamente do seu código.

```cpp
ComPtr<IUnknown>* Begin();
```

### <a name="return-value"></a>Valor de retorno

O endereço do primeiro elemento da matriz interna de manipuladores de eventos.

### <a name="remarks"></a>Comentários

Obtém o endereço do primeiro elemento da matriz interna de manipuladores de eventos.

## <a name="end"></a>EventTargetArray::End

Oferece suporte a infraestrutura do WRL e não se destina a ser usado diretamente do seu código.

```cpp
ComPtr<IUnknown>* End();
```

### <a name="return-value"></a>Valor de retorno

O endereço do último elemento da matriz interna de manipuladores de eventos.

### <a name="remarks"></a>Comentários

Obtém o endereço do último elemento da matriz interna de manipuladores de eventos.

## <a name="eventtargetarray"></a>EventTargetArray::EventTargetArray

Oferece suporte a infraestrutura do WRL e não se destina a ser usado diretamente do seu código.

```cpp
EventTargetArray(
   _Out_ HRESULT* hr,
   size_t items
);
```

### <a name="parameters"></a>Parâmetros

*hr*<br/>
Depois de operações esse construtor, parâmetro *hr* indica se a alocação da matriz foi bem-sucedida ou falhou. A lista a seguir mostra os possíveis valores para *hr*.

+   S_OK<br/>
    A operação foi bem-sucedida.

+   E_OUTOFMEMORY<br/>
    Não foi possível alocar memória para a matriz.

+   S_FALSE<br/>
    Parâmetro *itens* é menor ou igual a zero.

*items*<br/>
O número de elementos da matriz para alocar.

### <a name="remarks"></a>Comentários

Inicializa uma nova instância da classe `EventTargetArray`.

`EventTargetArray` é usado para manter uma matriz de manipuladores de eventos em um `EventSource` objeto.

## <a name="length"></a>EventTargetArray::Length

Oferece suporte a infraestrutura do WRL e não se destina a ser usado diretamente do seu código.

```cpp
size_t Length();
```

### <a name="return-value"></a>Valor de retorno

O número atual de elementos na matriz interna de manipuladores de eventos.

### <a name="remarks"></a>Comentários

Obtém o número atual de elementos na matriz interna de manipuladores de eventos.
