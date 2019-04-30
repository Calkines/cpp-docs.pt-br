---
title: Iterators
ms.date: 11/04/2016
helpviewer_keywords:
- iterator conventions
- C++ Standard Library, iterator conventions
ms.assetid: 2f746be7-b37d-4bfc-bf05-be4336ca982f
ms.openlocfilehash: 3b6713a80244d7063baac2c75ffead76fe93facc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396128"
---
# <a name="iterators"></a>Iterators

Um iterador é um objeto que pode iterar em elementos em um contêiner da Biblioteca Padrão do C++ e fornecer acesso a elementos individuais. Os contêineres da Biblioteca Padrão do C++ fornecem iteradores de modo que todos os algoritmos possam acessar seus elementos de maneira padrão sem precisar se preocupar com o tipo do contêiner em que os elementos estão armazenados.

Você pode usar iteradores explicitamente usando funções membro e globais, como `begin()` e `end()` e operadores, como **++** e **--** para mover para frente ou com versões anteriores. Você também pode usar iteradores implicitamente com um intervalo de-loop for ou (para alguns tipos de iterador) o operador subscrito  **\[]**.

Na Biblioteca Padrão do C++, o início de uma sequência ou intervalo é o primeiro elemento. O final de uma sequência ou intervalo sempre é definido como um após o último elemento. As funções globais `begin` e `end` retornam iteradores a um contêiner especificado. O loop do iterador explícito típico sobre todos os elementos em um contêiner tem esta aparência:

```cpp
vector<int> vec{ 0,1,2,3,4 };
for (auto it = begin(vec); it != end(vec); it++)
{
    // Access element using dereference operator
    cout << *it << " ";
}
```

A mesma coisa pode ser feita de forma mais simples com um intervalo range-for:

```cpp
for (auto num : vec)
{
    // no deference operator
    cout << num << " ";
}
```

Há cinco categorias de iteradores. Em ordem crescente de potência, as categorias são:

- **Saída**. Uma *iterador de saída* `X` pode iterar para frente em uma sequência usando o **++** operador e pode gravar apenas uma vez, um elemento usando o __\*__ operador.

- **Entrada**. Uma *iterador de entrada* `X` pode iterar para frente em uma sequência usando o + + operador e pode ler um elemento qualquer número de vezes usando a **&ast;** operador. Você pode comparar iteradores de entrada usando o **++** e **! =** operadores. Depois de você incrementar qualquer cópia de um iterador de entrada, nenhuma das outras cópias pode ser comparada, cancelada ou incrementada com segurança.

- **Avanço**. Um *iterador de avanço* `X` pode iterar para frente em uma sequência usando o + + operador e pode ler qualquer elemento ou gravar elementos não constantes quantas vezes desejar usando a **&ast;** operador. Você pode acessar membros do elemento usando o **->** operador e a comparação de encaminham iteradores usando o **==** e **! =** operadores. Você pode fazer várias cópias de um iterador de avanço, cada uma das quais pode ser desreferenciada e incrementada de forma independente. Um iterador de avanço inicializado sem referência a nenhum contêiner é chamada de um *iterador de avanço nulo*. Iteradores de avanço nulos sempre são comparados como iguais.

- **Bidirecional**. Um *iterador bidirecional* `X` pode tomar o lugar de um iterador de avanço. Você pode, no entanto, decrementar um iterador bidirecional, como em `--X`, `X--`, ou `(V = *X--)`. É possível acessar membros do elemento e comparar iteradores bidirecionais da mesma forma que ocorre com iteradores de avanço.

- **Acesso aleatório**. Um *iterador de acesso aleatório* `X` pode tomar o lugar de um iterador bidirecional. Com um iterador de acesso aleatório, você pode usar o operador subscrito  **\[]** para acessar elementos. Você pode usar o **+**, **-**, **+=** e **-=** operadores para mover Avançar ou retroceder um número especificado de elementos e para calcular a distância entre iteradores. Você pode comparar iteradores bidirecionais usando **==**, **! =**, **\<**, **>**, **\< =**, e **>=**.

Todos os iteradores podem ser atribuídos ou copiados. Eles são considerados objetos leves e geralmente são passados e retornados por valor, não por referência. Observe também que nenhuma das operações descritas anteriormente pode gerar uma exceção quando executada em um iterador válido.

A hierarquia das categorias de iterador pode ser resumida mostrando três sequências. Para acesso somente gravação a uma sequência, você pode usar qualquer um entre:

> iterador de saída<br/>
> -> iterador de avanço<br/>
> -> iterador bidirecional<br/>
> -> iterador de acesso aleatório<br/>

A seta para a direita significa "pode ser substituído por". Qualquer algoritmo que chama um iterador de saída deve funcionar bem com um iterador de avanço, por exemplo, mas *não* o oposto.

Para acesso somente leitura a uma sequência, você pode usar qualquer um entre:

> iterador de entrada<br/>
> -> iterador de avanço<br/>
> -> iterador bidirecional<br/>
> -> iterador de acesso aleatório<br/>

Um iterador de entrada é a mais fraca de todas as categorias, nesse caso.

Por fim, para acesso de leitura/gravação a uma sequência, você pode usar qualquer um entre:

> iterador de avanço<br/>
> -> iterador bidirecional<br/>
> -> iterador de acesso aleatório<br/>

Um ponteiro de objeto sempre pode servir como um iterador de acesso aleatório, de modo que ele pode servir como qualquer categoria de iterador se der suporte para o acesso de leitura/gravação adequado para a sequência que designa.

Um iterador `Iterator` diferente de um ponteiro de objeto também deve definir os tipos de membro exigidos pela especialização `iterator_traits<Iterator>`. Observe que esses requisitos podem ser atendidos derivando `Iterator` da classe base pública [iterator](../standard-library/iterator-struct.md).

É importante compreender as promessas e limitações de cada categoria de iterador para ver como os iteradores são usados por contêineres e algoritmos na Biblioteca Padrão do C++.

> [!NOTE]
> É possível evitar o uso de iteradores explicitamente usando loops range-for. Para obter mais informações, consulte [baseado em intervalo para a instrução](../cpp/range-based-for-statement-cpp.md).

Visual C++ agora oferece iteradores verificados e iteradores de depuração para garantir que você não substituir os limites de seu contêiner. Para obter mais informações, consulte [Iteradores verificados](../standard-library/checked-iterators.md) e [Suporte para iterador de depuração](../standard-library/debug-iterator-support.md).

## <a name="see-also"></a>Consulte também

[Referência da biblioteca padrão C++](../standard-library/cpp-standard-library-reference.md)<br/>
[Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
