---
title: Interfaces (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 5416fb8a99420f0f6c84318753ee3399ccf5db2a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287369"
---
# <a name="interfaces-atl"></a>Interfaces (ATL)

Uma interface é a maneira na qual um objeto exponha sua funcionalidade para o mundo exterior. No COM, uma interface é uma tabela de ponteiros (como uma vtable C++) para funções implementadas pelo objeto. A tabela representa a interface e as funções para o qual ele aponta são os métodos dessa interface. Um objeto pode expor quantas interfaces conforme ele escolhe.

Cada interface é baseada na interface COM fundamental, [IUnknown](../atl/iunknown.md). Os métodos de `IUnknown` permitem a navegação para outras interfaces expostas pelo objeto.

Além disso, cada interface é fornecida uma interface exclusiva IID (ID). Este exclusividade torna fácil para dar suporte a controle de versão da interface. Uma nova versão de uma interface é simplesmente uma nova interface, com uma IID de novo.

> [!NOTE]
>  IIDs para interfaces COM e OLE padrão são predefinidos.

## <a name="see-also"></a>Consulte também

[Introdução a COM](../atl/introduction-to-com.md)<br/>
[Interfaces e objetos COM](/windows/desktop/com/com-objects-and-interfaces)
