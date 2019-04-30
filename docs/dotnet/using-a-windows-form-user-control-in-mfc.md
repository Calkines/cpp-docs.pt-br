---
title: Usando um controle de usuário do Windows Form no MFC
ms.date: 1/08/2018
helpviewer_keywords:
- MFC [C++], Windows Forms support
- interoperability [C++], Windows Forms in MFC
- interoperability [C++], MFC
- interop [C++], Windows Forms in MFC
- interop [C++], MFC
- Windows Forms [C++], MFC support
ms.assetid: 63fb099b-1dff-469c-9e34-dab52e122fcd
ms.openlocfilehash: 38c5c37712b430b137934d441056e60f2c130f78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384485"
---
# <a name="using-a-windows-form-user-control-in-mfc"></a>Usando um controle de usuário do Windows Form no MFC

Usando as classes de suporte do MFC Windows Forms, você pode hospedar controles dos Windows Forms em seus aplicativos do MFC como um controle ActiveX em caixas de diálogo do MFC ou modos de exibição. Além disso, os formulários do Windows Forms podem ser hospedados como caixas de diálogo do MFC.

As seções a seguir descrevem como:

- Hospede um controle de formulários do Windows em uma caixa de diálogo do MFC.

- Hospede um controle de usuário do Windows Forms como uma exibição MFC.

- Hospede um formulário do Windows Forms como uma caixa de diálogo do MFC.

> [!NOTE]
> Integração de formulários do Windows MFC funciona apenas em projetos que vincular dinamicamente ao MFC (projetos nos quais `_AFXDLL` é definida).

> [!NOTE]
> Quando você compila seu aplicativo usando uma cópia privada (modificada) das interfaces de formulários do Windows MFC DLL (mfcmifc80.dll), ele será instalado no GAC, a menos que você substitua a chave da Microsoft com sua própria chave de fornecedor. Para obter mais informações sobre assinatura de assembly, consulte [Programando com Assemblies](/dotnet/framework/app-domains/programming-with-assemblies) e [Assemblies com nome forte (assinatura de Assembly) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md).

Se seu aplicativo do MFC usa o Windows Forms, você precisará redistribuir mfcmifc80.dll com seu aplicativo. Para obter mais informações, consulte [redistribuindo a biblioteca do MFC](../windows/redistributing-the-mfc-library.md).

## <a name="in-this-section"></a>Nesta seção

[Hospedando um controle de usuário do Windows Form em uma caixa de diálogo do MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)

[Hospedando um controle de usuário do Windows Forms como uma exibição do MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)

[Hospedando um controle de usuário do Windows Form como uma caixa de diálogo do MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)

## <a name="reference"></a>Referência

[Classe CWinFormsControl](../mfc/reference/cwinformscontrol-class.md)

[Classe CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md)

[Classe CWinFormsView](../mfc/reference/cwinformsview-class.md)

[Interface ICommandSource](../mfc/reference/icommandsource-interface.md)

[Interface ICommandTarget](../mfc/reference/icommandtarget-interface.md)

[Interface ICommandUI](../mfc/reference/icommandui-interface.md)

[Interface IView](../mfc/reference/iview-interface.md)

[CommandHandler](../atl/commandhandler.md)

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)

[UICheckState](../mfc/reference/uicheckstate-enumeration.md)

## <a name="related-sections"></a>Seções relacionadas

[Windows Forms](/dotnet/framework/winforms/index)

[Controles dos Windows Forms](/dotnet/framework/winforms/controls/index)

## <a name="see-also"></a>Consulte também

[Elementos da Interface do usuário](../mfc/user-interface-elements-mfc.md)<br/>
[Modos de exibição de formulário](../mfc/form-views-mfc.md)
