---
title: Estrutura scheduler_ptr
ms.date: 11/04/2016
f1_keywords:
- scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::scheduler_ptr
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::get
- PPLINTERFACE/concurrency::scheduler_ptr::scheduler_ptr::operator bool
ms.assetid: e88c84af-c306-476d-aef1-f42a0fa0a80f
ms.openlocfilehash: 2373fe3bc8cac501d1b6b32ca66996eff47ba6f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180727"
---
# <a name="schedulerptr-structure"></a>Estrutura scheduler_ptr

Representa um ponteiro para um agendador. Esta classe existe para permitir a especificação de um tempo de vida compartilhado usando o shared_ptr ou apenas uma referência simples usando o ponteiro bruto.

## <a name="syntax"></a>Sintaxe

```
struct scheduler_ptr;
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[scheduler_ptr::scheduler_ptr](#ctor)|Sobrecarregado. Cria um ponteiro de Agendador de shared_ptr para Agendador|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[scheduler_ptr::get](#get)|Retorna o ponteiro bruto ao Agendador|

### <a name="public-operators"></a>Operadores públicos

|Nome|Descrição|
|----------|-----------------|
|[scheduler_ptr::operator bool](#operator_bool)|Testar se o ponteiro de Agendador é não nulo|
|[scheduler_ptr::operator-&gt;](#operator_ptr)|Atua como um ponteiro|

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`scheduler_ptr`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** pplinterface. h

**Namespace:** simultaneidade

##  <a name="get"></a>  scheduler_ptr:: Get método

Retorna o ponteiro bruto ao Agendador.

```
scheduler_interface* get() const;
```

### <a name="return-value"></a>Valor de retorno

##  <a name="operator_bool"></a>  scheduler_ptr::operator bool

Testa se o ponteiro de Agendador é não nulo.

```
operator bool() const;
```

##  <a name="operator_ptr"></a>  scheduler_ptr::operator-&gt;

Se comporta como um ponteiro.

```
scheduler_interface* operator->() const;
```

### <a name="return-value"></a>Valor de retorno

##  <a name="ctor"></a>  scheduler_ptr:: scheduler_ptr construtor

Cria um ponteiro de Agendador de shared_ptr para Agendador.

```
explicit scheduler_ptr(std::shared_ptr<scheduler_interface> scheduler);
explicit scheduler_ptr(_In_opt_ scheduler_interface* pScheduler);
```

### <a name="parameters"></a>Parâmetros

*scheduler*<br/>
O Agendador para converter.

*pScheduler*<br/>
O ponteiro de Agendador para converter.

## <a name="see-also"></a>Consulte também

[Namespace de simultaneidade](concurrency-namespace.md)
