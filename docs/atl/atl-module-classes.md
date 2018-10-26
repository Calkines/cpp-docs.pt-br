---
title: Classes de módulo ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CComModule class, what's changed
- ATL, module classes
- module classes
ms.assetid: fd75382d-c955-46ba-a38e-37728b7fa00f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e067b1d72b80950b4ed33fbae8cac7333ac0438
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083068"
---
# <a name="atl-module-classes"></a>Classes de módulo ATL

Este tópico discute as classes de módulo que foram introduzidas na ATL 7.0.

## <a name="ccommodule-replacement-classes"></a>Classes de substituição CComModule

Versões anteriores do ATL usado `CComModule`. Na ATL 7.0 `CComModule` funcionalidade é substituída por várias classes:

- [CAtlBaseModule](../atl/reference/catlbasemodule-class.md) contém informações necessárias pela maioria dos aplicativos que usam ATL. Contém o HINSTANCE do módulo e a instância do recurso.

- [CAtlComModule](../atl/reference/catlcommodule-class.md) contém informações necessárias pelas classes COM de ATL.

- [CAtlWinModule](../atl/reference/catlwinmodule-class.md) contém informações necessárias pelas classes de janelas em ATL.

- [CAtlDebugInterfacesModule](../atl/reference/catldebuginterfacesmodule-class.md) contém suporte para depuração de interface.

- [CAtlModule](../atl/reference/catlmodule-class.md) a seguir `CAtlModule`-classes derivadas são personalizadas para conter as informações necessárias em um tipo de aplicativo específico. A maioria dos membros nessas classes podem ser substituídas:

   - [CAtlDllModuleT](../atl/reference/catldllmodulet-class.md) usados em aplicativos de DLL. Fornece código para as exportações padrão.

   - [CAtlExeModuleT](../atl/reference/catlexemodulet-class.md) usado em aplicativos EXE. Fornece o código necessário em um EXE.

   - [CAtlServiceModuleT](../atl/reference/catlservicemodulet-class.md) fornece suporte para criar serviços do Windows 2000 e o Windows NT.

`CComModule` ainda está disponível para compatibilidade com versões anteriores.

## <a name="reasons-for-distributing-ccommodule-functionality"></a>Motivos para a distribuição de funcionalidade CComModule

A funcionalidade de `CComModule` foi distribuído em várias classes novas pelos seguintes motivos:

- Verifique a funcionalidade no `CComModule` granular.

   Suporte para COM, janelas, interface de depuração e recursos específicos do aplicativo (DLL ou EXE) agora está em classes separadas.

- Declare automaticamente a instância global de cada um desses módulos.

   Uma instância global das classes de módulo necessário é vinculada ao projeto.

- Remova a necessidade de chamar métodos Init e termo.

   Métodos Init e o termo foram movidos para os construtores e destruidores para classes de módulo; não é necessário chamar Init e termo.

## <a name="see-also"></a>Consulte também

[Conceitos](../atl/active-template-library-atl-concepts.md)<br/>
[Visão geral da classe](../atl/atl-class-overview.md)

