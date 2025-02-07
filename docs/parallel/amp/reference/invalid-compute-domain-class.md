---
title: Classe invalid_compute_domain
ms.date: 11/04/2016
f1_keywords:
- invalid_compute_domain
- AMPRT/invalid_compute_domain
- AMPRT/Concurrency::invalid_compute_domain::invalid_compute_domain
helpviewer_keywords:
- invalid_compute_domain class
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
ms.openlocfilehash: 51fcd9e42bc4497131da5adb3dff72efb46537b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351713"
---
# <a name="invalidcomputedomain-class"></a>Classe invalid_compute_domain

A exceção que é lançada quando o tempo de execução não pode iniciar um kernel usando o domínio de cálculo especificado na [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each) site de chamada.

## <a name="syntax"></a>Sintaxe

```
class invalid_compute_domain : public runtime_exception;
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[Construtor de invalid_compute_domain](#ctor)|Inicializa uma nova instância da classe `invalid_compute_domain`.|

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`exception`

`runtime_exception`

`invalid_compute_domain`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** amprt. h

**Namespace:** Concorrência

## <a name="ctor"></a> invalid_compute_domain

Inicializa uma nova instância da classe.

## <a name="syntax"></a>Sintaxe

```
explicit invalid_compute_domain(
    const char * _Message ) throw();

invalid_compute_domain() throw();
```

### <a name="parameters"></a>Parâmetros

*_Message*<br/>
Uma descrição do erro.

### <a name="return-value"></a>Valor de retorno

Uma instância da `invalid_compute_domain` classe

## <a name="see-also"></a>Consulte também

[Namespace de simultaneidade (C++ AMP)](concurrency-namespace-cpp-amp.md)
