---
title: Troca de dados para exibições de registro (Acesso a dados MFC)
ms.date: 11/19/2018
helpviewer_keywords:
- RFX (record field exchange), data exchange mechanism
- RFX (record field exchange), record views
- record views, data exchange
- DDX (dialog data exchange), record views
- RFX (record field exchange)
ms.assetid: abc52ca7-6997-47a7-98f3-f347f52b1f72
ms.openlocfilehash: a7c6714218b5891e078e750a974faed274e113c9
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023588"
---
# <a name="data-exchange-for-record-views---mfc-data-access"></a>Troca de dados para exibições de registro (Acesso a dados MFC)

Quando você usa [Adicionar classe](../mfc/reference/adding-an-mfc-odbc-consumer.md) para mapear os controles no recurso de modelo de caixa de diálogo de uma exibição do registro para os campos de um conjunto de registros, a estrutura gerencia a troca de dados em ambas as direções — de conjunto de registros para controles e dos controles para o conjunto de registros. O uso do mecanismo DDX significa que você não precisa escrever o código para transferir os dados de um para outro lado por conta própria.

DDX para exibições de registro funciona em conjunto com [RFX](../data/odbc/record-field-exchange-rfx.md) para conjuntos de registros de classe `CRecordset` (ODBC).  RFX move dados entre o registro atual da fonte de dados e os membros de dados do campo de um objeto recordset. DDX move os dados de membros de dados de campo para os controles no formulário. Essa combinação preenche os controles do formulário inicialmente e conforme o usuário é movido de registro em registro. Ela também pode mover dados atualizados de volta ao conjunto de registros e, em seguida, para a fonte de dados.

A figura a seguir mostra a relação entre DDX e RFX para exibições de registro.

![Caixa de diálogo&#45;troca de dados e de registro&#45;a troca de campos](../data/media/vc37xt1.gif "caixa de diálogo&#45;registro e troca de dados&#45;a troca de campos")<br/>
Troca de dados de diálogo e troca de campos de registro

Para obter mais informações sobre DDX, consulte [troca de dados de caixa de diálogo e validação](../mfc/dialog-data-exchange-and-validation.md). Para obter mais informações sobre RFX, consulte [Exchange RFX (Record Field)](../data/odbc/record-field-exchange-rfx.md).

## <a name="see-also"></a>Consulte também

[Exibição de registro (Acesso a dados MFC)](../data/record-views-mfc-data-access.md)<br/>
[Lista de drivers ODBC](../data/odbc/odbc-driver-list.md)