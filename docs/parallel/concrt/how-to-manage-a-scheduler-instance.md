---
title: 'Como: Gerenciar uma instância do Agendador'
ms.date: 11/04/2016
helpviewer_keywords:
- managing a scheduler instance [Concurrency Runtime]
- scheduler instances, managing [Concurrency Runtime]
ms.assetid: 2cc804f0-5ff3-498b-97f1-a9f67a005448
ms.openlocfilehash: f402e82a18f7b804f2c25ebf0a4392d19694d25c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510533"
---
# <a name="how-to-manage-a-scheduler-instance"></a>Como: Gerenciar uma instância do Agendador

As instâncias do Agendador permitem associar políticas de agendamento específicas com vários tipos de cargas de trabalho. Este tópico contém dois exemplos básicos que mostram como criar e gerenciar uma instância do Agendador.

Os exemplos criam agendadores que usam as políticas padrão do Agendador. Para obter um exemplo que cria um Agendador que usa uma política personalizada, [consulte Como: Especifique políticas](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)específicas do Agendador.

### <a name="to-manage-a-scheduler-instance-in-your-application"></a>Para gerenciar uma instância do agendador no aplicativo

1. Crie um objeto [Concurrency:: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) que contém os valores de política para o Agendador usar.

1. Chame o método [Concurrency:: CurrentScheduler:: Create](reference/currentscheduler-class.md#create) ou o método [Concurrency:: Scheduler:: Create](reference/scheduler-class.md#create) para criar uma instância do Agendador.

   Se você usar o `Scheduler::Create` método, chame o método [Concurrency:: Scheduler:: Attach](reference/scheduler-class.md#attach) quando precisar associar o Agendador ao contexto atual.

1. Chame a função [CreateEvent](/windows/win32/api/synchapi/nf-synchapi-createeventw) para criar um identificador para um objeto de evento de redefinição automática não sinalizado.

1. Passe o identificador para o objeto de evento que você acabou de criar ao método [Concurrency:: CurrentScheduler:: RegisterShutdownEvent](reference/currentscheduler-class.md#registershutdownevent) ou o método [Concurrency:: Scheduler:: RegisterShutdownEvent](reference/scheduler-class.md#registershutdownevent) . Isso registra o evento a ser definido quando o Agendador é destruído.

1. Execute as tarefas que você deseja que o Agendador atual agende.

1. Chame o método [Concurrency:: CurrentScheduler::D Etach](reference/currentscheduler-class.md#detach) para desanexar o Agendador atual e restaurar o Agendador anterior como o atual.

   Se você usar o `Scheduler::Create` método, chame o método [Concurrency:: Scheduler:: Release](reference/scheduler-class.md#release) para diminuir a contagem de `Scheduler` referência do objeto.

1. Passe o identificador para o evento para a função [WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) para aguardar o desligamento do Agendador.

1. Chame a função [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) para fechar o identificador para o objeto de evento.

## <a name="example"></a>Exemplo

O código a seguir mostra duas maneiras de gerenciar uma instância do Agendador. Cada exemplo usa primeiro o agendador padrão para executar uma tarefa que imprime o identificador exclusivo do Agendador atual. Cada exemplo usa uma instância do Agendador para executar a mesma tarefa novamente. Por fim, cada exemplo restaura o agendador padrão como o atual e executa a tarefa mais uma vez.

O primeiro exemplo usa a classe [Concurrency:: CurrentScheduler](../../parallel/concrt/reference/currentscheduler-class.md) para criar uma instância do Agendador e associá-la ao contexto atual. O segundo exemplo usa a classe [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) para executar a mesma tarefa. Normalmente, a `CurrentScheduler` classe é usada para trabalhar com o Agendador atual. O segundo exemplo, que usa a `Scheduler` classe, é útil quando você deseja controlar quando o Agendador está associado ao contexto atual ou quando você deseja associar agendadores específicos a tarefas específicas.

[!code-cpp[concrt-scheduler-instance#1](../../parallel/concrt/codesnippet/cpp/how-to-manage-a-scheduler-instance_1.cpp)]

Este exemplo gerencia a seguinte saída.

```Output
Using CurrentScheduler class...

Current scheduler id: 0
Creating and attaching scheduler...
Current scheduler id: 1
Detaching scheduler...
Current scheduler id: 0

Using Scheduler class...

Current scheduler id: 0
Creating scheduler...
Attaching scheduler...
Current scheduler id: 2
Detaching scheduler...
Current scheduler id: 0
```

## <a name="compiling-the-code"></a>Compilando o código

Copie o código de exemplo e cole-o em um projeto do Visual Studio ou cole-o em um arquivo `scheduler-instance.cpp` chamado e, em seguida, execute o comando a seguir em uma janela de prompt de comando do Visual Studio.

**CL. exe/EHsc Scheduler-instance. cpp**

## <a name="see-also"></a>Consulte também

[Instâncias de agendador](../../parallel/concrt/scheduler-instances.md)<br/>
[Como: Especificar políticas específicas do agendador](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)
