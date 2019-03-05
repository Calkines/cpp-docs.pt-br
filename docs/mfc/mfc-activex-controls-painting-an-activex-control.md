---
title: 'Controles ActiveX MFC: Pintando um controle ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
ms.openlocfilehash: b90aa331c289caf827785af2eeba037e70f686ab
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281924"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>Controles ActiveX MFC: Pintando um controle ActiveX

Este artigo descreve o processo de pintura do controle ActiveX e como você pode alterar o código de pintura para otimizar o processo. (Consulte [otimizando o desenho de controle](../mfc/optimizing-control-drawing.md) para técnicas sobre como otimizar o desenho por não ter controles individualmente restaurem objetos GDI selecionados anteriormente. Depois que todos os controles desenhados, o contêiner pode restaurar automaticamente os objetos originais.)

>[!IMPORTANT]
> ActiveX é uma tecnologia herdada que não deve ser usada para novos desenvolvimentos. Para obter mais informações sobre tecnologias modernas que substituem o ActiveX, consulte [controles ActiveX](activex-controls.md).

Os exemplos neste artigo são de um controle criado pelo Assistente de controle ActiveX do MFC com as configurações padrão. Para obter mais informações sobre como criar um aplicativo de esqueleto de controle usando o Assistente de controle de ActiveX do MFC, consulte o artigo [Assistente de controle ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md).

Os seguintes tópicos são abordados:

- [O processo geral de um controle e o código criado pelo Assistente de controle de ActiveX para dar suporte à pintura de pintura](#_core_the_painting_process_of_an_activex_control)

- [Como otimizar o processo de pintura](#_core_optimizing_your_paint_code)

- [Como pintar seu controle usando metarquivos](#_core_painting_your_control_using_metafiles)

##  <a name="_core_the_painting_process_of_an_activex_control"></a> O processo de pintura de um controle ActiveX

Quando os controles ActiveX são inicialmente exibidos ou são redesenhados, elas seguem um processo de pintura semelhante a outros aplicativos desenvolvidos usando o MFC, com uma diferença importante: Controles ActiveX podem estar em um ativo ou em um estado inativo.

Um controle ativo é representado em um contêiner de controle ActiveX por uma janela filho. Como outras janelas, ele é responsável por pintando em si, quando for recebida uma mensagem WM_PAINT. A classe do controle base, [COleControl](../mfc/reference/colecontrol-class.md), manipula essa mensagem em seu `OnPaint` função. Essa implementação padrão chama o `OnDraw` função do seu controle.

Um controle inativo é pintado diferente. Quando o controle estiver inativo, sua janela é invisível ou inexistente, portanto, ele não pode receber uma mensagem de pintura. Em vez disso, o contêiner de controle chama diretamente o `OnDraw` função do controle. Isso é diferente do processo de pintura do controle de um Active Directory em que o `OnPaint` nunca é chamada de função de membro.

Conforme discutido nos parágrafos anteriores, como um controle ActiveX é atualizado depende do estado do controle. No entanto, como o framework chama o `OnDraw` função de membro em ambos os casos, você adiciona a maior parte do seu código de pintura nessa função de membro.

O `OnDraw` função de membro manipula pintura do controle. Quando um controle estiver inativo, o contêiner de controle chama `OnDraw`, passando o contexto de dispositivo do contêiner de controle e as coordenadas da área retangular ocupadas pelo controle.

O retângulo transmitido pelo framework para o `OnDraw` função de membro contém a área ocupada pelo controle. Se o controle estiver ativo, o canto superior esquerdo é (0, 0) e o contexto de dispositivo passado para a janela filho que contém o controle. Se o controle estiver inativo, a coordenada superior esquerda não é necessariamente (0, 0) e o contexto de dispositivo passado para o contêiner de controle que contém o controle.

> [!NOTE]
>  É importante que as modificações `OnDraw` não dependem do ponto à esquerda superior do retângulo que está sendo igual a (0, 0) e que você desenhar somente dentro do retângulo passado para `OnDraw`. Se você desenhar além da área do retângulo, poderão ocorrer resultados inesperados.

A implementação padrão fornecida pelo Assistente de controle ActiveX do MFC no arquivo de implementação de controle (. CPP), mostrado abaixo, pinta o retângulo com um pincel branco e preenche a elipse com a cor de plano de fundo atual.

[!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]

> [!NOTE]
>  Ao pintar um controle, você não deve fazer suposições sobre o estado do contexto do dispositivo que é passado como o *pdc* parâmetro para o `OnDraw` função. Ocasionalmente, o contexto de dispositivo é fornecido pelo aplicativo de contêiner e não serão necessariamente inicializado para o estado padrão. Em particular, selecione explicitamente pincéis, canetas, cores, fontes e outros recursos que seu código de desenho depende.

##  <a name="_core_optimizing_your_paint_code"></a> Otimizando o código de pintura

Depois que o controle está pintando com êxito em si, a próxima etapa é otimizar o `OnDraw` função.

A implementação padrão do controle ActiveX de pintura pinta a área inteira do controle. Isso é suficiente para controles simples, mas em muitos casos redesenho do controle seria com mais rapidez se apenas a parte que precisava ser atualizada foi redesenhada, em vez de todo o controle.

O `OnDraw` função fornece um método fácil de otimização, passando *rcInvalid*, a área retangular do controle que precisa ser redesenhada. Use esta área, geralmente menor do que a área inteira do controle, para acelerar o processo de pintura.

##  <a name="_core_painting_your_control_using_metafiles"></a> Pintando seu controle usando metarquivos

Na maioria dos casos o *pdc* parâmetro para o `OnDraw` função aponta para um contexto de dispositivo da tela (DC). No entanto, ao imprimir imagens do controle ou durante uma sessão de visualização de impressão, o controlador de domínio recebida para a renderização é um tipo especial chamado "metarquivo DC". Ao contrário de uma tela de controlador de domínio, que imediatamente manipula solicitações enviadas a ele, um controlador de domínio do metarquivo armazena as solicitações para serem reproduzidas em um momento posterior. Alguns aplicativos de contêiner também podem optar por processar a imagem de controle usando um controlador de domínio no modo de design do metarquivo.

Metarquivo desenho solicitações pode ser feito pelo contêiner por meio de duas funções de interface: `IViewObject::Draw` (essa função também pode ser chamada para desenhar-metarquivo não) e `IDataObject::GetData`. Quando um metarquivo do controlador de domínio é passado como um dos parâmetros, a estrutura MFC faz uma chamada para [COleControl::OnDrawMetafile](../mfc/reference/colecontrol-class.md#ondrawmetafile). Como esta é uma função membro virtual, substituem essa função na classe de controle para fazer qualquer processamento especial. As chamadas de comportamento padrão `COleControl::OnDraw`.

Para verificar se que o controle pode ser desenhado na tela e Metarquivo contextos de dispositivo, você deve usar apenas as funções de membro que são suportadas em uma tela e um controlador de domínio do metarquivo. Lembre-se de que o sistema de coordenadas não pode ser medido em pixels.

Porque a implementação padrão de `OnDrawMetafile` chama o controle `OnDraw` função, use apenas as funções de membro que são adequadas para um metarquivo e um contexto de dispositivo da tela, a menos que você substitua `OnDrawMetafile`. O exemplo a seguir lista o subconjunto de `CDC` funções de membro que podem ser usadas em um metarquivo e um contexto de dispositivo da tela. Para obter mais informações sobre essas funções, consulte a classe [CDC](../mfc/reference/cdc-class.md) na *referência da MFC*.

|Arc|BibBlt|Chord|
|---------|------------|-----------|
|`Ellipse`|`Escape`|`ExcludeClipRect`|
|`ExtTextOut`|`FloodFill`|`IntersectClipRect`|
|`LineTo`|`MoveTo`|`OffsetClipRgn`|
|`OffsetViewportOrg`|`OffsetWindowOrg`|`PatBlt`|
|`Pie`|`Polygon`|`Polyline`|
|`PolyPolygon`|`RealizePalette`|`RestoreDC`|
|`RoundRect`|`SaveDC`|`ScaleViewportExt`|
|`ScaleWindowExt`|`SelectClipRgn`|`SelectObject`|
|`SelectPalette`|`SetBkColor`|`SetBkMode`|
|`SetMapMode`|`SetMapperFlags`|`SetPixel`|
|`SetPolyFillMode`|`SetROP2`|`SetStretchBltMode`|
|`SetTextColor`|`SetTextJustification`|`SetViewportExt`|
|`SetViewportOrg`|`SetWindowExt`|`SetWindowORg`|
|`StretchBlt`|`TextOut`||

Além `CDC` funções de membro, há várias outras funções que são compatíveis em um controlador de domínio do metarquivo. Eles incluem [CPalette::AnimatePalette](../mfc/reference/cpalette-class.md#animatepalette), [CFont::CreateFontIndirect](../mfc/reference/cfont-class.md#createfontindirect)e três funções de membro de `CBrush`: [CreateBrushIndirect](../mfc/reference/cbrush-class.md#createbrushindirect), [CreateDIBPatternBrush](../mfc/reference/cbrush-class.md#createdibpatternbrush), e [CreatePatternBrush](../mfc/reference/cbrush-class.md#createpatternbrush).

Funções que não são registradas em um metarquivo são: [DrawFocusRect](../mfc/reference/cdc-class.md#drawfocusrect), [DrawIcon](../mfc/reference/cdc-class.md#drawicon), [DrawText](../mfc/reference/cdc-class.md#drawtext), [ExcludeUpdateRgn](../mfc/reference/cdc-class.md#excludeupdatergn), [FillRect](../mfc/reference/cdc-class.md#fillrect), [FrameRect ](../mfc/reference/cdc-class.md#framerect), [GrayString](../mfc/reference/cdc-class.md#graystring), [InvertRect](../mfc/reference/cdc-class.md#invertrect), [ScrollDC](../mfc/reference/cdc-class.md#scrolldc), e [TabbedTextOut](../mfc/reference/cdc-class.md#tabbedtextout). Como um controlador de domínio de meta-arquivo não é, na verdade, associado um dispositivo, é possível usar SetDIBits, GetDIBits e CreateDIBitmap com um controlador de domínio do metarquivo. Você pode usar SetDIBitsToDevice e StretchDIBits com um metarquivo do controlador de domínio como o destino. [CreateCompatibleDC](../mfc/reference/cdc-class.md#createcompatibledc), [CreateCompatibleBitmap](../mfc/reference/cbitmap-class.md#createcompatiblebitmap), e [CreateDiscardableBitmap](../mfc/reference/cbitmap-class.md#creatediscardablebitmap) não são significativos com um controlador de domínio do metarquivo.

Outro ponto a considerar ao usar um controlador de domínio do metarquivo é que o sistema de coordenadas não pode ser medido em pixels. Por esse motivo, todos os seu código de desenho deve ser ajustado para caber no retângulo passado para `OnDraw` no *rcBounds* parâmetro. Isso impede que a pintura acidental fora do controle porque *rcBounds* representa o tamanho da janela do controle.

Depois que você tiver implementado a renderização de meta-arquivo para o controle, use o contêiner de teste para testar o metarquivo. Ver [testando propriedades e eventos com contêiner de teste](../mfc/testing-properties-and-events-with-test-container.md) para obter informações sobre como acessar o contêiner de teste.

#### <a name="to-test-the-controls-metafile-using-test-container"></a>Para testar o metarquivo do controle usando o contêiner de teste

1. Sobre o contêiner de teste **edite** menu, clique em **inserir o novo controle**.

1. No **inserir o novo controle** caixa, selecione o controle e clique em **Okey**.

   O controle será exibido no contêiner de teste.

1. Sobre o **controle** menu, clique em **desenhar metarquivo**.

   É exibida uma janela separada, na qual o metarquivo é exibido. Você pode alterar o tamanho dessa janela para ver como o dimensionamento afeta metarquivo do controle. Você pode fechar esta janela a qualquer momento.

## <a name="see-also"></a>Consulte também

[Controles ActiveX do MFC](../mfc/mfc-activex-controls.md)
