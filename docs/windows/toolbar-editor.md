---
title: Editor de barra de ferramentas (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.toolbar.F1
dev_langs:
- C++
helpviewer_keywords:
- resource editors [C++], Toolbar editor
- editors, toolbars
- toolbars [C++], editing
- Toolbar editor
ms.assetid: aa9f0adf-60f6-4f79-ab05-bc330f15ec43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 273893f5164c4e89b3516c43b5414e5487af376e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063205"
---
# <a name="toolbar-editor-c"></a>Editor de barra de ferramentas (C++)

O **barra de ferramentas** editor permite que você criar recursos de barra de ferramentas do C++ e converter os bitmaps para os recursos da barra de ferramentas. O **barra de ferramentas** editor usa uma exibição gráfica para mostrar uma barra de ferramentas e botões que se assemelhem como eles aparecerão em um aplicativo concluído.

Com o **barra de ferramentas** editor, você pode:

- [Criar novas barras de ferramentas e botões](../windows/creating-new-toolbars.md)

- [Converter bitmaps em recursos da barra de ferramentas](../windows/converting-bitmaps-to-toolbars.md)

- [Criar, mover e editar os botões de barra de ferramentas](../windows/creating-moving-and-editing-toolbar-buttons.md)

- [Criar dicas de ferramenta](../windows/creating-a-tool-tip-for-a-toolbar-button.md)

O **barra de ferramentas** janela do editor mostra dois modos de exibição de uma imagem de botão, o mesmo que a janela do editor de imagem. Uma barra de divisão separa os dois painéis. Você pode arrastar a barra de divisão de um lado para o outro para alterar o tamanho relativo dos painéis. O painel ativo exibe uma borda de seleção. Acima de dois modos de exibição da imagem é a barra de ferramentas do assunto.

![Barra de ferramentas do Editor](../mfc/media/vctoolbareditor.gif "vcToolbarEditor") barra de ferramentas do Editor

O **barra de ferramentas** editor é semelhante ao **imagem** editor na funcionalidade. Os itens de menu, ferramentas gráficas e grade de bitmap são iguais do **imagem** editor. Há um comando de menu na **imagem** menu para permitir que você alterne entre a **barra de ferramentas** editor e o **imagem** editor. Para obter mais informações sobre como usar o **gráficos** barra de ferramentas **cores** paleta, ou **imagem** menu, consulte [Editor de imagens](../windows/image-editor-for-icons.md).

Para obter informações sobre como adicionar recursos a projetos gerenciados, consulte [recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index) na *guia do desenvolvedor do .NET Framework*. Para obter informações sobre como adicionar manualmente os arquivos de recursos a projetos gerenciados, acessar recursos, exibir recursos estáticos e atribuir cadeias de caracteres de recurso a propriedades, consulte [criando arquivos de recursos para aplicativos de área de trabalho](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obter informações sobre globalização e localização de recursos em aplicativos gerenciados, consulte [Globalizing e Localizando aplicativos do .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

MFC ou ATL

## <a name="see-also"></a>Consulte também

[Editores de recursos](../windows/resource-editors.md)<br/>
[Menus e outros recursos](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)