---
title: Exibindo e adicionando controles ActiveX a uma caixa de diálogo (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.controls.activex
helpviewer_keywords:
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
ms.openlocfilehash: 947318fb9f628c1184398c039c9697128b09c869
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642501"
---
# <a name="viewing-and-adding-activex-controls-to-a-dialog-box-c"></a>Exibindo e adicionando controles ActiveX a uma caixa de diálogo (C++)

Visual Studio permite que você inserir controles ActiveX em sua caixa de diálogo.

### <a name="to-see-the-activex-controls-you-have-available"></a>Para ver os controles ActiveX que estão disponíveis

1. Abra uma caixa de diálogo no editor de caixa de diálogo.

2. Clique com botão direito em qualquer lugar no corpo da caixa de diálogo.

3. No menu de atalho, clique em **Inserir controle ActiveX**.

   O [caixa de diálogo Inserir controle ActiveX](../windows/insert-activex-control-dialog-box.md) é exibida, mostrando todos os controles ActiveX em seu sistema. Na parte inferior da caixa de diálogo, o caminho para o arquivo de controle ActiveX é exibida.

### <a name="to-add-an-activex-control-to-a-dialog-box"></a>Para adicionar um controle ActiveX a uma caixa de diálogo

1. No [caixa de diálogo Inserir controle ActiveX](../windows/insert-activex-control-dialog-box.md), selecione o controle que você deseja adicionar à sua caixa de diálogo e clique em **Okey**.

   O controle aparece na caixa de diálogo onde você pode editá-lo ou criar manipuladores para ele como faria qualquer outro controle.

   > [!NOTE]
   > Você pode adicionar controles ActiveX para o [janela caixa de ferramentas](/visualstudio/ide/reference/toolbox).

   > [!CAUTION]
   > Ele pode não ser legal para distribuir todos os controles ActiveX em seu sistema. Consulte o contrato de licença para softwares que instalados os controles ou entre em contato com a empresa de software.

   Você pode colocar controles na **caixa de ferramentas** janela para facilitar o acesso. Para saber mais, confira [Caixa de Ferramentas](/visualstudio/ide/reference/toolbox).

Para obter informações sobre como adicionar recursos a projetos gerenciados, consulte [recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index) na *guia do desenvolvedor do .NET Framework*. Para obter informações sobre como adicionar manualmente os arquivos de recursos a projetos gerenciados, acessar recursos, exibir recursos estáticos e atribuir cadeias de caracteres de recurso a propriedades, consulte [criando arquivos de recursos para aplicativos de área de trabalho](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obter informações sobre globalização e localização de recursos em aplicativos gerenciados, consulte [Globalizing e Localizando aplicativos do .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte também

[Controles em caixas de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles ActiveX do MFC](../mfc/mfc-activex-controls.md)<br/>
[Contêineres de controle ActiveX](../mfc/activex-control-containers.md)