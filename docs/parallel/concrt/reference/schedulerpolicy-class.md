---
title: Classe SchedulerPolicy
ms.date: 11/04/2016
f1_keywords:
- SchedulerPolicy
- concrt/concurrency::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::GetPolicyValue
- concrt/concurrency::SchedulerPolicy::SetConcurrencyLimits
- concrt/concurrency::SchedulerPolicy::SetPolicyValue
helpviewer_keywords:
- SchedulerPolicy class
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
ms.openlocfilehash: 0d1c28501abc86d09b683b0ed91f831fe8697306
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462045"
---
# <a name="schedulerpolicy-class"></a>Classe SchedulerPolicy

O `SchedulerPolicy` classe contém um conjunto de pares chave/valor, uma para cada elemento de diretiva que controlam o comportamento de uma instância do Agendador.

## <a name="syntax"></a>Sintaxe

```
class SchedulerPolicy;
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|[SchedulerPolicy](#ctor)|Sobrecarregado. Constrói uma nova política de agendador e o preenche com valores para [chaves de política](concurrency-namespace-enums.md) agendadores de tempo de execução de simultaneidade e o Gerenciador de recursos de suporte.|
|[~ Destruidor SchedulerPolicy](#dtor)|Destrói uma política de Agendador.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[GetPolicyValue](#getpolicyvalue)|Recupera o valor da chave de política fornecida como o `key` parâmetro.|
|[SetConcurrencyLimits](#setconcurrencylimits)|Define simultaneamente as `MinConcurrency` e `MaxConcurrency` diretivas no `SchedulerPolicy` objeto.|
|[SetPolicyValue](#setpolicyvalue)|Define o valor da chave de política fornecida como o `key` parâmetro e retorna o valor antigo.|

### <a name="public-operators"></a>Operadores públicos

|Nome|Descrição|
|----------|-----------------|
|[operator=](#operator_eq)|Atribui a política de Agendador de outra política de Agendador.|

## <a name="remarks"></a>Comentários

Para obter mais informações sobre as políticas que podem ser controladas usando o `SchedulerPolicy` classe, consulte [PolicyElementKey](concurrency-namespace-enums.md).

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

`SchedulerPolicy`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** concrt. h, concrtrm. h

**Namespace:** simultaneidade

##  <a name="getpolicyvalue"></a> GetPolicyValue

Recupera o valor da chave de política fornecida como o `key` parâmetro.

```
unsigned int GetPolicyValue(PolicyElementKey key) const;
```

### <a name="parameters"></a>Parâmetros

*key*<br/>
A chave de política para recuperar um valor para.

### <a name="return-value"></a>Valor de retorno

Se a chave especificada o `key` parâmetro é suportado, o valor de política para a chave de conversão para um `unsigned int`.

### <a name="remarks"></a>Comentários

O método gerará [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) para uma chave de política inválida.

##  <a name="operator_eq"></a> operador =

Atribui a política de Agendador de outra política de Agendador.

```
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```

### <a name="parameters"></a>Parâmetros

*_RhsPolicy*<br/>
A política para atribuir a esta política.

### <a name="return-value"></a>Valor de retorno

Uma referência à política de Agendador.

### <a name="remarks"></a>Comentários

Muitas vezes, a maneira mais conveniente para definir uma nova política de Agendador é copiar uma política existente e modificá-la usando o `SetPolicyValue` ou `SetConcurrencyLimits` métodos.

##  <a name="ctor"></a> SchedulerPolicy

Constrói uma nova política de agendador e o preenche com valores para [chaves de política](concurrency-namespace-enums.md) agendadores de tempo de execução de simultaneidade e o Gerenciador de recursos de suporte.

```
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```

### <a name="parameters"></a>Parâmetros

*_PolicyKeyCount*<br/>
O número de chave/valor pares que seguem o `_PolicyKeyCount` parâmetro.

*_SrcPolicy*<br/>
A política de origem para copiar.

### <a name="remarks"></a>Comentários

O primeiro construtor cria uma nova política de Agendador onde todas as políticas serão inicializadas com seus valores padrão.

O segundo construtor cria uma nova política de agendador que usa um estilo de parâmetro nomeado da inicialização. Valores depois o `_PolicyKeyCount` parâmetro são fornecidos como pares chave/valor. Qualquer chave de política que não é especificada nesse construtor terá seu valor padrão. Esse construtor pode lançar exceções [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md), [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) ou [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md).

O terceiro construtor é um construtor de cópia. Muitas vezes, a maneira mais conveniente para definir uma nova política de Agendador é copiar uma política existente e modificá-la usando o `SetPolicyValue` ou `SetConcurrencyLimits` métodos.

##  <a name="dtor"></a> ~ SchedulerPolicy

Destrói uma política de Agendador.

```
~SchedulerPolicy();
```

##  <a name="setconcurrencylimits"></a> SetConcurrencyLimits

Define simultaneamente as `MinConcurrency` e `MaxConcurrency` diretivas no `SchedulerPolicy` objeto.

```
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```

### <a name="parameters"></a>Parâmetros

*_MinConcurrency*<br/>
O valor para o `MinConcurrency` chave de política.

*_MaxConcurrency*<br/>
O valor para o `MaxConcurrency` chave de política.

### <a name="remarks"></a>Comentários

O método gerará [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md) se o valor especificado para o `MinConcurrency` diretiva é maior do que o especificado para o `MaxConcurrency` política.

O método também pode lançar [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) outros valores inválidos.

##  <a name="setpolicyvalue"></a> SetPolicyValue

Define o valor da chave de política fornecida como o `key` parâmetro e retorna o valor antigo.

```
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```

### <a name="parameters"></a>Parâmetros

*key*<br/>
A chave de política para definir um valor.

*value*<br/>
O valor para definir a chave de política.

### <a name="return-value"></a>Valor de retorno

Se a chave especificada o `key` parâmetro é suportado, o valor antigo da política para a chave é convertido em um `unsigned int`.

### <a name="remarks"></a>Comentários

O método gerará [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) para uma chave de política inválida ou qualquer chave de política cujo valor não pode ser definido pelo `SetPolicyValue` método.

O método gerará [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) para um valor que não há suporte para a chave especificada pelo `key` parâmetro.

Observe que esse método não tem permissão para definir a `MinConcurrency` ou `MaxConcurrency` políticas. Para definir esses valores, use o [SetConcurrencyLimits](#setconcurrencylimits) método.

## <a name="see-also"></a>Consulte também

[Namespace de simultaneidade](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[Classe CurrentScheduler](currentscheduler-class.md)<br/>
[Classe Scheduler](scheduler-class.md)<br/>
[Agendador de tarefas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)

