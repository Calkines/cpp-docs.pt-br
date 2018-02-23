---
title: COLUMN_ENTRY_TYPE_SIZE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- COLUMN_ENTRY_TYPE_SIZE
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_ENTRY_TYPE_SIZE macro
ms.assetid: d8b169e8-af22-464b-8cb3-eaa346f7a739
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f582dd356f90921f0b01a51985f1b199bf08be65
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2018
---
# <a name="columnentrytypesize"></a>COLUMN_ENTRY_TYPE_SIZE
Representa uma associação para a coluna específica no banco de dados. Dá suporte a `type` e `size` parâmetros.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)  
  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `nOrdinal`  
 [in] O número da coluna.  
  
 `wType`  
 [in] Tipo de dados de entrada da coluna.  
  
 `nLength`  
 [in] Tamanho da entrada de coluna em bytes.  
  
 `data`  
 [in] O membro de dados correspondente no registro do usuário.  
  
## <a name="remarks"></a>Comentários  
 Essa macro é uma variante especializada do [COLUMN_ENTRY](../../data/oledb/column-entry.md) macro que fornece um meio de especificar o tamanho dos dados e o tipo.  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** atldbcli.h  
  
## <a name="see-also"></a>Consulte também  
 [Macros e funções globais para modelos de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)