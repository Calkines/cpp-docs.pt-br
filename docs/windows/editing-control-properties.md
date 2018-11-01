---
title: Editando propriedades de controle
ms.date: 11/04/2016
helpviewer_keywords:
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls [C++], editing properties
ms.assetid: 9bdae21d-6dec-4344-a197-2ca4fc46d040
ms.openlocfilehash: cd9226e6eb4fc2b16d24cd0c9727d4fcbfdbf02b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454781"
---
# <a name="editing-control-properties"></a>Editando propriedades de controle

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>Para editar as propriedades de um controle ou controles

1. Na caixa de diálogo, selecione o controle que você deseja modificar.

   > [!NOTE]
   > Se você selecionar vários controles, somente as propriedades comuns para os controles selecionados podem ser editadas.

2. No [janela de propriedades](/visualstudio/ide/reference/properties-window), alterar as propriedades de seu controle.

   > [!NOTE]
   > Quando você define o **Bitmap** propriedade de um botão, um botão de opção ou um controle de caixa de seleção igual a **verdadeiro**, o estilo BS_BITMAP é implementado para o seu controle. Para obter mais informações, consulte [estilos de botão](../mfc/reference/styles-used-by-mfc.md#button-styles). Para obter um exemplo de associação de um bitmap com um controle, consulte [CButton::SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Bitmaps não aparecerá no seu controle enquanto você estiver na **caixa de diálogo** editor de recursos.

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>Para desfazer as alterações nas propriedades de um controle

1. Verifique se o controle tem foco **caixa de diálogo** editor.

2. Escolher **desfazer** da **editar** menu (se o foco não estiver no controle, o **desfazer** comando estará disponível).

Para obter informações sobre como adicionar recursos a projetos gerenciados, consulte [recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index) na *guia do desenvolvedor do .NET Framework*. Para obter informações sobre como adicionar manualmente os arquivos de recursos a projetos gerenciados, acessar recursos, exibir recursos estáticos e atribuir cadeias de caracteres de recursos a propriedades, consulte [instruções passo a passo: Localizando Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte também

[Controles em caixas de diálogo](../windows/controls-in-dialog-boxes.md)