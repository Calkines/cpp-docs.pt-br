---
title: 'Passo a passo: Adicionando um objeto D2D a um projeto do MFC'
ms.date: 04/25/2019
helpviewer_keywords:
- MFC, D2D
- D2D [MFC]
ms.assetid: dda36c33-c231-4da6-a62f-72d69a12b6dd
ms.openlocfilehash: cbb9e4002bb47ad8f65678c7a324267ca9717e94
ms.sourcegitcommit: f82a6de52470070accb09a3a8f8b08060c492efa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68411759"
---
# <a name="walkthrough-adding-a-d2d-object-to-an-mfc-project"></a>Passo a passo: Adicionando um objeto D2D a um projeto do MFC

Este tutorial ensina como adicionar um objeto Direct2D (D2D) básico a um projeto Visual C++, biblioteca MFC (MFC) e, em seguida, compilar o projeto em um aplicativo que imprime "Olá, mundo!" em um plano de fundo de gradiente.

O tutorial mostra como realizar essas tarefas:

- Crie um aplicativo MFC.

- Crie um pincel de cor sólida e um pincel de gradiente linear.

- Modifique o pincel de gradiente para que ele seja alterado adequadamente quando a janela for redimensionada.

- Implemente um manipulador de desenho D2D.

- Verifique os resultados.

[!INCLUDE[note_settings_general](../mfc/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este passo a passos, você deve ter o Visual Studio instalado com o **desenvolvimento de desktop com C++**  carga de trabalho e o componente opcional **do Visual C++ MFC para x86 e x64** .

## <a name="to-create-an-mfc-application"></a>Para criar um aplicativo MFC

1. Use o **Assistente de aplicativo MFC** para criar um aplicativo MFC. Confira [Passo a passo: Usando os novos controles](walkthrough-using-the-new-mfc-shell-controls.md) do shell do MFC para obter instruções sobre como abrir o assistente para sua versão do Visual Studio.

1. Na caixa **nome** , digite *MFCD2DWalkthrough*. Escolha **OK**.

1. No **Assistente de aplicativo do MFC**, escolha **concluir** sem alterar as configurações.

## <a name="to-create-a-solid-color-brush-and-a-linear-gradient-brush"></a>Para criar um pincel de cor sólida e um pincel de gradiente linear

1. No **Gerenciador de soluções**, no projeto **MFCD2DWalkthrough** , na pasta **arquivos de cabeçalho** , abra MFCD2DWalkthroughView. h. Adicione este código à `CMFCD2DWalkthroughView` classe para criar três variáveis de dados:

   ```cpp
   CD2DTextFormat* m_pTextFormat;
   CD2DSolidColorBrush* m_pBlackBrush;
   CD2DLinearGradientBrush* m_pLinearGradientBrush;
   ```

   Salve o arquivo e feche-o.

1. Na pasta **arquivos de origem** , abra MFCD2DWalkthroughView. cpp. No construtor para a `CMFCD2DWalkthroughView` classe, adicione este código:

   ```cpp
   // Enable D2D support for this window:
   EnableD2DSupport();

   // Initialize D2D resources:
   m_pBlackBrush = new CD2DSolidColorBrush(
       GetRenderTarget(),
       D2D1::ColorF(D2D1::ColorF::Black));

   m_pTextFormat = new CD2DTextFormat(
       GetRenderTarget(),
       _T("Verdana"),
       50);

   m_pTextFormat->Get()->SetTextAlignment(
       DWRITE_TEXT_ALIGNMENT_CENTER);

   m_pTextFormat->Get()->SetParagraphAlignment(
       DWRITE_PARAGRAPH_ALIGNMENT_CENTER);

   D2D1_GRADIENT_STOP gradientStops[2];

   gradientStops[0].color =
       D2D1::ColorF(D2D1::ColorF::White);

   gradientStops[0].position = 0.f;
   gradientStops[1].color =
       D2D1::ColorF(D2D1::ColorF::Indigo);

   gradientStops[1].position = 1.f;

   m_pLinearGradientBrush = new CD2DLinearGradientBrush(
       GetRenderTarget(),
       gradientStops,
       ARRAYSIZE(gradientStops),
       D2D1::LinearGradientBrushProperties(
           D2D1::Point2F(0,0),
           D2D1::Point2F(0,0)));
   ```

   Salve o arquivo e feche-o.

## <a name="to-modify-the-gradient-brush-so-that-it-will-change-appropriately-when-the-window-is-resized"></a>Para modificar o pincel de gradiente para que ele seja alterado adequadamente quando a janela for redimensionada

1. No menu **projeto** , escolha **Assistente de classe**.

1. No **Assistente de classe do MFC**, em nome da **classe**, selecione `CMFCD2DWalkthroughView`.

1. Na guia **mensagens** , na caixa **mensagens** , selecione `WM_SIZE` e, em seguida, escolha **Adicionar manipulador**. Essa ação adiciona o `OnSize` manipulador de mensagens `CMFCD2DWalkthroughView` à classe.

1. Na caixa **manipuladores existentes** , selecione `OnSize`. Escolha **Editar código** para exibir o `CMFCD2DWalkthroughView::OnSize` método. No final do método, adicione o código a seguir.

   ```cpp
   m_pLinearGradientBrush->SetEndPoint(CPoint(cx, cy));
   ```

   Salve o arquivo e feche-o.

## <a name="to-implement-a-d2d-drawing-handler"></a>Para implementar um manipulador de desenho D2D

1. No menu **projeto** , escolha **Assistente de classe**.

1. No **Assistente de classe do MFC**, em nome da **classe**, selecione `CMFCD2DWalkthroughView`.

1. Na guia **mensagens** , escolha **Adicionar mensagem personalizada**.

1. Na caixa de diálogo **Adicionar mensagem personalizada** , na caixa de **mensagem personalizada do Windows** , digite *AFX_WM_DRAW2D*. Na caixa **nome do manipulador de mensagens** , digite *OnDraw2D*. Selecione a opção **mensagem registrada** e escolha **OK**. Essa ação adiciona um manipulador de mensagens para a mensagem AFX_WM_DRAW2D à `CMFCD2DWalkthroughView` classe.

1. Na caixa **manipuladores existentes** , selecione `OnDraw2D`. Escolha **Editar código** para exibir o `CMFCD2DWalkthroughView::OnDraw2D` método. Use este código para o `CMFCD2DWalkthroughView::OnDrawD2D` método:

   ```cpp
   afx_msg LRESULT CMFCD2DWalkthroughView::OnDraw2D(
       WPARAM wParam,
       LPARAM lParam)
   {
       CHwndRenderTarget* pRenderTarget = (CHwndRenderTarget*)lParam;
       ASSERT_VALID(pRenderTarget);

       CRect rect;
       GetClientRect(rect);

       pRenderTarget->FillRectangle(rect, m_pLinearGradientBrush);

       pRenderTarget->DrawText(
           _T("Hello, World!"),
           rect,
           m_pBlackBrush,
           m_pTextFormat);

       return TRUE;
   }
   ```

   Salve o arquivo e feche-o.

## <a name="to-verify-the-results"></a>Para verificar os resultados

Crie e execute o aplicativo. Ele deve ter um retângulo gradiente que muda quando você redimensiona a janela. "Olá, Mundo!" deve ser exibido no centro do retângulo.

## <a name="see-also"></a>Consulte também

[Explicações Passo a Passo](../mfc/walkthroughs-mfc.md)
