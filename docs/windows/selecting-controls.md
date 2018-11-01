---
title: Selecionando controles
ms.date: 11/04/2016
helpviewer_keywords:
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
ms.assetid: 27f05450-4550-4229-9f4c-2c9e06365596
ms.openlocfilehash: ccef63ae6388f376c4be96a34f2857fcedde0ea9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637093"
---
# <a name="selecting-controls"></a>Selecionando controles

Selecione controles para tamanho, alinhar, mover, copiar, ou excluí-los e, em seguida, executar a operação desejada. Na maioria dos casos, você precisa selecionar mais de um controle para usar as ferramentas de dimensionamento e o alinhamento a [barra de ferramentas do Editor de caixa de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).

Quando um controle for selecionado, ele tem uma borda sombreada em torno dele com sólida (ativa) ou vazios (inativo) "alças de dimensionamento" pequenos quadrados que aparecem na borda de seleção. Quando vários controles estiverem selecionados, o controle dominante tem alças de dimensionamento sólida; todos os outros controles selecionados tem alças de dimensionamento vazado.

Quando você estiver dimensionando ou alinhar vários controles, o **caixa de diálogo** editor usa o "controle dominante" para determinar como os outros controles são dimensionados ou alinhados. Por padrão, o controle dominante é o primeiro controle selecionado.

- [Selecionando vários controles](../windows/selecting-multiple-controls.md)

- [Especificando o controle dominante](../windows/specifying-the-dominant-control.md)

Para obter informações sobre como adicionar recursos a projetos gerenciados, consulte [recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index) na *guia do desenvolvedor do .NET Framework*. Para obter informações sobre como adicionar manualmente os arquivos de recursos a projetos gerenciados, acessar recursos, exibir recursos estáticos e atribuir cadeias de caracteres de recurso a propriedades, consulte [criando arquivos de recursos para aplicativos de área de trabalho](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obter informações sobre globalização e localização de recursos em aplicativos gerenciados, consulte [Globalizing e Localizando aplicativos do .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte também

[Controles em caixas de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles](../mfc/controls-mfc.md)