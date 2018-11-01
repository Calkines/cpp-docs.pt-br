---
title: Transação (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets [C++], updating
- transactions [C++], MFC ODBC classes
- ODBC [C++], transactions
- recordsets [C++], updating
- databases [C++], transactions
- recordsets [C++], transactions
- ODBC recordsets [C++], transactions
ms.assetid: a2ec0995-2029-45f2-8092-6efd6f2a77f4
ms.openlocfilehash: 0deb21a43ff17ca94efe29bdec37db7611331a86
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615807"
---
# <a name="transaction-odbc"></a>Transação (ODBC)

Este tópico se aplica às classes ODBC do MFC.

Uma transação é uma maneira de agrupar, ou um lote, uma série de atualizações para um [fonte de dados](../../data/odbc/data-source-odbc.md) para que todos são confirmados ao mesmo tempo ou nenhum são confirmadas se você reverter a transação. Se você não usar uma transação, as alterações na fonte de dados são confirmadas automaticamente, em vez de confirmação sob demanda.

> [!NOTE]
>  Nem todos os drivers de banco de dados ODBC suportam a transações. Chame o `CanTransact` função de membro de seu [CDatabase](../../mfc/reference/cdatabase-class.md) ou [CRecordset](../../mfc/reference/crecordset-class.md) objeto para determinar se o driver dá suporte a transações para um determinado banco de dados. Observe que `CanTransact` não informa se a fonte de dados fornece suporte de transação completa. Você também deve chamar `CDatabase::GetCursorCommitBehavior` e `CDatabase::GetCursorRollbackBehavior` após `CommitTrans` e `Rollback` para verificar o efeito da transação na abertura `CRecordset` objeto.

Chamadas para o `AddNew` e `Edit` funções de membro de uma `CRecordset` afetam os dados de origem imediatamente quando você chama do objeto `Update`. `Delete` chamadas também entram em vigor imediatamente. Por outro lado, você pode usar uma transação consiste em várias chamadas para `AddNew`, `Edit`, `Update`, e `Delete`, que são executadas, mas não foi confirmada até que você chame `CommitTrans` explicitamente. Estabelecendo uma transação, você pode executar uma série dessas chamadas, mantendo a capacidade de revertê-los. Se um recurso crítico não está disponível ou outra condição impede que toda a transação seja concluída, você pode reverter a transação em vez de confirmá-lo. Nesse caso, nenhuma das alterações que pertencem à transação afeta a fonte de dados.

> [!NOTE]
>  Atualmente, a classe `CRecordset` não oferece suporte a atualizações para a fonte de dados se você tiver implementado a busca de linhas em massa. Isso significa que você não pode fazer chamadas para `AddNew`, `Edit`, `Delete`, ou `Update`. No entanto, você pode escrever funções próprias para executar atualizações e, em seguida, chamar essas funções dentro de uma determinada transação. Para obter mais informações sobre a busca de linhas em massa, consulte [conjunto de registros: buscando registros em massa (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
>  Além de afetar seu conjunto de registros, as transações afetam instruções SQL que você execute diretamente desde que você use o ODBC **HDBC** associado com seus `CDatabase` objeto ou um ODBC **HSTMT** com base em que **HDBC**.

As transações são particularmente úteis quando você tem vários registros que devem ser atualizados ao mesmo tempo. Nesse caso, você deseja evitar uma transação concluída de metade, tais como pode acontecer se uma exceção foi lançada antes da última atualização foi feita. Agrupar essas atualizações em uma transação permite uma recuperação (reversão) das alterações e retorna os registros para o estado anterior à transação. Por exemplo, se um banco transfere dinheiro de uma conta para a conta B, tanto a retirada de A e o depósito em B deve ser bem-sucedidas para processar os fundos corretamente ou a transação inteira falhará.

As classes de banco de dados, você executa transações por meio de `CDatabase` objetos. Um `CDatabase` objeto representa uma conexão a uma fonte de dados e um ou mais conjuntos de registros associados a esse `CDatabase` objeto opera em tabelas do banco de dados por meio de funções de membro do conjunto de registros.

> [!NOTE]
>  Há suporte para apenas um nível de transações. Você não pode aninhar transações, nem pode abranger de uma transação de vários objetos de banco de dados.

Os tópicos a seguir fornecem mais informações sobre como as transações são executadas:

- [Transação: realizando uma transação em um conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)

- [Transação: como as transações afetam atualizações (ODBC)](../../data/odbc/transaction-how-transactions-affect-updates-odbc.md)

## <a name="see-also"></a>Consulte também

[ODBC (conectividade de banco de dados aberto)](../../data/odbc/open-database-connectivity-odbc.md)