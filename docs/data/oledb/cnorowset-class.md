---
title: Classe CNoRowset | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
dev_langs:
- C++
helpviewer_keywords:
- CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f14ad79e1cbd2207b4eb1582cb80e0107d68ec39
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064232"
---
# <a name="cnorowset-class"></a>Classe CNoRowset

Pode ser usado como um argumento de modelo (`TRowset`) para [CCommand](../../data/oledb/ccommand-class.md) ou [CTable](../../data/oledb/ctable-class.md).

## <a name="syntax"></a>Sintaxe

```cpp
template <class TAccessor = CAccessorBase>
class CNoRowset
```

### <a name="parameters"></a>Parâmetros

*TAccessor*<br/>
Uma classe de acessador. O padrão é `CAccessorBase`.

## <a name="remarks"></a>Comentários

Use `CNoRowset` como um argumento de modelo se o comando não retornar um conjunto de linhas.

`CNoRowset` implementa os seguintes métodos de stub, cada um dos quais correspondem aos outros métodos de classe de acessador:

- `BindFinished` -Indica quando a associação for concluída (retorna `S_OK`).

- `Close` -Libera linhas e a interface IRowset atual.

- `GetIID` -Recupera a ID de interface de um ponto de conexão.

- `GetInterface` -Recupera uma interface.

- `GetInterfacePtr` -Recupera um ponteiro de interface encapsulado.

- `SetAccessor` -Define um ponteiro para o acessador.

- `SetupOptionalRowsetInterfaces` -Configura interfaces opcionais para o conjunto de linhas.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atldbcli.h

## <a name="see-also"></a>Consulte também

[Modelos de consumidor do OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referência de modelos de consumidor do OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)