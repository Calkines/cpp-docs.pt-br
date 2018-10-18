---
title: Classes geradas pelo Assistente do consumidor | Microsoft Docs
ms.custom: ''
ms.date: 10/15/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attribute-injected classes and methods
- wizard-generated classes and methods
- OLE DB consumers, wizard-generated classes and methods
- command classes in OLE DB consumer
- classes [C++], OLE DB Consumer Wizard-generated
- consumer wizard-generated classes and methods
- user record classes in OLE DB consumer
ms.assetid: dba0538f-2afe-4354-8cbb-f202ea8ade5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a7498f15072f3b9687476ba7f6c291ebf5ff88cd
ms.sourcegitcommit: db6b2ad3195e71abfb60b62f3f015f08b0a719d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410767"
---
# <a name="consumer-wizard-generated-classes"></a>Classes geradas pelo Assistente do Consumidor

Quando você usa o **ATL OLE DB Assistente de consumidor** para gerar um consumidor, você tem a opção de usar atributos de modelos OLE DB ou OLE DB. Em ambos os casos, o assistente gera uma classe de comando e uma classe de registro de usuário. A classe de comando contém código para abrir a fonte de dados e o conjunto de linhas que você especificou no assistente. A classe de registro de usuário contém um mapa de coluna para a tabela de banco de dados que você selecionou. No entanto, o código gerado é diferente em cada caso:  
  
- Se você selecionar um consumidor de modelo, o assistente gera uma classe de comando e uma classe de registro de usuário. A classe de comando terá o nome que você insere na **classe** caixa no Assistente (por exemplo, `CProducts`), e a classe de registro de usuário terá um nome no formato "*ClassName*acessador" (por exemplo, `CProductsAccessor`). Ambas as classes são colocadas no arquivo de cabeçalho do consumidor.  
  
- Se você selecionar um consumidor atribuído, a classe de registro de usuário terá um nome no formato "_*ClassName*acessador" e serão injetados. Ou seja, você poderá exibir apenas a classe de comando no editor de texto; Você só pode exibir a classe de registro de usuário como o código injetado. Para obter informações sobre como exibir o código injetado, consulte [depurando código injetado](/visualstudio/debugger/how-to-debug-injected-code).  
  
Os exemplos a seguir usam uma classe de comando criada na `Products` tabela do `Northwind` demonstram o código gerado pelo Assistente de consumidor para a classe de comando e a classe de registro de usuário no banco de dados.  
  
## <a name="templated-user-record-classes"></a>Classes de registro do usuário com modelo  

Se você criar um consumidor do OLE DB usando os modelos OLE DB (em vez dos atributos de banco de dados OLE), o assistente gera código conforme descrito nesta seção.  
  
### <a name="column-data-members"></a>Membros de dados de coluna  

A primeira parte da classe de registro de usuário inclui as declarações de membro de dados e os membros de dados de status e o comprimento de cada coluna de associação de dados. Para obter informações sobre esses membros de dados, consulte [membros de dados de Status de campo em acessadores de Wizard-Generated](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).  
  
> [!NOTE]
> Se você modificar a classe de registro de usuário ou escrever seu próprios consumidor, as variáveis de dados devem vir antes das variáveis de status e o comprimento.  
  
> [!NOTE]
> O ATL OLE DB consumidor Wizard usa o `DB_NUMERIC` tipo para associar os tipos de dados numéricos. Ele usado anteriormente `DBTYPE_VARNUMERIC` (o formato que é descrito pelo `DB_VARNUMERIC` tipo; consulte OLEDB). Se você não usar o Assistente para criar os consumidores, é recomendável que você use `DB_NUMERIC`.  
  
```cpp  
// Products.H : Declaration of the CProducts class  
  
class CProductsAccessor  
{  
public:  
   // Column data members:  
   LONG m_ProductID;  
   TCHAR m_ProductName[41];  
   LONG m_SupplierID;  
   LONG m_CategoryID;  
   TCHAR m_QuantityPerUnit[21];  
   CURRENCY m_UnitPrice;  
   SHORT m_UnitsInStock;  
   SHORT m_UnitsOnOrder;  
   SHORT m_ReorderLevel;  
   VARIANT_BOOL m_Discontinued;  
  
   // Column status data members:  
   DBSTATUS m_dwProductIDStatus;  
   DBSTATUS m_dwProductNameStatus;  
   DBSTATUS m_dwSupplierIDStatus;  
   DBSTATUS m_dwCategoryIDStatus;  
   DBSTATUS m_dwQuantityPerUnitStatus;  
   DBSTATUS m_dwUnitPriceStatus;  
   DBSTATUS m_dwUnitsInStockStatus;  
   DBSTATUS m_dwUnitsOnOrderStatus;  
   DBSTATUS m_dwReorderLevelStatus;  
   DBSTATUS m_dwDiscontinuedStatus;  
  
   // Column length data members:  
   DBLENGTH m_dwProductIDLength;  
   DBLENGTH m_dwProductNameLength;  
   DBLENGTH m_dwSupplierIDLength;  
   DBLENGTH m_dwCategoryIDLength;  
   DBLENGTH m_dwQuantityPerUnitLength;  
   DBLENGTH m_dwUnitPriceLength;  
   DBLENGTH m_dwUnitsInStockLength;  
   DBLENGTH m_dwUnitsOnOrderLength;  
   DBLENGTH m_dwReorderLevelLength;  
   DBLENGTH m_dwDiscontinuedLength;  
```  
  
### <a name="rowset-properties"></a>Propriedades do conjunto de linhas  

Em seguida, o assistente define as propriedades do conjunto de linhas. Se você selecionou **alteração**, **inserir**, ou **excluir** em ATL OLE DB consumidor Wizard, as propriedades adequadas são definidas aqui (DBPROP_IRowsetChange é sempre definido, em seguida, um ou mais DBPROPVAL_UP_CHANGE, DBPROPVAL_UP_INSERT e/ou DBPROPVAL_UP_DELETE, respectivamente).  
  
```cpp  
void GetRowsetProperties(CDBPropSet* pPropSet)  
{  
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
}  
```  
  
### <a name="command-or-table-class"></a>Comando ou classe de tabela  

Se você especificar uma classe de comando, o assistente declara a classe de comando; para o código de modelo, o comando tem esta aparência:  
  
```cpp  
DEFINE_COMMAND_EX(CProductsAccessor, L" \  
SELECT \  
   ProductID, \  
   ProductName, \  
   SupplierID, \  
   CategoryID, \  
   QuantityPerUnit, \  
   UnitPrice, \  
   UnitsInStock, \  
   UnitsOnOrder, \  
   ReorderLevel, \  
   Discontinued \  
   FROM dbo.Products")  
```  
  
### <a name="column-map"></a>Mapa de coluna  

O assistente, em seguida, gera as associações de coluna ou um mapa de coluna. Para corrigir vários problemas com alguns provedores, o código a seguir pode associar colunas em uma ordem diferente daquela que relatado pelo provedor.  
  
```  
   BEGIN_COLUMN_MAP(CProductsAccessor)  
      COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(3, m_SupplierID, m_dwSupplierIDLength, m_dwSupplierIDStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(4, m_CategoryID, m_dwCategoryIDLength, m_dwCategoryIDStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(5, m_QuantityPerUnit, m_dwQuantityPerUnitLength, m_dwQuantityPerUnitStatus)  
      _COLUMN_ENTRY_CODE(6, DBTYPE_CY, _SIZE_TYPE(m_UnitPrice), 0, 0, offsetbuf(m_UnitPrice), offsetbuf(m_dwUnitPriceLength), offsetbuf(m_dwUnitPriceStatus))  
      COLUMN_ENTRY_LENGTH_STATUS(7, m_UnitsInStock, m_dwUnitsInStockLength, m_dwUnitsInStockStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(8, m_UnitsOnOrder, m_dwUnitsOnOrderLength, m_dwUnitsOnOrderStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(9, m_ReorderLevel, m_dwReorderLevelLength, m_dwReorderLevelStatus)  
      _COLUMN_ENTRY_CODE(10, DBTYPE_BOOL, _SIZE_TYPE(m_Discontinued), 0, 0, offsetbuf(m_Discontinued), offsetbuf(m_dwDiscontinuedLength), offsetbuf(m_dwDiscontinuedStatus))  
   END_COLUMN_MAP()  
};  
```  
  
### <a name="class-declaration"></a>Declaração de classe  

Por fim, o assistente gera uma declaração de classe como o seguinte comando:  
  
```cpp  
class CProducts : public CCommand<CAccessor<CProductsAccessor>>  
```  
  
## <a name="attribute-injected-user-record-classes"></a>Classes de registro de usuário injetadas por atributos  

Se você criar um consumidor do OLE DB usando os atributos de banco de dados ([db_command](../../windows/db-command.md) ou [db_table](../../windows/db-table.md)), os atributos de injetam uma classe de registro de usuário com um nome no formato "_*ClassName*Acessador. " Por exemplo, se você nomeou sua classe de comando `COrders`, a classe de registro de usuário será `_COrdersAccessor`. Embora a classe de registro de usuário aparece na **modo de exibição de classe**, duas vezes sobre ela navega para a classe de comando ou de tabela no arquivo de cabeçalho. Nesses casos, você só pode exibir a declaração real da classe de registro de usuário exibindo o código injetado de atributo.  
  
Pode haver possíveis complicações se você adicionar ou substituir métodos consumidores atribuído. Por exemplo, você pode adicionar um `_COrdersAccessor` construtor para o `COrders` declaração, mas observe que na verdade isso adiciona um construtor para o injetado `COrdersAccessor` classe. Um construtor pode inicializar os colunas/parâmetros, mas não é possível criar um construtor de cópia dessa forma, porque ele não pode instanciar diretamente o `COrdersAccessor` objeto. Se você precisar de um construtor (ou outro método) diretamente na `COrders` classe, é recomendável que você defina uma nova classe que deriva de `COrders` e adicione os métodos necessários lá.  
  
No exemplo a seguir, o assistente gera uma declaração para a classe `COrders`, mas a classe de registro de usuário `COrdersAccessor` não for exibido, pois os atributos injetá-la.  
  
```cpp  
#define _ATL_ATTRIBUTES  
#include <atlbase.h>  
#include <atldbcli.h>  
[  
   db_source(L"your connection string"),  
   db_command(L"Select ShipName from Orders;")  
]  
class COrders  
{  
public:  
  
   // COrders()            // incorrect constructor name  
   _COrdersAccessor()      // correct constructor name  
   {  
   }  
      [db_column(1) ] TCHAR m_ShipName[41];  
   };  
```  
  
A declaração de classe de comando injetado tem esta aparência:  
  
```  
class CProducts : public CCommand<CAccessor<_CProductsAccessor>>  
```  
  
A maioria do código injetado é igual ou semelhante à versão do modelo. As principais diferenças são no injetado métodos, que são descritos em [Consumer Wizard-Generated métodos](../../data/oledb/consumer-wizard-generated-methods.md).  
  
Para obter informações sobre como exibir o código injetado, consulte [depurando código injetado](/visualstudio/debugger/how-to-debug-injected-code).  
  
## <a name="see-also"></a>Consulte também  

[Criando um consumidor do OLE DB usando um assistente](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)