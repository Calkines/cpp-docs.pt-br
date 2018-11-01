---
title: Namespaces e visibilidade do tipo (C++/CX)
ms.date: 12/30/2016
ms.assetid: cbc01a3a-3b69-4ded-9c42-ecbf0fd0a00e
ms.openlocfilehash: e9efc207fe0ed49fecf30366d265019e7a3ee009
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440515"
---
# <a name="namespaces-and-type-visibility-ccx-"></a>Namespaces e visibilidade do tipo (C++/CX)

Um namespace é uma construção C++ padrão para agrupamento de tipos que têm funcionalidade relacionada e para evitar colisões de nomes em bibliotecas. O sistema de tipo de tempo de execução do Windows requer que todos os tipos públicos de tempo de execução do Windows, incluindo aqueles em seu próprio código, devem ser declarados em um namespace no escopo do namespace. Os tipos públicos que são declarados no escopo global ou aninhados dentro de outra classe causarão um erro no tempo de compilação.

Um arquivo .winmd deve ter o mesmo nome do namespace raiz. Por exemplo, uma classe denominada A.B.C.MyClass poderá ser instanciada somente se for definida em um arquivo de metadados denominado A.winmd ou A.B.winmd ou A.B.C.winmd. O nome do executável não precisa coincidir com o nome do arquivo .winmd.

## <a name="type-visibility"></a>Visibilidade de tipo

Em um namespace, tipos de tempo de execução do Windows — ao contrário de tipos C++ padrão — têm acessibilidade privada ou pública. Por padrão, a acessibilidade é privada. Somente um tipo público fica visível para os metadados e, portanto, pode ser consumido de aplicativos e componentes que podem ser escritos uma linguagem que não seja a do C++. Em geral, as regras para tipos visíveis são mais restritivas que as regras para tipos não visíveis, pois os tipos visíveis não podem expor conceitos específicos do C++ que não têm suporte nas linguagens .NET ou no JavaScript.

> [!NOTE]
> Os metadados são consumidos somente em tempo de execução por linguagens .NET e pelo JavaScript. Quando um aplicativo ou componente do C++ estiver se comunicando com outro aplicativo ou componente do C++ (isso inclui componentes do Windows, que são todos escritos em C++), não será exigido nenhum consumo em tempo de execução dos metadados.

## <a name="member-accessibility-and-visibility"></a>Acessibilidade e visibilidade do membro

Em um representante, uma interface ou uma classe ref privada, nenhum membro é emitido para metadados, mesmo que eles tenham acessibilidade pública. Em classes ref públicas, você pode controlar a visibilidade de membros nos metadados, independentemente da acessibilidade no seu código-fonte. Como no C++ padrão, aplique o princípio do privilégio mínimo; não torne seus membros visíveis nos metadados, a menos que definitivamente devam estar.

Use os modificadores de acesso a seguir para controlar a visibilidade dos metadados e a acessibilidade do código-fonte.

||||
|-|-|-|
|Modificador|Significado|Emitido para metadados?|
|particulares|A acessibilidade padrão. Mesmo significado que em C++ padrão.|Não|
|protegidos|Mesmo significado que em C++ padrão, dentro do aplicativo ou componente e nos metadados.|Sim|
|públicos|Mesmo significado que em C++ padrão.|Sim|
|`public protected` - ou - `protected public`|Acessibilidade protegida nos metadados, público no aplicativo ou componente.|Sim|
|`protected private` ou `private protected`|Não visível nos metadados; acessibilidade protegida no aplicativo ou componente.||
|`internal` ou `private public`|O membro é público no aplicativo ou componente, mas não é visível nos metadados.|Não|

## <a name="windows-runtime-namespaces"></a>Namespaces de tempo de execução do Windows

A API do Windows consiste em tipos que são declarados no Windows::\* namespaces. Esses namespaces são reservados para Windows e os tipos não podem ser adicionados a eles. No **Pesquisador de Objetos**, você pode exibir esses namespaces no arquivo windows.winmd. Para obter a documentação sobre esses namespaces, veja [API do Windows](https://msdn.microsoft.com/library/windows/apps/br211377).

## <a name="ccx-namespaces"></a>namespaces C++/CX

O C + + c++ /CLI CX definir certos tipos nesses namespaces como parte da projeção do sistema de tipo de tempo de execução do Windows.

|||
|-|-|
|**Namespace**|**Descrição**|
|default|Contém tipos numéricos e char16 internos. Esses tipos estão no escopo em cada namespace e uma instrução `using` nunca é necessária.|
|Plataforma|Contém tipos principalmente públicos que correspondem aos tipos de tempo de execução do Windows, como `Array<T>`, `String`, `Guid`, e `Boolean`. Também inclui tipos auxiliares especializados, como `Platform::Agile<T>` e `Platform::Box<T>`.|
|Platform::Collections|Contém as classes de coleção concretos que implementam as interfaces de coleção de tempo de execução do Windows `IVector`, `IMap`e assim por diante. Esses tipos são definidos em um arquivo de cabeçalho, collection.h, não em platform.winmd.|
|Platform::Details|Contém tipos que são usados pelo compilador e não devem ser usados para consumo público.|

## <a name="see-also"></a>Consulte também

[Sistema de tipos (C++/CX)](../cppcx/type-system-c-cx.md)