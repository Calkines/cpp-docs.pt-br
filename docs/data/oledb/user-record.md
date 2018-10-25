---
title: Registro de usuário | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1c1958604edbb2f9d9c10e58082e70c2df400b8c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077368"
---
# <a name="user-record"></a>Registro de usuário

O registro de usuário fornece a estrutura de código e os dados que representa os dados da coluna para um conjunto de linhas. Um registro de usuário pode ser criado em tempo de compilação ou tempo de execução. Quando você cria um provedor usando o OLE DB Assistente de provedor ATL, o assistente cria um registro de usuário padrão que se parece com isso (supondo que você especificou um nome de provedor [nome curto] da *personalizado*):

```cpp
class CWindowsFile:
   public WIN32_FIND_DATA
{
public:

BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()

};
```

Os modelos de provedor do OLE DB lidar com todas as especificações de OLE DB relativas à interações com o cliente. Para obter os dados de coluna necessários para uma resposta, o provedor chamará o `GetColumnInfo` função, que você deve colocar no registro do usuário. Você pode substituir explicitamente `GetColumnInfo` no registro do usuário, por exemplo, por declará-la no arquivo. h como mostrado aqui:

```cpp
template <class T>
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols)
```

Isso é equivalente a:

```cpp
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)
```

Você também deve implementar `GetColumnInfo` no arquivo. cpp do registro do usuário.

As macros PROVIDER_COLUMN_MAP auxiliam na criação de um `GetColumnInfo` função:

- BEGIN_PROVIDER_COLUMN_MAP define o protótipo de função e uma matriz estática de `ATLCOLUMNINFO` estruturas.

- PROVIDER_COLUMN_ENTRY define e inicializa um único `ATLCOLUMNINFO`.

- END_PROVIDER_COLUMN_MAP fechará a matriz e a função. Ele também coloca a contagem de elementos de matriz para o *pcCols* parâmetro.

Quando um registro de usuário é criado em tempo de execução `GetColumnInfo` usa o *pEsse* parâmetro para receber um ponteiro para uma instância de conjunto de linhas ou de comando. Comandos e conjuntos de linhas devem dar suporte a `IColumnsInfo` de interface, para que as informações de coluna podem ser obtidas este ponteiro.

`CommandClass` e `RowsetClass` são o comando e o conjunto de linhas que usam o registro do usuário.

Para obter um exemplo mais detalhado de como substituir `GetColumnInfo` em um registro de usuário, consulte [dinamicamente determinando colunas retornadas ao consumidor](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>Consulte também

[Arquitetura de modelo do provedor do OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)