---
title: Classe IRowsetUpdateImpl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
- SetData
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- GetOriginalData
- ATL::IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetPendingRows
- GetPendingRows
- IRowsetUpdateImpl.GetPendingRows
- ATL::IRowsetUpdateImpl::GetPendingRows
- ATL.IRowsetUpdateImpl.GetPendingRows
- ATL.IRowsetUpdateImpl.GetRowStatus
- IRowsetUpdateImpl::GetRowStatus
- IRowsetUpdateImpl.GetRowStatus
- ATL::IRowsetUpdateImpl::GetRowStatus
- GetRowStatus
- ATL.IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
- SetData method
- GetOriginalData method
- GetPendingRows method
- GetRowStatus method
- Undo method
- Update method
- IsUpdateAllowed method
- m_mapCachedData
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f13da3ed0b1f2193ab86e1644d401a6e4fb6b942
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49082840"
---
# <a name="irowsetupdateimpl-class"></a>Classe IRowsetUpdateImpl

A implementação de modelos OLE DB do [IRowsetUpdate](/previous-versions/windows/desktop/ms714401) interface.  
  
## <a name="syntax"></a>Sintaxe

```cpp
template <  
   class T,   
   class Storage,   
   class UpdateArray = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>   
>  

class IRowsetUpdateImpl : public IRowsetChangeImpl<  
   T,   
   Storage,   
   IRowsetUpdate,   
   RowClass,   
   MapClass>  
```  
  
### <a name="parameters"></a>Parâmetros  

*T*<br/>
Uma classe derivada de `IRowsetUpdateImpl`.  
  
*Armazenamento*<br/>
O registro do usuário.  
  
*UpdateArray*<br/>
Uma matriz que contém os dados armazenados em cache para atualizar o conjunto de linhas.  
  
*RowClass*<br/>
A unidade de armazenamento para o `HROW`.  
  
*MapClass*<br/>
A unidade de armazenamento para todos os identificadores de linha mantidos pelo provedor.  

## <a name="requirements"></a>Requisitos  

**Cabeçalho:** atldb.h  
  
## <a name="members"></a>Membros  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Métodos de interface (usados com IRowsetChange)  
  
|||  
|-|-|  
|[SetData](#setdata)|Define valores de dados em uma ou mais colunas.|  
  
### <a name="interface-methods-used-with-irowsetupdate"></a>Métodos de interface (usados com IRowsetUpdate)  
  
|||  
|-|-|  
|[GetOriginalData](#getoriginaldata)|Obtém os dados transmitidos para mais recentemente ou obtidos da fonte de dados, ignorando as alterações pendentes.|  
|[GetPendingRows](#getpendingrows)|Retorna uma lista de linhas com alterações pendentes.|  
|[GetRowStatus](#getrowstatus)|Retorna o status de linhas especificados.|  
|[Desfazer](#undo)|Desfaz todas as alterações para a linha desde a última busca ou atualização.|  
|[Atualizar](#update)|Transmite todas as alterações feitas na linha desde a última busca ou atualização.|  
  
### <a name="implementation-methods-callback"></a>Métodos de implementação (retorno de chamada)  
  
|||  
|-|-|  
|[IsUpdateAllowed](#isupdateallowed)|Usado para verificar a segurança, integridade, e assim por diante antes de permitir atualizações.|  
  
### <a name="data-members"></a>Membros de Dados  
  
|||  
|-|-|  
|[m_mapCachedData](#mapcacheddata)|Contém os dados originais para a operação adiada.|  
  
## <a name="remarks"></a>Comentários  

Primeiro, você deve ler e entender a documentação [IRowsetChange](/previous-versions/windows/desktop/ms715790), porque tudo descritos lá também se aplica aqui. Você também deve ler o capítulo 6 a *referência do programador DB OLE* sobre a definição de dados.  
  
`IRowsetUpdateImpl` implementa o OLE DB `IRowsetUpdate` interface, que permite que os consumidores atrasar a transmissão das alterações feitas com `IRowsetChange` para os dados de origem e desfazer as alterações antes da transmissão.  
  
> [!IMPORTANT]
>  É altamente recomendável que você leia a documentação a seguir antes de tentar implementar seu provedor:  
  
- [Criando um provedor atualizável](../../data/oledb/creating-an-updatable-provider.md)  
  
- Capítulo 6 a *referência do programador do OLE DB*  
  
- Consulte também como o `RUpdateRowset` classe é usada em de [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) exemplo  

## <a name="setdata"></a> Irowsetupdateimpl:: SetData

Define valores de dados em uma ou mais colunas.  
  
### <a name="syntax"></a>Sintaxe  
  
```cpp
STDMETHOD (SetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData);  
```  
  
#### <a name="parameters"></a>Parâmetros  

Ver [IRowsetChange:: SetData](/previous-versions/windows/desktop/ms721232) na *referência do programador do OLE DB*.  
  
### <a name="remarks"></a>Comentários  

Esse método substitui o [irowsetchangeimpl:: SetData](../../data/oledb/irowsetchangeimpl-setdata.md) método, mas inclui o cache de dados originais a fim de Permitir processamento imediato ou adiado da operação.

## <a name="getoriginaldata"></a> Irowsetupdateimpl:: Getoriginaldata

Obtém os dados transmitidos para mais recentemente ou obtidos da fonte de dados, ignorando as alterações pendentes.  
  
### <a name="syntax"></a>Sintaxe  
  
```cpp
STDMETHOD (GetOriginalData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pData);  
```  
  
#### <a name="parameters"></a>Parâmetros  

Ver [IRowsetUpdate::GetOriginalData](/previous-versions/windows/desktop/ms709947) na *referência do programador do OLE DB*.   

## <a name="getpendingrows"></a> Irowsetupdateimpl:: Getpendingrows

Retorna uma lista de linhas com alterações pendentes.  
  
### <a name="syntax"></a>Sintaxe  
  
```cpp
STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,  
   DBPENDINGSTATUS dwRowStatus,  
   DBCOUNTITEM* pcPendingRows,  
   HROW** prgPendingRows,  
   DBPENDINGSTATUS** prgPendingStatus);  
```  
  
#### <a name="parameters"></a>Parâmetros  

*hReserved*<br/>
[in] Corresponde do *hChapter* parâmetro na [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626).  
  
Para outros parâmetros, consulte [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626) na *referência do programador DB OLE*.  
  
### <a name="remarks"></a>Comentários  

Para obter mais informações, consulte [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626) na *referência do programador DB OLE*.  

## <a name="getrowstatus"></a> Irowsetupdateimpl:: Getrowstatus

Retorna o status de linhas especificados.  
  
### <a name="syntax"></a>Sintaxe  
  
```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBPENDINGSTATUS rgPendingStatus[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  

*hReserved*<br/>
[in] Corresponde do *hChapter* parâmetro na [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377).  
  
Para outros parâmetros, consulte [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377) na *referência do programador DB OLE*.  

## <a name="undo"></a> Irowsetupdateimpl:: Undo

Desfaz todas as alterações para a linha desde a última busca ou atualização.  
  
### <a name="syntax"></a>Sintaxe  
  
```cpp
STDMETHOD (Undo )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[ ],  
   DBCOUNTITEM* pcRowsUndone,  
   HROW** prgRowsUndone,  
   DBROWSTATUS** prgRowStatus);  
```  
  
#### <a name="parameters"></a>Parâmetros  

*hReserved*<br/>
[in] Corresponde do *hChapter* parâmetro na [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655).  
  
*pcRowsUndone*<br/>
[out] Corresponde do *pcRows* parâmetro na [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655).  
  
*prgRowsUndone*<br/>
[in] Corresponde do *prgRows* parâmetro na [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655).  
  
Para outros parâmetros, consulte [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655) na *referência do programador DB OLE*. 

## <a name="update"></a> Irowsetupdateimpl:: Update

Transmite todas as alterações feitas na linha desde a última busca ou atualização.  
  
### <a name="syntax"></a>Sintaxe  
  
```cpp
STDMETHOD (Update )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBCOUNTITEM* pcRows,  
   HROW** prgRows,  
   DBROWSTATUS** prgRowStatus);  
```  
  
#### <a name="parameters"></a>Parâmetros  

*hReserved*<br/>
[in] Corresponde do *hChapter* parâmetro na [IRowsetUpdate:: Update](/previous-versions/windows/desktop/ms719709).  
  
Para outros parâmetros, consulte [IRowsetUpdate:: Update](/previous-versions/windows/desktop/ms719709) na *referência do programador DB OLE*.  
  
### <a name="remarks"></a>Comentários  

As alterações são transmitidas por meio da chamada [irowsetchangeimpl:: Flushdata](../../data/oledb/irowsetchangeimpl-flushdata.md). O consumidor deve chamar [crowset:: Update](../../data/oledb/crowset-update.md) para que as alterações entrem em vigor. Definir *prgRowstatus* para um valor apropriado, conforme descrito em [estados de linha](/previous-versions/windows/desktop/ms722752) no *referência do programador DB OLE*. 
  
## <a name="isupdateallowed"></a> Irowsetupdateimpl:: Isupdateallowed

Substitua este método para verificar a segurança, integridade, e assim por diante antes das atualizações.  
  
### <a name="syntax"></a>Sintaxe  
  
```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,  
   HROW /* [in] */ /* hRowUpdate */,  
   DBROWSTATUS* /* [out] */ /* pRowStatus */);  
```  
  
#### <a name="parameters"></a>Parâmetros  

*status*<br/>
[in] O status de operações nas linhas pendentes.  
  
*hRowUpdate*<br/>
[in] Identificador para as linhas que o usuário deseja atualizar.  
  
*pRowStatus*<br/>
[out] O status retornado para o usuário.  
  
### <a name="remarks"></a>Comentários  

Se você determinar que uma atualização deve ser permitida, Retorna S_OK; Caso contrário, retornará E_FAIL. Se você permitir que uma atualização, você também precisa definir a `DBROWSTATUS` na [irowsetupdateimpl:: Update](../../data/oledb/irowsetupdateimpl-update.md) com um número apropriado [estado de linha](/previous-versions/windows/desktop/ms722752).  

## <a name="mapcacheddata"></a> Irowsetupdateimpl:: M_mapcacheddata

Um mapa que contém os dados originais para a operação adiada.  
  
### <a name="syntax"></a>Sintaxe  
  
```cpp
CAtlMap<   
   HROW hRow,    
   Storage* pData   
>   
m_mapCachedData;  
```  
  
#### <a name="parameters"></a>Parâmetros  

*hRow*<br/>
Identificador para as linhas de dados.  
  
*pData*<br/>
Um ponteiro para os dados sejam armazenados em cache. Os dados são do tipo *armazenamento* (a classe de registro de usuário). Consulte a *armazenamento* argumento de modelo em [classe IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md).  

## <a name="see-also"></a>Consulte também  

[Modelos de provedor do OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitetura de modelo do provedor do OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Criando um provedor atualizável](../../data/oledb/creating-an-updatable-provider.md)