---
title: Estrutura IUMSScheduler
ms.date: 11/04/2016
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
ms.openlocfilehash: f377d6079017266630434ce71602a7e70e58ae21
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301858"
---
# <a name="iumsscheduler-structure"></a>Estrutura IUMSScheduler

Uma interface para uma abstração de um agendador de trabalho que deseja o Gerenciador de recursos do tempo de execução de simultaneidade entregá-lo a threads agendáveis no modo de usuário (UMS). O Gerenciador de recursos usa essa interface para se comunicar com os agendadores de thread UMS. A interface `IUMSScheduler` herda da interface `IScheduler` .

## <a name="syntax"></a>Sintaxe

```
struct IUMSScheduler : public IScheduler;
```

## <a name="members"></a>Membros

### <a name="public-methods"></a>Métodos Públicos

|Nome|Descrição|
|----------|-----------------|
|[IUMSScheduler::SetCompletionList](#setcompletionlist)|Atribui um `IUMSCompletionList` interface para um agendador de thread UMS.|

## <a name="remarks"></a>Comentários

Se você estiver implementando um agendador personalizado que se comunica com o Gerenciador de recursos, e você desejar threads UMS a serem passadas para o Agendador em vez de threads de Win32 comuns, você deve fornecer uma implementação do `IUMSScheduler` interface. Além disso, você deve definir o valor da política para a chave de política de Agendador `SchedulerKind` ser `UmsThreadDefault`. Se a diretiva especifica thread UMS, o `IScheduler` interface que é passado como um parâmetro para o [iresourcemanager:: Registerscheduler](iresourcemanager-structure.md#registerscheduler) método deve ser um `IUMSScheduler` interface.

O Gerenciador de recursos é capaz de entregar threads UMS apenas em sistemas operacionais que têm o recurso UMS. sistemas operacionais de 64 bits com a versão do Windows 7 e posteriores dão suporte a threads UMS. Se você criar uma política de Agendador com o `SchedulerKind` chave definida como o valor `UmsThreadDefault` e a plataforma subjacente não oferece suporte a UMS, o valor da `SchedulerKind` chave nessa diretiva será alterado para o valor `ThreadScheduler`. Você deve sempre ler novamente esse valor de política antes que espera receber threads UMS.

O `IUMSScheduler` interface é uma extremidade de um canal bidirecional de comunicação entre um agendador e o Gerenciador de recursos. A outra extremidade é representada pela `IResourceManager` e `ISchedulerProxy` interfaces, que são implementados pelo Gerenciador de recursos.

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[IScheduler](ischeduler-structure.md)

`IUMSScheduler`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** concrtrm. h

**Namespace:** simultaneidade

##  <a name="setcompletionlist"></a>  Método iumsscheduler:: Setcompletionlist

Atribui um `IUMSCompletionList` interface para um agendador de thread UMS.

```
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```

### <a name="parameters"></a>Parâmetros

*pCompletionList*<br/>
A interface de lista de conclusão para o Agendador. Há uma única lista por Agendador.

### <a name="remarks"></a>Comentários

O Gerenciador de recursos será invocar esse método em um agendador que especifica que ele deseja threads UMS, depois que o Agendador solicitou uma alocação inicial de recursos. O Agendador pode usar o `IUMSCompletionList` interface para determinar quando os proxies de thread UMS tiveram desbloqueado. Ele é válido somente para acessar essa interface de um proxy de thread em execução em uma raiz de processador virtual atribuída ao Agendador UMS.

## <a name="see-also"></a>Consulte também

[Namespace de simultaneidade](concurrency-namespace.md)<br/>
[PolicyElementKey](concurrency-namespace-enums.md)<br/>
[Estrutura IScheduler](ischeduler-structure.md)<br/>
[Estrutura IUMSCompletionList](iumscompletionlist-structure.md)<br/>
[Estrutura IResourceManager](iresourcemanager-structure.md)
