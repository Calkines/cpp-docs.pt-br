---
title: Atributos de compilador (COM C++)
ms.date: 10/02/2018
helpviewer_keywords:
- cl.exe compiler, attributes
- attributes [C++/CLI], compiler
ms.assetid: 53cd9bee-1521-48ec-b171-80feac2096cc
ms.openlocfilehash: ea4d3119a640c0642664210384c297e011104411
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030811"
---
# <a name="compiler-attributes"></a>Atributos de compilador

Os atributos de compilador fornecem uma variedade de funcionalidades.

|Atributo|Descrição|
|---------------|-----------------|
|[emitidl](emitidl.md)|Determina se todos os atributos IDL subsequentes serão processados e colocados no arquivo. idl gerado.|
|[event_receiver](event-receiver.md)|Cria um receptor de eventos.|
|[origem do evento](event-source.md)|Cria uma origem de evento.|
|[export](export.md)|Faz com que uma estrutura de dados a serem colocados no arquivo. idl.|
|[implementa](implements-cpp.md)|Especifica as interfaces de distribuição que são forçadas para serem membros da coclass IDL.|
|[importidl](importidl.md)|Insere o arquivo. idl especificado no arquivo. idl gerado.|
|[importlib](importlib.md)|Torna os tipos que já foram compilados em outra biblioteca de tipos disponível para a biblioteca de tipos que está sendo criada.|
|[includelib](includelib-cpp.md)|Faz com que um arquivo. IDL ou. h a serem incluídos no arquivo. idl gerado.|
|[library_block](library-block.md)|Coloca uma construção de dentro do bloco de biblioteca do arquivo. idl.|
|[no_injected_text](no-injected-text.md)|Impede que o compilador injetando código como resultado do uso do atributo.|
|[satype](satype.md)|Especifica o tipo de dados a `SAFEARRAY`.|
|[version](version-cpp.md)|Identifica uma versão específica entre várias versões de uma interface ou classe.|

## <a name="see-also"></a>Consulte também

[Atributos por grupo](attributes-by-group.md)