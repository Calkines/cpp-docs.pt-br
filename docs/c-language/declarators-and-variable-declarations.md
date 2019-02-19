---
title: Declaradores e declarações variáveis
ms.date: 11/04/2016
helpviewer_keywords:
- declaring variables, declarators
- declarators, definition
- declaring variables, declaration statements
ms.assetid: 5fd67a6a-3a6a-4ec9-b257-3f7390a48d40
ms.openlocfilehash: 928de4b1724577a9fdb282f5109b4b5d0b31c4e6
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147484"
---
# <a name="declarators-and-variable-declarations"></a>Declaradores e declarações variáveis

O restante desta seção descreve o formato e o significado das declarações para os tipos de variável resumidos nesta lista. Em particular, as demais seções explicam como declarar o seguinte:

|Tipo de variável|Descrição|
|----------------------|-----------------|
|[Variáveis simples](../c-language/simple-variable-declarations.md)|Variáveis de valor único com tipo integral ou de ponto flutuante|
|[Matrizes](../c-language/array-declarations.md)|Variáveis compostas de uma coleção de elementos com o mesmo tipo|
|[Ponteiros](../c-language/pointer-declarations.md)|Variáveis que apontam para outras variáveis e contêm locais de variáveis (na forma de endereços) em vez de valores|
|[Variáveis de enumeração](../c-language/c-enumeration-declarations.md)|Variáveis simples com tipo integral que mantêm um único valor de um conjunto de constantes de inteiro nomeadas|
|[Estruturas](../c-language/structure-declarations.md)|Variáveis compostas de uma coleção de valores que podem ter tipos diferentes|
|[Uniões](../c-language/union-declarations.md)|Variáveis compostas de vários valores de tipos diferentes que ocupam o mesmo espaço de armazenamento|

Um declarador é a parte de uma declaração que especifica o nome a ser introduzido no programa. Pode incluir modificadores como <strong>\*</strong> (pointer-to) e qualquer uma das palavras-chave de convenção de chamada da Microsoft.

**Seção específica da Microsoft**

No declarador

```C
__declspec(thread) char *var;
```

`char` é o especificador de tipo, `__declspec(thread)` e `*` são os modificadores, e `var` é o nome do identificador.

**Fim da seção específica da Microsoft**

Você usa declaradores para declarar matrizes de valores, ponteiros para valores e funções que retornam valores de um tipo especificado. Os declaradores aparecem nas declarações de matrizes e de ponteiros descritas posteriormente nesta seção.

## <a name="syntax"></a>Sintaxe

*declarator*:<br/>
&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(**  *declarator*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **[**  *constant-expression*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *parameter-type-list*  **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **(**  *identifier-list*<sub>opt</sub> **)**

*pointer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *type-qualifier-list*<sub>opt</sub> *pointer*

*type-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier-list type-qualifier*

> [!NOTE]
> Consulte a sintaxe de *declaration* na [Visão Geral de Declarações](../c-language/overview-of-declarations.md) ou em [Resumo da Sintaxe da Linguagem C](../c-language/c-language-syntax-summary.md) para a sintaxe que se refere a *declarator*.

Quando um declarador consiste em um identificador não modificado, o item que está sendo declarado tem um tipo de base. Se um asterisco (<strong>\*</strong>) aparecer à esquerda de um identificador, o tipo será modificado para um tipo de ponteiro. Se o identificador for seguido por colchetes (**[ ]**), o tipo será modificado para um tipo de matriz. Se o identificador for seguido por parênteses, o tipo será modificado para um tipo de função. Para obter mais informações sobre como interpretar a precedência em declarações, consulte [Interpretação de declaradores mais complexos](../c-language/interpreting-more-complex-declarators.md).

Cada declarador declara pelo menos um identificador. Um declarador deve incluir um especificador de tipo para ser uma declaração completa. O especificador de tipo fornece o tipo dos elementos de um tipo de matriz, o tipo de objeto tratado por um tipo ponteiro ou o tipo de retorno de uma função.

As declarações de [matrizes](../c-language/array-declarations.md) e de [ponteiros](../c-language/pointer-declarations.md) são discutidas em mais detalhes posteriormente nesta seção. Os exemplos a seguir ilustram alguns formatos simples de declaradores:

```C
int list[20]; // Declares an array of 20 int values named list
char *cp;     // Declares a pointer to a char value
double func( void ); // Declares a function named func, with no
                     // arguments, that returns a double value
int *aptr[10] // Declares an array of 10 pointers
```

**Seção específica da Microsoft**

O compilador de C da Microsoft não limita o número de declaradores que podem modificar um tipo aritmético, de estrutura ou de união. O número é limitado somente pela memória disponível.

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[Declarações e tipos](../c-language/declarations-and-types.md)
