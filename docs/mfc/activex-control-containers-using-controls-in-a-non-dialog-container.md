---
title: 'Contêineres de controle ActiveX: Usando controles em um contêiner não da caixa de diálogo'
ms.date: 11/04/2016
helpviewer_keywords:
- Create method [MFC], ActiveX controls
- CreateControl method [MFC]
- ActiveX controls [MFC], creating
- ActiveX control containers [MFC], non-dialog containers
- ActiveX control containers [MFC], inserting controls
ms.assetid: 46f195b0-b8ca-4409-8cca-fbfaf2c9ab9f
ms.openlocfilehash: 70a67a6952d5361177b89e3ba514d7036b5799b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394865"
---
# <a name="activex-control-containers-using-controls-in-a-non-dialog-container"></a>Contêineres de controle ActiveX: Usando controles em um contêiner não da caixa de diálogo

Em alguns aplicativos, como um SDI ou um aplicativo MDI, você desejará inserir um controle em uma janela do aplicativo. O **criar** função de membro da classe wrapper, inserida pelo Visual C++, pode criar uma instância do controle dinamicamente, sem a necessidade de uma caixa de diálogo.

O **criar** função de membro tem os seguintes parâmetros:

*lpszWindowName*<br/>
Um ponteiro para o texto a ser exibido na propriedade de texto ou uma legenda do controle (se houver).

*dwStyle*<br/>
Estilos do Windows. Para obter uma lista completa, consulte [CWnd::CreateControl](../mfc/reference/cwnd-class.md#createcontrol).

*rect*<br/>
Especifica o tamanho e a posição do controle.

*pParentWnd*<br/>
Especifica a janela do controle pai, geralmente um `CDialog`. Ele não deve ser **nulo**.

*nID*<br/>
Especifica a ID do controle e pode ser usado pelo contêiner para referir-se ao controle.

Um exemplo de como usar essa função para criar dinamicamente um controle ActiveX seria em um modo de exibição de formulário de um aplicativo SDI. Em seguida, você pode criar uma instância do controle no `WM_CREATE` manipulador do aplicativo.

Neste exemplo, `CMyView` é a classe de exibição principal, `CCirc` é a classe de wrapper e CIRC. H é o cabeçalho (. H) o arquivo da classe wrapper.

Implementar esse recurso é um processo de quatro etapas.

### <a name="to-dynamically-create-an-activex-control-in-a-non-dialog-window"></a>Para criar dinamicamente um controle ActiveX em uma janela de caixa de diálogo não

1. Inserir CIRC. H em CMYVIEW. H, imediatamente antes o `CMyView` definição de classe:

   [!code-cpp[NVC_MFC_AxCont#12](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_1.h)]

1. Adicionar uma variável de membro (do tipo `CCirc`) para a seção protegida do `CMyView` localizada em CMYVIEW de definição de classe. H:

   [!code-cpp[NVC_MFC_AxCont#13](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_2.h)]
    [!code-cpp[NVC_MFC_AxCont#14](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_3.h)]

1. Adicionar um `WM_CREATE` manipulador de mensagens para a classe `CMyView`.

1. Na função de manipulador, `CMyView::OnCreate`, faça uma chamada para o controle `Create` funcionam usando a **isso** ponteiro como a janela pai:

   [!code-cpp[NVC_MFC_AxCont#15](../mfc/codesnippet/cpp/activex-control-containers-using-controls-in-a-non-dialog-container_4.cpp)]

1. Recompile o projeto. Um controle de c será criado dinamicamente sempre que o modo de exibição do aplicativo é criado.

## <a name="see-also"></a>Consulte também

[Contêineres de controle ActiveX](../mfc/activex-control-containers.md)
