---
title: "IColumnsInfoImpl::GetColumnInfo | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetColumnInfo"
  - "ATL::IColumnsInfoImpl::GetColumnInfo"
  - "ATL.IColumnsInfoImpl.GetColumnInfo"
  - "ATL::IColumnsInfoImpl<T>::GetColumnInfo"
  - "IColumnsInfoImpl::GetColumnInfo"
  - "IColumnsInfoImpl<T>::GetColumnInfo"
  - "IColumnsInfoImpl.GetColumnInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Método GetColumnInfo"
ms.assetid: a6739a39-7402-496a-b544-a5b1ed05fadf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IColumnsInfoImpl::GetColumnInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Retorna os metadados da coluna necessários para a maioria dos consumidores.  
  
## Sintaxe  
  
```  
  
      STDMETHOD (GetColumnInfo)(  
   DBORDINAL* pcColumns,  
   DBCOLUMNINFO** prgInfo,  
   OLECHAR** ppStringsBuffer   
);  
```  
  
#### Parâmetros  
 Consulte [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx)*na referência do programador de OLE DB*.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Consulte também  
 [Classe IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)   
 [IColumnsInfoImpl::MapColumnIDs](../../data/oledb/icolumnsinfoimpl-mapcolumnids.md)