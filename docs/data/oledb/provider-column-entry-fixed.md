---
title: PROVIDER_COLUMN_ENTRY_FIXED | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROVIDER_COLUMN_ENTRY_FIXED
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_FIXED macro
ms.assetid: 71f9c9aa-56a0-488b-96ba-5c72da9c71d0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f374f5e7d4a2dfd24cdd3b2067b0bda935ce438f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="providercolumnentryfixed"></a>PROVIDER_COLUMN_ENTRY_FIXED
Representa uma coluna específica suportada pelo provedor.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name  
, ordinal, dbtype, member )  
```  
  
#### <a name="parameters"></a>Parâmetros  
 *name*  
 [in] O nome da coluna.  
  
 `ordinal`  
 [in] O número da coluna. A menos que a coluna é uma coluna de indicador, o número da coluna não deve ser 0.  
  
 `dbtype`  
 [in] O tipo de dados em [DBTYPE](https://msdn.microsoft.com/en-us/library/ms711251.aspx).  
  
 `member`  
 [in] A variável de membro em `dataClass` que armazena os dados.  
  
## <a name="remarks"></a>Comentários  
 Permite que você especifique o tipo de dados de coluna.  
  
## <a name="example"></a>Exemplo  
 Consulte [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** atldb.h  
  
## <a name="see-also"></a>Consulte também  
 [Macros para modelos de provedor do OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Modelos de provedor do OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitetura do modelo de provedor do OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Criando um provedor do OLE DB](../../data/oledb/creating-an-ole-db-provider.md)