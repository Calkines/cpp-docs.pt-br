---
title: APIs de chave WRL por categoria
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7367bacf-6b7c-4ecd-a0ce-a662db46fc66
ms.openlocfilehash: f3065323c567c944dab12fc1ebbcbd6bb57127e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223138"
---
# <a name="key-wrl-apis-by-category"></a>APIs de chave WRL por categoria

As tabelas a seguir listam os principais produtos de classes, structs, funções e macros biblioteca de modelos de C++ de tempo de execução do Windows. Construtores em classes e namespaces de auxiliar são omitidos. Essas listas ampliar a documentação de API, que é organizada por namespace.

## <a name="classes"></a>Classes

|Título|Descrição|
|-----------|-----------------|
|[Classe ActivationFactory](activationfactory-class.md)|Permite que um ou mais classes sejam ativadas pelo tempo de execução do Windows.|
|[Classe AsyncBase](asyncbase-class.md)|Implementa a máquina de estado assíncrona do tempo de execução do Windows.|
|[Classe ClassFactory](classfactory-class.md)|Implementa a funcionalidade básica do `IClassFactory` interface.|
|[Classe ComPtr](comptr-class.md)|Cria uma *ponteiro inteligente* tipo que representa a interface especificada pelo parâmetro de modelo. ComPtr automaticamente mantém uma contagem de referência para o ponteiro de interface subjacente e libera a interface quando a contagem de referência chega a zero.|
|[Classe Event (Biblioteca de Modelos C++ do Tempo de Execução do Windows)](event-class-wrl.md)|Representa um evento.|
|[Classe EventSource](eventsource-class.md)|Representa um evento. `EventSource` funções de membro, adicionar, remover e invocar manipuladores de eventos.|
|[Classe FtmBase](ftmbase-class.md)|Representa um objeto livre de marshaler.|
|[Classe HandleT](handlet-class.md)|Representa um identificador para um objeto.|
|[Classe HString](hstring-class.md)|Fornece suporte para manipular identificadores de HSTRING.|
|[Classe HStringReference](hstringreference-class.md)|Representa um HSTRING que é criado a partir de uma cadeia de caracteres existente.|
|[Classe Module](module-class.md)|Representa uma coleção de objetos relacionados.|
|[Classe Module::GenericReleaseNotifier](module-genericreleasenotifier-class.md)|Invoca um manipulador de eventos quando o último objeto no módulo atual é liberado. O manipulador de eventos é especificado em um lambda, functor ou ponteiro para função.|
|[Classe Module::MethodReleaseNotifier](module-methodreleasenotifier-class.md)|Invoca um manipulador de eventos quando o último objeto no módulo atual é liberado. O manipulador de eventos é especificado por um objeto e seu membro de ponteiro ao método.|
|[Classe Module::ReleaseNotifier](module-releasenotifier-class.md)|Invoca um manipulador de eventos quando o último objeto em um módulo é liberado.|
|[Classe RoInitializeWrapper](roinitializewrapper-class.md)|Inicializa o tempo de execução do Windows.|
|[Classe RuntimeClass](runtimeclass-class.md)|Representa uma classe instanciada que herda o número especificado de interfaces e fornece o tempo de execução do Windows especificado, COM clássico e suporte fraco de referência.|
|[Classe SimpleActivationFactory](simpleactivationfactory-class.md)|Fornece um mecanismo fundamental para criar um tempo de execução do Windows ou a classe base do COM clássico.|
|[Classe SimpleClassFactory](simpleclassfactory-class.md)|Fornece um mecanismo fundamental para criar uma classe base.|
|[Classe WeakRef](weakref-class.md)|Representa uma *referência fraca* que pode ser usado pelo apenas Windows Runtime, com clássico não. Uma referência fraca representa um objeto que pode ou não ser acessível.|

## <a name="structures"></a>Estruturas

|Título|Descrição|
|-----------|-----------------|
|[Estrutura ChainInterfaces](chaininterfaces-structure.md)|Especifica as funções de verificação e de inicialização que podem ser aplicadas a um conjunto de IDs de interface.|
|[Estrutura CloakedIid](cloakediid-structure.md)|Indica para o `RuntimeClass`, `Implements` e `ChainInterfaces` que a interface especificada não está acessível na lista de IID de modelos.|
|[Estrutura Implements](implements-structure.md)|Implementa `QueryInterface` e `GetIid` para interfaces especificadas.|
|[Estrutura MixIn](mixin-structure.md)|Garante que uma classe de tempo de execução deriva de interfaces do COM clássico, em seguida e as interfaces de tempo de execução do Windows, se houver.|

## <a name="functions"></a>Funções

|Título|Descrição|
|-----------|-----------------|
|[Função ActivateInstance](activateinstance-function.md)|Registra e recupera uma instância de um tipo especificado definido em uma ID de classe especificado.|
|[Função AsWeak](asweak-function.md)|Recupera uma referência fraca a uma instância especificada.|
|[Função de retorno de chamada](callback-function-wrl.md)|Cria um objeto cuja função de membro é um método de retorno de chamada.|
|[Função CreateActivationFactory](createactivationfactory-function.md)|Cria uma fábrica que produz instâncias da classe especificada que pode ser ativado pelo tempo de execução do Windows.|
|[Função CreateClassFactory](createclassfactory-function.md)|Cria uma fábrica que produz instâncias da classe especificada.|
|[Função GetActivationFactory](getactivationfactory-function.md)|Recupera um alocador de ativação para o tipo especificado pelo parâmetro de modelo.|
|[Função Make](make-function.md)|Inicializa a classe de tempo de execução do Windows especificada.|

## <a name="macros"></a>Macros

|Título|Descrição|
|-----------|-----------------|
|[ActivatableClass Macros](activatableclass-macros.md)|Popula um cache interno que contém uma fábrica que pode criar uma instância da classe especificada.|
|[Macro InspectableClass](inspectableclass-macro.md)|Define o nível de confiança e o nome de classe do tempo de execução.|

## <a name="see-also"></a>Consulte também

[WRL (Biblioteca de Modelos C++ do Tempo de Execução do Windows)](windows-runtime-cpp-template-library-wrl.md)