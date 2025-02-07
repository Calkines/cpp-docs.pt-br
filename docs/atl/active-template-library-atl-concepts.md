---
title: Conceitos da Biblioteca de Modelo Ativa (ATL)
ms.date: 05/06/2019
helpviewer_keywords:
- ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
ms.openlocfilehash: a7b6a40eaed05462f3aa5c877a1c4da3e19c0b03
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65836993"
---
# <a name="active-template-library-atl-concepts"></a>Conceitos da Biblioteca de Modelo Ativa (ATL)

A ATL (Active Template Library) é um conjunto de classes C++ baseadas em modelo que permite criar objetos COM (Component Object Model) pequenos e rápidos. Ela tem suporte especial para as principais funcionalidades do COM, incluindo implementações de estoque, interfaces duplas, interfaces de enumerador COM padrão, pontos de conexão, interfaces destacáveis e controles ActiveX.

Se você usa a programação da ATL com muita frequência, o ideal é saber mais sobre os atributos COM e .NET, que foram projetados para simplificar a programação COM. Para obter mais informações, confira [Programação atribuída](../windows/attributed-programming-concepts.md). (Os atributos COM e .NET não devem ser confundidos com a funcionalidade \[\[attribute]] no padrão do C++.)

## <a name="in-this-section"></a>Nesta seção

[Introdução ao COM e à ATL](../atl/introduction-to-com-and-atl.md)<br/>
Apresenta os principais conceitos por trás do COM (Component Object Model). Este artigo explica também brevemente o que é a ATL e quando usá-la.

[Princípios básicos de objetos COM da ATL](../atl/fundamentals-of-atl-com-objects.md)<br/>
Aborda a relação entre várias classes da ATL e como essas classes são implementadas.

[Interfaces duplas e a ATL](../atl/dual-interfaces-and-atl.md)<br/>
Descreve as interfaces duplas da perspectiva da ATL.

[Coleções e enumeradores da ATL](../atl/atl-collections-and-enumerators.md)<br/>
Descreve a implementação e a criação de coleções e enumeradores na ATL.

[Fundamentos do controle composto](../atl/atl-composite-control-fundamentals.md)<br/>
Fornece instruções passo a passo para a criação de um controle composto. Um controle composto é um tipo de controle ActiveX que pode conter outros controles ActiveX ou controles do Windows.

[Perguntas frequentes sobre contenção de controle da ATL](../atl/atl-control-containment-faq.md)<br/>
Aborda as perguntas fundamentais relacionadas à hospedagem de controles com a ATL.

[Página de propriedades COM da ATL](../atl/atl-com-property-pages.md)<br/>
Mostra como especificar e implementar páginas de propriedades do COM.

[Suporte da ATL para controles DHTML](../atl/atl-support-for-dhtml-controls.md)<br/>
Fornece instruções passo a passo para a criação de um controle DHTML.

[Pontos de conexão da ATL](../atl/atl-connection-points.md)<br/>
Explica o que são pontos de conexão e como a ATL implementa-os.

[Manipulação de eventos e a ATL](../atl/event-handling-and-atl.md)<br/>
Descreve as etapas que você precisa executar para manipular eventos COM usando as classes [IDispEventImpl](../atl/reference/idispeventimpl-class.md) e [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) da ATL.

[ATL e o marshaler livre de threads](../atl/atl-and-the-free-threaded-marshaler.md)<br/>
Fornece detalhes sobre a opção do Assistente de Objeto Simples da ATL que permite que a classe agregue o FTM (marshaler livre de threads).

[Como especificar o modelo de threading do projeto](../atl/specifying-the-threading-model-for-a-project-atl.md)<br/>
Descreve as macros que estão disponíveis para controlar o desempenho em tempo de execução relacionado ao threading no projeto.

[Classes de módulo da ATL](../atl/atl-module-classes.md)<br/>
Aborda as novas classes de módulo da ATL 7.0. As classes de módulo implementam a funcionalidade básica necessária para a ATL.

[Serviços da ATL](../atl/atl-services.md)<br/>
Aborda a série de eventos ocorridos quando um serviço é implementado. Também aborda alguns dos conceitos relacionados ao desenvolvimento de um serviço.

[Classes de janela da ATL](../atl/atl-window-classes.md)<br/>
Descreve como criar janelas de superclasse e subclasse na ATL. As classes de janela da ATL não são classes COM.

[Classes de coleção da ATL](../atl/atl-collection-classes.md)<br/>
Descreve como usar matrizes e mapas na ATL.

[Componente de Registro da ATL (Registrador)](../atl/atl-registry-component-registrar.md)<br/>
Aborda a sintaxe de script e os parâmetros substituíveis da ATL. Ele também explica como configurar uma vinculação estática para o Registrador.

[Programando com código de tempo de execução C e da ATL](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
Aborda os benefícios da vinculação estática ou dinâmica ao CRT (Biblioteca em Tempo de Execução C).

[Programação com o CComBSTR](../atl/programming-with-ccombstr-atl.md)<br/>
Aborda várias situações que exigem cuidado durante a programação com `CComBSTR`.

[Referência de codificação](../atl/atl-encoding-reference.md)<br/>
Fornece funções e macros que dão suporte à codificação de uma variedade de padrões comuns da Internet como uuencode, hexadecimal e UTF8 em atlenc.h.

[Referência de utilitários](../atl/atl-utilities-reference.md)<br/>
Fornece código para manipular URLs e caminhos na forma de [CPathT](../atl/reference/cpatht-class.md) e [CUrl](../atl/reference/curl-class.md). Um pool de threads, [CThreadPool](../atl/reference/cthreadpool-class.md), pode ser usado em seus próprios aplicativos. Esse código pode ser encontrado em atlpath.h e atlutil.h.

## <a name="related-sections"></a>Seções relacionadas

[Tutorial da ATL](../atl/active-template-library-atl-tutorial.md)<br/>
Explica como criar um controle e demonstra alguns conceitos básicos da ATL no processo.

[Amostras da ATL](../overview/visual-cpp-samples.md)<br/>
Fornece descrições de links para os programas de exemplo da ATL.

[Criando um projeto ATL](../atl/reference/creating-an-atl-project.md)<br/>
Contém informações sobre o Assistente de Projeto da ATL.

[Assistente de Controle da ATL](../atl/reference/atl-control-wizard.md)<br/>
Explica como adicionar classes.

[Programação atribuída](../windows/attributed-programming-concepts.md)<br/>
Fornece uma visão geral sobre como usar atributos para simplificar a programação COM, além de uma lista de links para tópicos mais detalhados.

[Visão geral de classes da ATL](../atl/atl-class-overview.md)<br/>
Fornece informações de referência e links para as classes da ATL.
