---
title: Pooling de recursos e serviços de banco de dados OLE
ms.date: 10/29/2018
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
ms.openlocfilehash: f46c6f493ae41570c75c384fcc836707faeab99f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023744"
---
# <a name="ole-db-resource-pooling-and-services"></a>Pooling de recursos e serviços de banco de dados OLE

Para funcionar bem com o pool de banco de dados OLE ou com qualquer serviço do OLE DB, seu provedor deve oferecer suporte a agregação de todos os objetos. Esse é um requisito de qualquer 1.5 do OLE DB ou o provedor mais recente. É fundamental para aproveitar os serviços. Provedores que não dão suporte a agregação não podem ser agrupadas e não há serviços adicionais são fornecidos.

Para ser colocado em pool, os provedores devem oferecer suporte a modelo de thread livre. O pool de recursos determina o modelo de thread do provedor de acordo com a propriedade DBPROP_THREADMODEL.

Se o provedor tem um estado de conexão global que podem ser alterados enquanto a fonte de dados está em um estado inicializado, ele deve dar suporte a nova propriedade DBPROP_RESETDATASOURCE. Essa propriedade é chamada antes que uma conexão é reutilizado e fornece o provedor a oportunidade para limpar o estado antes de seu próximo uso. Se o provedor não é possível limpar em algum estado associado a conexão, ele pode retornar DBPROPSTATUS_NOTSETTABLE para a propriedade e a conexão não será reutilizada.

Provedores que se conectar a um banco de dados remoto e podem detectar se essa conexão pode ser perdido devem dar suporte a propriedade DBPROP_CONNECTIONSTATUS. Esta propriedade fornece serviços de OLE DB a capacidade de detectar conexões inativas e certifique-se de que eles não são retornados ao pool.

Por fim, a inscrição automática de transação geralmente não funciona, a menos que ele é implementado no mesmo nível que pooling ocorre. Provedores que dão suporte a inscrição automática de transação devem dar suporte a desabilitar esta inscrição expondo a propriedade DBPROP_INIT_OLEDBSERVICES e desabilitar a inscrição, se o DBPROPVAL_OS_TXNENLISTMENT está desmarcada.

## <a name="see-also"></a>Consulte também

[Técnicas de provedor avançadas](../../data/oledb/advanced-provider-techniques.md)