---
title: Sistema de tipos (C++/CX)
ms.date: 02/03/2017
ms.assetid: b67bee8a-b526-4872-969e-ef22724e88fe
ms.openlocfilehash: fbc7a178621624e396c80509703ce1b5b4c19162
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745948"
---
# <a name="type-system-ccx"></a>Sistema de tipos (C++/CX)

Usando a arquitetura de tempo de execução do Windows, você pode usar C + + c++ /CLI CX, Visual Basic, Visual c# e JavaScript para escrever aplicativos e componentes que diretamente acessar a API do Windows e interoperem com outros aplicativos do Windows Runtime e os componentes. Aplicativos da plataforma do Windows universal escritos em C++ são compilados para código nativo executado diretamente na CPU. Aplicativos da plataforma do Windows universal escritos em c# ou Visual Basic são compilados para Microsoft intermediate language (MSIL) e executar no common language runtime (CLR). Aplicativos da plataforma do Windows universal escritos em JavaScript são executam em um ambiente de tempo de execução. Os próprios componentes de sistema operacional de tempo de execução do Windows são escritos em C++ e executados como código nativo. Todos esses componentes e aplicativos da plataforma Universal do Windows se comunicam diretamente por meio da interface de binária de aplicativo (ABI) do tempo de execução do Windows.

Para habilitar o suporte para o tempo de execução do Windows em uma linguagem C++ moderna, a Microsoft criou o C + + c++ /CLI CX. C + + c++ /CLI CX fornece tipos básicos internos e implementações de tipos fundamentais do tempo de execução do Windows que permitem que aplicativos e componentes se comuniquem na ABI com aplicativos que são escritos em outras linguagens C++. Você pode consumir qualquer tipo de tempo de execução do Windows, ou criar classes, structs, interfaces e outros tipos definidos pelo usuário que podem ser consumidos por outros componentes e aplicativos da plataforma Universal do Windows. um aplicativo de plataforma Universal do Windows que é escrito em C + + c++ /CX também pode usar classes regulares C++ e estruturas, desde que eles não tenham acessibilidade pública.

Para uma discussão mais profunda da projeção de idioma C++/CX e como ela funciona sob as coberturas, veja estas postagens do blog:

1. [C + + c++ /CX parte 0 de \[n\]: Uma introdução](https://blogs.msdn.microsoft.com/vcblog/2012/08/29/ccx-part-0-of-n-an-introduction)

1. [C + + c++ /CX parte 1 de \[n\]: Uma classe simples](https://blogs.msdn.microsoft.com/vcblog/2012/09/05/ccx-part-1-of-n-a-simple-class)

1. [C + + c++ /CX parte 2 de \[n\]: Tipos que desempenham funções diferentes](https://blogs.msdn.microsoft.com/vcblog/2012/09/17/ccx-part-2-of-n-types-that-wear-hats)

1. [C + + c++ /CX parte 3 de \[n\]: Em construção](https://blogs.msdn.microsoft.com/vcblog/2012/10/05/ccx-part-3-of-n-under-construction/)

1. [C + + c++ /CX parte 4 de \[n\]: Funções de membro estático](https://blogs.msdn.microsoft.com/vcblog/2012/10/19/ccx-part-4-of-n-static-member-functions)

## <a name="windows-metadata-winmd-files"></a>Arquivos de metadados do Windows (.winmd)

Quando você compila um aplicativo de plataforma Universal do Windows que está escrito em C++, o compilador gera o executável no código de máquina nativo e também gera um arquivo de metadados (. winmd) separado do Windows que contém descrições dos tipos públicos do tempo de execução do Windows, que incluem classes, estruturas, enumerações, interfaces, interfaces parametrizadas e delegados. O formato de metadados lembra o formato usado nos assemblies do .NET Framework.  Em um componente do C++, o arquivo .winmd contém apenas metadados; o código executável reside em um arquivo separado. Esse é o caso para os componentes de tempo de execução do Windows que estão incluídos com o Windows. O nome do arquivo WinMD deve coincidir ou ser um prefixo do namespace raiz no código-fonte. (Para as linguagens .NET Framework, o arquivo .winmd contém o código e os metadados, assim como um assembly do .NET Framework.)

Os metadados no arquivo .winmd representam a superfície publicada do seu código. Tipos publicados são visíveis para outras plataformas Windows Universal independentemente da linguagem, os outros aplicativos são escritos em. Portanto, os metadados ou seu código publicado, só pode conter tipos especificados pelo sistema de tipo de tempo de execução do Windows. As construções de linguagem específicas ao C++, como classes, matrizes, modelos ou contêineres STL regulares não podem ser publicadas nos metadados porque um aplicativo cliente Javascript ou C# não saberia o que fazer com elas.

Se um tipo ou um método estará visível nos metadados dependerá de quais modificadores de acessibilidade foram aplicados a ele. Para ser visível, um tipo deve ser declarado em um namespace e deve ser declarado como público. Uma classe ref não pública é permitida como um tipo auxiliar interno no seu código; ela não está visível nos metadados. Até mesmo em uma classe ref pública, nem todos os membros estão necessariamente visíveis. A tabela a seguir lista a relação entre especificadores de acesso C++ em uma classe ref pública e visibilidade de metadados de tempo de execução do Windows:

|||
|-|-|
|**Publicado nos metadados**|**Não publicado nos metadados**|
|públicos|private|
|protected|interno|
|público protegido|privado protegido|

Use o **Pesquisador de objetos** para exibir o conteúdo de arquivos .winmd. Os componentes de tempo de execução do Windows que estão incluídos com o Windows estão no arquivo winmd. O arquivo Default winmd contém tipos fundamentais que são usados no C + + c++ /CX e Platform. winmd contém tipos adicionais do namespace de plataforma. Por padrão, esses três arquivos. winmd são incluídos em cada projeto de C++ para aplicativos da plataforma Universal do Windows.

> [!TIP]
> Os tipos no [Platform::Collections Namespace](../cppcx/platform-collections-namespace.md) não aparecem no arquivo .winmd porque não são públicos. Eles são implementações particulares específicas do C++ das interfaces definidas em `Windows::Foundation::Collections`. Um aplicativo de tempo de execução do Windows que é escrito em JavaScript ou c# não sabe o que um [Platform::Collections::Vector&lt;2](../cppcx/platform-collections-vector-class.md) for, mas pode consumir um `Windows::Foundation::Collections::IVector`. Os tipos `Platform::Collections` são definidos em collection.h.

## <a name="windows-runtime-type-system-in-ccx"></a>Sistema de tipo de tempo de execução do Windows no C + + c++ /CX

As seções a seguir descrevem os principais recursos do sistema de tipo de tempo de execução do Windows e como eles são suportados no C + + c++ /CLI CX.

### <a name="namespaces"></a>Namespaces

Todos os tipos de tempo de execução do Windows devem ser declarados dentro de um namespace; a API do Windows em si é organizada por namespaces. Um arquivo .winmd deve ter o mesmo nome do namespace raiz. Por exemplo, uma classe denominada A.B.C.MyClass poderá ser instanciada somente se for definida em um arquivo de metadados denominado A.winmd ou A.B.winmd ou A.B.C.winmd. O nome da DLL não precisa coincidir com o nome do arquivo .winmd.

A própria API do Windows foi reinventada como uma biblioteca de classes bem fatorada organizada por namespaces.  Todos os componentes de tempo de execução do Windows são declarados nos namespaces Windows.

Para obter mais informações, consulte [Namespaces e visibilidade de tipo](../cppcx/namespaces-and-type-visibility-c-cx.md).

### <a name="fundamental-types"></a>Tipos fundamentais

O tempo de execução do Windows define a seguintes tipos fundamentais, UInt8, Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, Double, Char16, Boolean e cadeia de caracteres. C + + c++ /CX oferece suporte aos tipos numéricos fundamentais em seu namespace padrão como uint16, uint32, uint64, int16, int32, int64, float32, float64 e char16. Boolean e String também são definidos no namespace Platform.

C + + c++ /CX também define uint8, equivalente a `unsigned char`, que não há suporte para o tempo de execução do Windows e não pode ser usado em APIs públicas.

Um tipo fundamental pode ser transformado em anulável convertendo-o em uma interface [Platform::IBox Interface](../cppcx/platform-ibox-interface.md) . Para obter mais informações, consulte [Classes e estruturas de valor](../cppcx/value-classes-and-structs-c-cx.md).

Para obter mais informações sobre tipos fundamentais, consulte [Tipos fundamentais](../cppcx/fundamental-types-c-cx.md)

### <a name="strings"></a>Cadeias de caracteres

Uma cadeia de caracteres de tempo de execução do Windows é uma sequência imutável de caracteres UNICODE de 16 bits. Uma cadeia de caracteres de tempo de execução do Windows é projetada como `Platform::String^`. Essa classe fornece métodos para construção, manipulação e conversão de cadeia de caracteres de e em `wchar_t`.

Para obter mais informações, consulte [Cadeias de caracteres](../cppcx/strings-c-cx.md).

### <a name="arrays"></a>Matrizes

O tempo de execução do Windows oferece suporte a matrizes dimensionais 1 de qualquer tipo. Não há suporte para matrizes de matrizes.  No C + + c++ /CLI CX, matrizes de tempo de execução do Windows são projetadas como o [classe Platform:: array](../cppcx/platform-array-class.md).

Para obter mais informações, consulte [matriz e WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)

### <a name="ref-classes-and-structs"></a>Classes e estruturas ref

Uma classe de tempo de execução do Windows é projetada no C + + c++ /CX como uma classe ou estrutura ref, porque eles são copiados por referência. O gerenciamento de memória para classes e estruturas ref é manipulado de forma transparente por meio da contagem de referência. Quando a última referência a um objeto fica fora do escopo, o objeto é destruído. Uma classe ou estrutura ref pode:

- Conter como membros construtores, métodos, propriedades e eventos. Esses membros podem ter acessibilidade pública, privada, protegida ou interna.

- Pode conter definições aninhadas privadas de enum, estrutura ou classe.

- Pode herdar diretamente de uma classe base e pode implementar qualquer número de interfaces. Todas as classes ref podem ser convertidas implicitamente na [Platform::Object Class](../cppcx/platform-object-class.md) e podem substituir seus métodos virtuais, por exemplo, [Object::ToString](../cppcx/platform-object-class.md#tostring).

Uma classe ref que tem um construtor público também precisa ser declarada como fechada para evitar mais derivação.

Para obter mais informações, consulte [Classes e estruturas ref](../cppcx/ref-classes-and-structs-c-cx.md)

### <a name="value-classes-and-structs"></a>Classes e estruturas de valor

Uma classe ou estrutura de valor representa uma estrutura de dados básica e contém apenas campos, que podem ser classes de valor, estruturas de valor ou o tipo `Platform::String^`.  As estruturas e classes de valor são copiadas por valor.

Um estrutura de valor pode ser transformada em anulável convertendo em uma interface IBox.

Para obter mais informações, consulte [Classes e estruturas de valor](../cppcx/value-classes-and-structs-c-cx.md).

### <a name="partial-classes"></a>Classes parciais

O recurso de classe parcial permite que uma classe seja definida em vários arquivos. Ele é usado principalmente para habilitar a geração de ferramentas, como o editor XAML, para modificar um arquivo sem tocar no arquivo que você edita.

Para obter mais informações, consulte [Classes parciais](../cppcx/partial-classes-c-cx.md)

### <a name="properties"></a>Propriedades

Uma propriedade é um membro de dados públicos de qualquer tipo de tempo de execução do Windows e é implementada como um par de métodos get/set. O código de cliente acessa uma propriedade como se fosse um campo público. Uma propriedade que não requer código get ou set personalizado é conhecida como uma *propriedade trivial* e pode ser declarada sem métodos get ou set explícitos.

Para obter mais informações, consulte [Propriedades](../cppcx/properties-c-cx.md).

### <a name="windows-runtime-collections-in-ccx"></a>Coleções de tempo de execução do Windows no C + + c++ /CX

O tempo de execução do Windows define um conjunto de interfaces para tipos de coleção que cada linguagem implementa sua própria maneira. C + + c++ /CLI CX fornece implementações na [Platform::Collections::Vector&lt;2](../cppcx/platform-collections-vector-class.md), [2&gt;classe Platform::Collections::Map&lt;2](../cppcx/platform-collections-map-class.md)e outros tipos de coleção concreta relacionadas, que são compatíveis com suas Contrapartes padrão do modelo STL (biblioteca).

Para obter mais informações, consulte [coleções](../cppcx/collections-c-cx.md).

### <a name="template-ref-classes"></a>Classes de referência de modelo

As classes ref particulares e internas podem ser modeladas e especializadas.

Para obter mais informações, consulte [Classes de referência de modelo](../cppcx/template-ref-classes-c-cx.md).

### <a name="interfaces"></a>Interfaces

Uma interface de tempo de execução do Windows define um conjunto de propriedades públicas, métodos e eventos que uma classe ou estrutura ref deverá implementar se ele herda da interface.

Para obter mais informações, consulte [Interfaces](../cppcx/interfaces-c-cx.md).

### <a name="enums"></a>Enums

Uma classe enum no tempo de execução do Windows é semelhante a uma enum com escopo em C++. O tipo subjacente é int32, a menos que o atributo [Flags] seja aplicado; nesse caso, o tipo subjacente será uint32.

Para obter mais informações, consulte [Enums](../cppcx/enums-c-cx.md).

### <a name="delegates"></a>Delegados

Um delegado no tempo de execução do Windows é análogo a um objeto std:: Function no C++. É um tipo especial de classe ref usado para invocar funções fornecidas pelo cliente que têm assinaturas compatíveis.  Delegados são mais comumente usados em tempo de execução do Windows como o tipo de um evento.

Para obter mais informações, consulte [Delegados](../cppcx/delegates-c-cx.md).

### <a name="exceptions"></a>Exceções

Em C++/CX, você pode capturar tipos de exceção personalizados, tipos [std::exception](../standard-library/exception-class.md) e tipos [Platform::Exception](../cppcx/platform-exception-class.md) .

Para obter mais informações, consulte [Exceções](../cppcx/exceptions-c-cx.md).

### <a name="events"></a>Eventos

Um evento é um membro público em uma classe ou estrutura ref cujo tipo é delegado. Um evento somente pode ser invocado, ou seja, disparado, pela classe que o possui. No entanto, o código de cliente pode fornecer suas próprias funções, que são conhecidas como manipuladores de eventos e são invocadas quando a classe possuidora dispara o evento.

Para obter mais informações, consulte [Eventos](../cppcx/events-c-cx.md).

### <a name="casting"></a>Conversão

O C++/CX oferece suporte aos operadores cast C++ padrão [static_cast](../cpp/static-cast-operator.md), [dynamic_cast](../cpp/dynamic-cast-operator.md)e [reinterpret_cast](../cpp/reinterpret-cast-operator.md), além do operador **safe_cast** que é específico ao C++/CX.

Para obter mais informações, consulte [Conversão](../cppcx/casting-c-cx.md).

### <a name="boxing"></a>Boxing

Uma variável demarcada é um tipo de valor que é encapsulado em um tipo de referência em situações nas quais a semântica de referência é necessária.

Para obter mais informações, consulte [Boxing](../cppcx/boxing-c-cx.md).

### <a name="attributes"></a>Atributos

Um atributo é um valor de metadados que pode ser aplicado a qualquer tipo de tempo de execução do Windows ou um membro de tipo e pode ser inspecionado em tempo de execução. O tempo de execução do Windows define um conjunto de atributos comuns no `Windows::Foundation::Metadata` namespace. Atributos definidos pelo usuário nas interfaces públicas não são suportados pelo tempo de execução do Windows nesta versão.

## <a name="api-deprecation"></a>Substituição de API

Descreve como marcar APIs públicas como preteridas usando o mesmo atributo usado pelos tipos de sistema de tempo de execução do Windows.

Para obter mais informações, consulte [reprovando tipos e membros](../cppcx/deprecating-types-and-members-c-cx.md).

## <a name="see-also"></a>Consulte também

[Referência de linguagem do Visual C++](../cppcx/visual-c-language-reference-c-cx.md)
