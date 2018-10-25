---
title: Classe CStreamRowset | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CStreamRowset<TAccessor>
- ATL::CStreamRowset
- CStreamRowset
- ATL.CStreamRowset<TAccessor>
- ATL.CStreamRowset
- CStreamRowset::CStreamRowset
- CStreamRowset.CStreamRowset
- ATL.CStreamRowset.CStreamRowset
- ATL::CStreamRowset::CStreamRowset
- CStreamRowset
- CStreamRowset<TAccessor>::CStreamRowset
- ATL::CStreamRowset<TAccessor>::CStreamRowset
- CStreamRowset<TAccessor>.Close
- ATL.CStreamRowset<TAccessor>.Close
- CStreamRowset::Close
- CStreamRowset<TAccessor>::Close
- ATL::CStreamRowset::Close
- ATL.CStreamRowset.Close
- ATL::CStreamRowset<TAccessor>::Close
- CStreamRowset.Close
dev_langs:
- C++
helpviewer_keywords:
- CStreamRowset class
- CStreamRowset class, constructor
- Close method
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8a19085ae5d46396415e5b54b9acada547bc8079
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077784"
---
# <a name="cstreamrowset-class"></a>Classe CStreamRowset

Usado em uma `CCommand` ou `CTable` declaração.

## <a name="syntax"></a>Sintaxe

```cpp
template <class TAccessor = CAccessorBase>
class CStreamRowset
```

### <a name="parameters"></a>Parâmetros

*TAccessor*<br/>
Uma classe de acessador.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atldbcli.h

## <a name="members"></a>Membros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CStreamRowset](#cstreamrowset)|Construtor. Cria uma instância e inicializa o `CStreamRowset` objeto.|
|[Fechar](#close)|Versões do [ISequentialStream](/previous-versions/windows/desktop/ms718035) ponteiro de interface na classe.|

## <a name="remarks"></a>Comentários

Use `CStreamRowset` em seu `CCommand` ou `CTable` declaração, por exemplo:

[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]

ou

[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]

`ICommand::Execute` Retorna um `ISequentialStream` ponteiro, que é armazenado em `m_spStream`. Você, em seguida, usar o `Read` método para recuperar os dados (cadeia de caracteres Unicode) em formato XML. Por exemplo:

[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]

SQL Server 2000 executa o formatação de XML e retornará todas as colunas e todas as linhas do conjunto de linhas como uma cadeia de caracteres XML.

> [!NOTE]
>  Esse recurso funciona apenas com o SQL Server 2000.

## <a name="cstreamrowset"></a> Cstreamrowset:: Cstreamrowset

Cria uma instância e inicializa o `CStreamRowset` objeto.

### <a name="syntax"></a>Sintaxe

```cpp
CStreamRowset();
```

## <a name="close"></a> Cstreamrowset:: Close

Versões do [ISequentialStream](/previous-versions/windows/desktop/ms718035) ponteiro de interface na classe.

### <a name="syntax"></a>Sintaxe

```cpp
void Close();
```

## <a name="see-also"></a>Consulte também

[Modelos de consumidor do OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referência de modelos de consumidor do OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)