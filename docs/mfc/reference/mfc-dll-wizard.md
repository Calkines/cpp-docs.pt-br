---
title: Assistente de DLL MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.dll.overview
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [MFC], creating
- MFC DLL Wizard
- DLLs [MFC], MFC
- DLL wizard [MFC]
- MFC DLLs [MFC]
- DLLs [MFC], creating
ms.assetid: 4e936031-7e39-4f40-a295-42a09c5ff264
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 721c8ba75fc72879a2c4c7de0f21010f51513f50
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808778"
---
# <a name="mfc-dll-wizard"></a>Assistente de DLL MFC

Quando você usa o Assistente de DLL do MFC para criar um projeto de DLL do MFC, você obtém um aplicativo de início do trabalho com uma funcionalidade interna que, quando compilado, irá implementar os recursos básicos de um [DLL](../../build/dlls-in-visual-cpp.md). O programa de início do MFC inclui arquivos de origem (. cpp) C++, arquivos de recurso (. rc) e um arquivo de projeto (. vcxproj). O código gerado nesses arquivos starter baseia-se no MFC. Para obter mais informações, consulte os detalhes do arquivo readme. txt que é gerado para o seu projeto no Visual Studio, e [Classes e funções geradas pelo Assistente de DLL do MFC](../../mfc/reference/classes-and-functions-generated-by-the-mfc-dll-wizard.md)

## <a name="overview"></a>Visão geral

Esta página do assistente descreve atual [configurações de aplicativo para o projeto de DLL do MFC](../../mfc/reference/application-settings-mfc-dll-wizard.md) você está criando. Por padrão, o projeto é criado como um projeto de DLL do MFC (MFC compartilhada) regular com nenhuma configuração adicional.

Para alterar esses padrões, clique em **configurações do aplicativo** na coluna à esquerda das alterações assistente e verifique na página do Assistente de DLL do MFC.

Depois de criar um projeto de DLL do MFC, você pode adicionar objetos ou controles ao seu projeto usando o Visual C++ [assistentes de código](../../ide/adding-functionality-with-code-wizards-cpp.md).

Você pode executar as seguintes tarefas e tipos de aprimoramentos para um projeto básico de DLL do MFC:

- [Exportação de uma DLL](../../build/exporting-from-a-dll.md)

- [Vincular um executável a uma DLL](../../build/linking-an-executable-to-a-dll.md)

- [Inicialize um DLL](../../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="see-also"></a>Consulte também

[Criando e gerenciando projetos do Visual C++](../../ide/creating-and-managing-visual-cpp-projects.md)<br/>
[Páginas de propriedade](../../ide/property-pages-visual-cpp.md)<br/>
[Trabalhando com Propriedades do Projeto](../../ide/working-with-project-properties.md)<br/>
[Classe MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Adicionando uma função de membro](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Implementando uma interface](../../ide/implementing-an-interface-visual-cpp.md)<br/>

