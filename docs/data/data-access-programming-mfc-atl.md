---
title: Acesso a dados (MFC / ATL) de programação | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], data access applications
- databases [C++], MFC
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: def97b2c-b5a6-445f-afeb-308050fd4852
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3932c4bfb8bdc1700db8e41c60a0b25cdf31fc79
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078174"
---
# <a name="data-access-programming-mfcatl"></a>Programação de acesso a dados (MFC/ATL)

Ao longo dos anos, o Visual C++ forneceu várias maneiras de trabalhar com bancos de dados. Em 2011, a Microsoft anunciou que ele estaria se alinhando com ODBC como a tecnologia preferencial para acessar produtos do SQL Server de código nativo. O ODBC é um padrão do setor e, ao usá-lo, você obtém o máximo de portabilidade de código em várias plataformas e fontes de dados. A maioria dos produtos de banco de dados SQL e muitos produtos NoSQL dão suporte ao ODBC. Você pode usar o ODBC diretamente, chamando as APIs de ODBC de nível inferior, ou você pode usar as classes wrapper de ODBC do MFC ou em uma biblioteca wrapper de C++ de terceiros.

A OLE DB é uma API de nível baixo e alto desempenho com base na especificação COM e só tem suporte no Windows. Use a OLE DB se seu programa estiver acessando [servidores vinculados](/sql/relational-databases/linked-servers/linked-servers-database-engine). A ATL fornece modelos de OLE DB que facilitam a criação de consumidores e provedores OLE DB personalizados. A versão mais recente da OLE DB é fornecida no SQL Native Client 11.

Se seu aplicativo herdado usa a OLE DB ou a interface ADO de nível mais alto para se conectar ao SQL Server e você não está acessando servidores vinculados, você deve considerar a migração para o ODBC em um futuro próximo. Se você não precisa de portabilidade multiplataforma ou dos recursos mais recentes do SQL Server, você pode usar o Provedor Microsoft OLE DB para ODBC (MSDASQL).  O MSDASQL permite que os aplicativos que são criados com base em OLE DB e ADO (que usa internamente OLEDB) acessem fontes de dados por meio de um driver ODBC. Assim como acontece com qualquer camada de translação, o MSDASQL pode afetar o desempenho do banco de dados. Você deve testar para determinar se o impacto é significativo para seu aplicativo. O MSDASQL é fornecido com o sistema operacional Windows e o Windows Server 2008 e Windows Vista SP1 são as primeira versões a incluir uma versão de 64 bits da tecnologia.

O componente SNAC (SQL Native Client), que empacota os drivers OLE DB e ODBC em uma única DLL, foi preterido para aplicativos ODBC. A versão do SQL Server 2012 do SNAC (SQLNCLI11.DLL) é fornecida com o SQL Server 2016 porque os outros componentes do SQL Server dependem dele. No entanto, os novos aplicativos de C++ que se conectam ao SQL Server ou ao Banco de Dados SQL do Azure por meio de ODBC devem usar [o driver ODBC mais recente](https://docs.microsoft.com/sql/connect/odbc/download-odbc-driver-for-sql-server). Para obter mais informações, consulte [Programação do SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client-programming)

Se você usa C++/CLI, você pode continuar a usar o ADO.NET como sempre. Para obter mais informações, consulte [Acesso a dados usando ADO.NET (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md) e [Acesso a dados no Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio).

- Além das classes wrapper de ODBC, o MFC também fornece as classes wrapper de DAO (Objetos de Acesso a Dados) para se conectar aos bancos de dados do Access.  No entanto, o DAO está obsoleto. Qualquer código com base em CDaoDatabase ou CDaoRecordset deve ser atualizado.

Para obter mais informações sobre o histórico de tecnologias de acesso a dados no Microsoft Windows, consulte [Microsoft Data Access Components (Wikipédia)](https://en.wikipedia.org/wiki/Microsoft_Data_Access_Components).

## <a name="see-also"></a>Consulte também

[Acesso a dados](data-access-in-cpp.md)<br/>
[Microsoft ODBC (Open Database Connectivity)](https://docs.microsoft.com/sql/odbc/microsoft-open-database-connectivity-odbc)<br/>
[Roteiro das tecnologias de acesso a dados](https://msdn.microsoft.com/library/ms810810.aspx)