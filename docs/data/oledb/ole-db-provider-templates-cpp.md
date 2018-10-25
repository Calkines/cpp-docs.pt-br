---
title: Modelos de provedor do OLE DB (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0eef554fd6b7fbd16ff7c34434d08d917b5dcea9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080059"
---
# <a name="ole-db-provider-templates-c"></a>Modelos de provedor de banco de dados OLE (C++)

OLE DB é uma parte importante da estratégia de acesso de dados Universal da Microsoft. O design de OLE DB permite que o acesso a dados de alto desempenho de qualquer fonte de dados. Quaisquer dados tabulares são visíveis através do OLE DB, independentemente se ela veio de um banco de dados. A flexibilidade oferece uma enorme quantidade de energia.

Conforme explicado em [consumidores do OLE DB e provedores](../../data/oledb/ole-db-consumers-and-providers.md), OLE DB usa o conceito de consumidores e provedores. O consumidor faz as solicitações de dados; o provedor retorna dados em um formato tabular para o consumidor. De uma perspectiva de programação, a implicação mais importante desse modelo é que o provedor deve implementar qualquer chamada que o consumidor pode fazer.

## <a name="what-is-a-provider"></a>O que é um provedor?

Um provedor OLE DB é um conjunto de objetos COM que atender a chamadas de interface de um objeto do consumidor, a transferência de dados em um formato tabular de uma fonte durável (chamada de um armazenamento de dados) para o consumidor.

Provedores podem ser simples ou complexos. O provedor pode dar suporte a uma quantidade mínima de funcionalidade ou um provedor de qualidade de produção completa ao implementar mais interfaces. Um provedor pode retornar uma tabela, permitem que o cliente determinar o formato da tabela e executar operações em que os dados.

Cada provedor implementa um conjunto padrão de objetos COM ao lidar com solicitações do cliente, com significado padrão que qualquer consumidor do OLE DB pode acessar dados em qualquer provedor, independentemente da linguagem (como C++ e básico).

Cada objeto COM contém várias interfaces, algumas das quais são necessárias e alguns dos quais são opcionais. Implementando as interfaces obrigatórias, um provedor garante um nível mínimo de funcionalidade (chamada conformidade) que qualquer cliente deve ser capaz de usar. Um provedor pode implementar interfaces opcionais para fornecer funcionalidade adicional. [O OLE DB modelo de arquitetura de provedor](../../data/oledb/ole-db-provider-template-architecture.md) descreve essas interfaces em detalhes. O cliente sempre deve chamar `QueryInterface` para determinar se um provedor dá suporte a uma determinada interface.

## <a name="ole-db-specification-level-support"></a>Suporte de nível de especificação do OLE DB

Os modelos de provedor do OLE DB oferecer suporte a especificação de versão 2.7 do OLE DB. Usando os modelos de provedor do OLE DB, você pode implementar um provedor de conformidade de nível 0. O exemplo de provedor, por exemplo, usa os modelos para implementar um servidor de comando non-MS-DOS que executa o comando DIR para consultar o sistema de arquivos. O exemplo de provedor retorna as informações de diretório em um conjunto de linhas, que é o mecanismo de banco de dados OLE padrão para retornar dados tabulares.

O tipo mais simples de provedor com suporte pelos modelos OLE DB é um provedor somente leitura com nenhum comando. Provedores de comandos também têm suporte, conforme são a capacidade de uso de indicadores e leitura/gravação. Você pode implementar um provedor de leitura/gravação ao escrever código adicional. Transações e conjuntos de linhas dinâmicos não são suportadas pela versão atual, mas você pode adicioná-los se desejar.

## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>Quando você precisa criar um provedor do OLE DB?

Você sempre precisa criar seu próprio provedor; A Microsoft fornece vários provedores predefinidos e padrão na **propriedades de vínculo de dados** caixa de diálogo no Visual C++. É o principal motivo para criar um provedor OLE DB para se beneficiar da estratégia de acesso a dados Universal. Portanto, algumas das vantagens de fazer são:

- Acessando dados através de qualquer linguagem como C++, Basic e Visual Basic Scripting Edition. Ele permite que os programadores diferentes em sua organização para acessar os mesmos dados da mesma forma, independentemente de qual idioma em que eles usam.

- Expondo seus dados para outros dados de fontes, como o SQL Server, Excel e Access. Isso pode ser muito útil se você quiser transferir dados entre diferentes formatos.

- Participar de operações de fonte de dados entre (heterogêneos). Isso pode ser uma maneira muito eficiente de data warehouse. Por meio de provedores de OLE DB, você pode manter os dados em seu formato nativo e ainda ser capaz de acessá-lo em uma operação simple.

- Adicionando recursos adicionais aos seus dados, como o processamento de consulta.

- Aumentando o desempenho de acesso aos dados controlando como ele é manipulado.

- Aumentar a robustez. Se você tiver um formato de dados proprietários que apenas um programador pode acessar, estão em risco. Usando provedores OLE DB, você pode abrir esse formato proprietário para todos os seus programadores.

## <a name="read-only-and-updatable-providers"></a>Provedores atualizáveis e somente leitura

Provedores podem variar muito em complexidade e a funcionalidade. É útil categorizar os provedores em provedores de somente leitura e atualizável:

- Visual C++ 6.0 tem suporte somente os provedores de somente leitura. [Criando um provedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md) discute como criar um provedor somente leitura.
- Visual C++ oferece suporte a provedores atualizáveis, o que podem atualizar (gravar) o repositório de dados. Para obter informações sobre os provedores atualizáveis, consulte [criando um provedor atualizável](../../data/oledb/creating-an-updatable-provider.md); o [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) é um exemplo de um provedor atualizável.

Para obter mais informações, consulte:

- [A arquitetura de modelo de provedor do OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)

- [Criando um provedor do OLE DB](../../data/oledb/creating-an-ole-db-provider.md)

- [Programação do OLE DB](../../data/oledb/ole-db-programming.md)

## <a name="see-also"></a>Consulte também

[Acesso a dados](../data-access-in-cpp.md)<br/>
[Documentação do SDK do OLE DB](/previous-versions/windows/desktop/ms722784)
[referência do programador do OLE DB](/previous-versions/windows/desktop/ms713643)