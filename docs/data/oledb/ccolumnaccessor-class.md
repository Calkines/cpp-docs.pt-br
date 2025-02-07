---
title: Classe CColumnAccessor
ms.date: 11/04/2016
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
ms.openlocfilehash: 2d65fb047e758f449ed76c954bb4ac0c3623f6dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209280"
---
# <a name="ccolumnaccessor-class"></a>Classe CColumnAccessor

Gera o código injetado de consumidor.

## <a name="syntax"></a>Sintaxe

```cpp
class CColumnAccessor : public CAccessorBase
```

## <a name="remarks"></a>Comentários

No código injetado, cada coluna é associada como um acessador separado. Você deve estar ciente de que essa classe é usada no código injetado (por exemplo, você pode encontrá-lo ao depuração), mas normalmente você nunca precisará usá-la ou seus métodos diretamente.

`CColumnAccessor` implementa os seguintes métodos de stub, cada um dos quais correspondem na funcionalidade para outros métodos de classe de acessador:

- `CColumnAccessor` O construtor; cria uma instância e inicializa o `CColumnAccessor` objeto.

- `CreateAccessor` Aloca memória para a coluna de estruturas de associação e inicializa os membros de dados de coluna.

- `BindColumns` Associa as colunas para acessadores.

- `SetParameterBuffer` Aloca buffers para parâmetros.

- `AddParameter` Adiciona uma entrada de parâmetro para as estruturas de entrada de parâmetro.

- `HasOutputColumns` Determina se o acessador de colunas de saída

- `HasParameters` Determina se o acessador possui parâmetros.

- `BindParameters` Associa os parâmetros criados para colunas.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atldbcli.h

## <a name="see-also"></a>Consulte também

[Modelos de consumidor do OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referência de modelos de consumidor do OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)