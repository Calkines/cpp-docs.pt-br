---
title: db_table (C++ COM atributo)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_table
helpviewer_keywords:
- db_table attribute
ms.assetid: ff9eb957-4e6d-4175-afcc-fd8ea916cec0
ms.openlocfilehash: 3ab548261d6ebcb9d3d7f7e352c8afe3b33db06f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148114"
---
# <a name="dbtable"></a>db_table

Abre uma tabela de OLE DB.

## <a name="syntax"></a>Sintaxe

```cpp
[ db_table(db_table, name, source_name, hresult) ]
```

#### <a name="parameters"></a>Parâmetros

*db_table*<br/>
Uma cadeia de caracteres especificando o nome de uma tabela de banco de dados (por exemplo, "produtos").

*name*<br/>
(Opcional) O nome do identificador que você usa para trabalhar com a tabela. Você deve especificar esse parâmetro se você quiser retornar mais de uma linha de resultados. **db_table** gera uma variável com o especificado *nome* que pode ser usado para percorrer o conjunto de linhas ou executar várias consultas de ação.

*source_name*<br/>
(Opcional) O `CSession` variável ou instância de uma classe que tem o `db_source` atributo aplicado a ele no qual o comando é executado. Ver [db_source](db-source.md).

*hresult*<br/>
(Opcional) Identifica a variável que receberá o HRESULT desse comando de banco de dados. Se a variável não existir, ele será automaticamente injetado pelo atributo.

## <a name="remarks"></a>Comentários

**db_table** cria um [CTable](../../data/oledb/ctable-class.md) objeto, que é usado por um consumidor OLE DB para abrir uma tabela. Você pode usar esse atributo apenas no nível de classe; Você não pode usá-lo embutido. Use `db_column` para associar colunas de tabela para variáveis; use `db_param` delimitar (define o tipo de parâmetro e, portanto, em) de parâmetros.

Quando o provedor do consumidor de atributo se aplica a esse atributo a uma classe, o compilador renomeará a classe \_ *YourClassName*acessador, onde *YourClassName* é o nome que você deu a classe e o compilador também criará uma classe chamada *YourClassName*, que é derivada de \_ *YourClassName*acessador.  No modo de exibição de classe, você verá as duas classes.

## <a name="example"></a>Exemplo

O exemplo a seguir abre a tabela de produtos para uso por `CProducts`.

```cpp
// db_table.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_table(L"dbo.Products") ]
class CProducts {
   [ db_column("1") ] LONG m_ProductID;
};
```

Para obter um exemplo desse atributo usado em um aplicativo, consulte os exemplos [AtlAgent](https://github.com/Microsoft/VCSamples) e [MultiRead](https://github.com/Microsoft/VCSamples).

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Atributo de contexto

|||
|-|-|
|**Aplica-se a**|**class**, **struct**|
|**Repetível**|Não|
|**Atributos obrigatórios**|Nenhum|
|**Atributos inválidos**|Nenhum|

Para obter mais informações sobre os contextos de atributo, consulte [contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte também

[Atributos de consumidor do OLE DB](ole-db-consumer-attributes.md)
