---
title: Automação em um DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], Automation
- Automation [C++], DLLs
ms.assetid: 2728ecd1-14e2-4ae0-a946-e749e11dbb74
ms.openlocfilehash: dedc832d6726dccf8c0c2e88f9f4d5c67590c1c2
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220926"
---
# <a name="automation-in-a-dll"></a>Automação em um DLL

Quando você escolhe a opção de automação no Assistente de DLL do MFC, o assistente fornece o seguinte:

- Uma linguagem de descrição do objeto inicial (. Arquivo ODL)

- Uma diretiva de inclusão no arquivo Stdafx. h para Afxole.h

- Uma implementação de `DllGetClassObject` função, que chama o **AfxDllGetClassObject** função

- Uma implementação de `DllCanUnloadNow` função, que chama o **AfxDllCanUnloadNow** função

- Uma implementação de `DllRegisterServer` função, que chama o [COleObjectFactory::UpdateRegistryAll](../mfc/reference/coleobjectfactory-class.md#updateregistryall) função

## <a name="what-do-you-want-to-know-more-about"></a>Que mais você deseja saber?

- [Servidores de automação](../mfc/automation-servers.md)

## <a name="see-also"></a>Consulte também

[Criar DLLs de C/C++ no Visual Studio](dlls-in-visual-cpp.md)
