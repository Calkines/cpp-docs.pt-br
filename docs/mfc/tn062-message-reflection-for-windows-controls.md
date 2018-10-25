---
title: 'TN062: Reflexão para controles do Windows de mensagem | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.controls.messages
dev_langs:
- C++
helpviewer_keywords:
- ON_WM_VKEYTOITEM_REFLECT macro [MFC]
- ON_WM_DRAWITEM_REFLECT macro [MFC]
- ON_WM_VSCROLL_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT message [MFC]
- ON_CONTROL_REFLECT_EX macro [MFC]
- ON_UPDATE_COMMAND_UI_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT_EX message [MFC]
- ON_WM_HSCROLL_REFLECT macro [MFC]
- message reflection [MFC]
- ON_WM_COMPAREITEM_REFLECT macro [MFC]
- ON_WM_MEASUREITEM_REFLECT macro [MFC]
- ON_NOTIFY message [MFC]
- WM_COMMAND [MFC]
- WM_CTLCOLOR message [MFC]
- TN062 [MFC]
- ON_WM_CHARTOITEM_REFLECT macro [MFC]
- ON_WM_CTLCOLOR_REFLECT macro [MFC]
- ON_WM_DELETEITEM_REFLECT macro [MFC]
- notification messages [MFC]
- ON_WM_PARENTNOTIFY_REFLECT macro [MFC]
- WM_NOTIFY message [MFC]
- ON_CONTROL_REFLECT macro
ms.assetid: 53efb0ba-fcda-4fa0-a3c7-14e0b78fb494
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 994095042dc473fda315b6d842d9ec9355ff3671
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055392"
---
# <a name="tn062-message-reflection-for-windows-controls"></a>TN062: reflexão de mensagem para controles do Windows

> [!NOTE]
> A nota técnica a seguir não foi atualizada desde que foi incluído pela primeira vez na documentação online. Como resultado, alguns procedimentos e tópicos podem estar desatualizadas ou incorretas. Para obter as informações mais recentes, é recomendável que você pesquise o tópico de interesse no índice da documentação online.

Essa observação técnica descreve reflexão de mensagem, um novo recurso do 4.0 do MFC. Ele também contém instruções para criar um controle reutilizável simple que usa a reflexão de mensagem.

Essa observação técnica não aborda a reflexão de mensagem que diz respeito aos controles ActiveX (antes chamados de controles OLE). Consulte o artigo [controles ActiveX: subclasses de um controle de Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md).

**O que é a reflexão de mensagem**

Controles do Windows com frequência enviam mensagens de notificação para as janelas pai. Por exemplo, muitos controles de enviar uma mensagem de notificação de cor de controle (WM_CTLCOLOR ou uma de suas variantes) para seu pai para permitir que o pai fornecer um pincel para pintar a tela de fundo do controle.

No Windows e no MFC antes da versão 4.0, a janela pai, muitas vezes, uma caixa de diálogo, é responsável por manipular essas mensagens. Isso significa que o código para manipular a mensagem deve estar na classe da janela pai e que ele deve ser duplicado em todas as classes necessárias para manipular a mensagem. No caso acima, cada caixa de diálogo que queria controles com telas de fundo personalizados precisa lidar com a mensagem de notificação de cor do controle. Seria muito mais fácil de reutilizar o código se uma classe de controle poderia ser escrita que lidaria com sua própria cor de plano de fundo.

No MFC 4.0, o mecanismo antigo ainda funciona — windows pai podem lidar com mensagens de notificação. Além disso, no entanto, 4.0 MFC facilita a reutilização, fornecendo um recurso chamado "reflexão de mensagem" que permite que essas mensagens de notificação a ser manipulada na janela de controle filho ou a janela pai ou em ambos. No exemplo de cor do plano de fundo a controle, agora você pode escrever uma classe de controle que define sua própria cor de plano de fundo ao manipular a mensagem WM_CTLCOLOR refletida — tudo sem depender do pai. (Observe que como reflexão de mensagem é implementado pelo MFC, não pelo Windows, a classe de janela pai deve ser derivada de `CWnd` para reflexão de mensagem funcione.)

Versões mais antigas do MFC faziam algo semelhante à reflexão de mensagem, fornecendo funções virtuais para algumas mensagens, como mensagens para caixas de lista desenhado pelo proprietário (WM_DRAWITEM e assim por diante). O novo mecanismo de reflexão de mensagem é generalizada e consistente.

Reflexão de mensagem é compatível com versões anteriores com o código escrito para versões do MFC antes de 4.0.

Se você tiver fornecido um manipulador para uma mensagem específica ou para um intervalo de mensagens na classe da sua janela pai, ele substituirá refletidas manipuladores de mensagens para a mesma mensagem, desde que você não chame a função do manipulador de classe base no seu próprio manipulador. Por exemplo, se você tratar WM_CTLCOLOR em sua classe de caixa de diálogo, sua manipulação substituirá quaisquer manipuladores de mensagem refletida.

Se, em sua classe de janela pai, você deve fornecer um manipulador para uma mensagem WM_NOTIFY específica ou mensagens de um intervalo de WM_NOTIFY, seu manipulador será chamado somente se o controle filho enviando essas mensagens não tem um manipulador de mensagens refletidas por meio de `ON_NOTIFY_REFLECT()`. Se você usar `ON_NOTIFY_REFLECT_EX()` em seu mapa de mensagem, seu manipulador de mensagens pode ou não pode permitir que a janela pai lidar com a mensagem. Se o manipulador retorna **falsos**, a mensagem será manipulada pelo pai, enquanto uma chamada que retorna **verdadeiro** não permite que o pai para tratá-la. Observe que a mensagem refletida é manipulada antes da mensagem de notificação.

Quando uma mensagem WM_NOTIFY é enviada, o controle é oferecido a primeira oportunidade para tratá-la. Se qualquer outra mensagem refletida for enviada, a janela pai tem a primeira oportunidade para tratá-la e o controle receberá a mensagem refletida. Para fazer isso, ele precisará de uma função de manipulador e uma entrada apropriada no mapa de mensagens de classe do controle.

A macro de mapa de mensagem para mensagens refletidas é ligeiramente diferente para notificações regulares: ele tem *_REFLECT* acrescentado ao nome comum. Por exemplo, para lidar com uma mensagem WM_NOTIFY no pai, use a macro ON_NOTIFY no mapa de mensagens do pai. Para lidar com a mensagem refletida no controle filho, use a macro ON_NOTIFY_REFLECT no mapa de mensagens do controle filho. Em alguns casos, os parâmetros são diferentes, também. Observe que ClassWizard geralmente pode adicionar as entradas de mapa de mensagem para você e fornecer implementações de função em esqueleto com os parâmetros corretos.

Ver [TN061: mensagens ON_NOTIFY e WM_NOTIFY](../mfc/tn061-on-notify-and-wm-notify-messages.md) para obter informações sobre a nova mensagem WM_NOTIFY.

**Entradas de mapa de mensagem e protótipos de função de manipulador para mensagens refletidas**

Para lidar com uma mensagem de notificação do controle refletido, use as macros de mapa de mensagem e os protótipos de função listados na tabela a seguir.

ClassWizard geralmente pode adicionar essas entradas de mapa de mensagem para você e fornecer implementações de função em esqueleto. Ver [definindo um manipulador de mensagem para uma mensagem refletida](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md) para obter informações sobre como definir manipuladores para mensagens refletidas.

Para converter o nome da mensagem para o nome da macro refletido, preceda *on _* e acrescente *_REFLECT*. Por exemplo, WM_CTLCOLOR torna-se ON_WM_CTLCOLOR_REFLECT. (Para ver quais mensagens podem ser refletidas, fazer a conversão oposta nas entradas de macro na tabela a seguir).

As três exceções à regra acima são da seguinte maneira:

- A macro para notificações de WM_COMMAND é ON_CONTROL_REFLECT.

- A macro para reflexos WM_NOTIFY é ON_NOTIFY_REFLECT.

- A macro para reflexos ON_UPDATE_COMMAND_UI é ON_UPDATE_COMMAND_UI_REFLECT.

Em cada um dos casos especiais acima, você deve especificar o nome da função de membro de manipulador. Em outros casos, você deve usar o nome padrão para a função de manipulador.

Os significados dos parâmetros e valores de retorno das funções estão documentados em nome da função ou o nome da função com *em* anexado. Por exemplo, `CtlColor` é documentado no `OnCtlColor`. Vários manipuladores de mensagem refletida necessário menos parâmetros que os manipuladores de semelhantes em uma janela pai. Apenas correspondem aos nomes na tabela a seguir com os nomes dos parâmetros formais na documentação.

|Entrada de mapa|Protótipo da função|
|---------------|------------------------|
|**ON_CONTROL_REFLECT (** `wNotifyCode` **,** `memberFxn` **)**|**void afx_msg** `memberFxn` **();**|
|**ON_NOTIFY_REFLECT (** `wNotifyCode` **,** `memberFxn` **)**|**void afx_msg** `memberFxn` **(NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT** <strong>\*</strong> *resultado* **);**|
|**ON_UPDATE_COMMAND_UI_REFLECT (** `memberFxn` **)**|**void afx_msg** `memberFxn` **(CCmdUI** <strong>\*</strong> `pCmdUI` **);**|
|**(ON_WM_CTLCOLOR_REFLECT)**|**afx_msg HBRUSH CtlColor (CDC** <strong>\*</strong> `pDC` **, UINT** `nCtlColor` **);**|
|**(ON_WM_DRAWITEM_REFLECT)**|**afx_msg void DrawItem (LPDRAWITEMSTRUCT** `lpDrawItemStruct` **);**|
|**(ON_WM_MEASUREITEM_REFLECT)**|**afx_msg void MeasureItem (LPMEASUREITEMSTRUCT** `lpMeasureItemStruct` **);**|
|**(ON_WM_DELETEITEM_REFLECT)**|**afx_msg void DeleteItem (LPDELETEITEMSTRUCT** `lpDeleteItemStruct` **);**|
|**(ON_WM_COMPAREITEM_REFLECT)**|**int afx_msg CompareItem (LPCOMPAREITEMSTRUCT** `lpCompareItemStruct` **);**|
|**(ON_WM_CHARTOITEM_REFLECT)**|**int afx_msg CharToItem (UINT** `nKey` **, UINT** `nIndex` **);**|
|**(ON_WM_VKEYTOITEM_REFLECT)**|**int afx_msg VKeyToItem (UINT** `nKey` **, UINT** `nIndex` **);**|
|**(ON_WM_HSCROLL_REFLECT)**|**afx_msg void HScroll (UINT** `nSBCode` **, UINT** `nPos` **);**|
|**(ON_WM_VSCROLL_REFLECT)**|**afx_msg void VScroll (UINT** `nSBCode` **, UINT** `nPos` **);**|
|**(ON_WM_PARENTNOTIFY_REFLECT)**|**afx_msg void ParentNotify (UINT** `message` **, LPARAM** `lParam` **);**|

As macros ON_NOTIFY_REFLECT e ON_CONTROL_REFLECT têm variações que permitem que mais de um objeto (como o controle e seu pai) para lidar com uma determinada mensagem.

|Entrada de mapa|Protótipo da função|
|---------------|------------------------|
|**ON_NOTIFY_REFLECT_EX (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **(NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT** <strong>\*</strong> *resultado* **);**|
|**ON_CONTROL_REFLECT_EX (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **();**|

## <a name="handling-reflected-messages-an-example-of-a-reusable-control"></a>Tratamento de mensagens de refletido: Um exemplo de um controle reutilizável

Este exemplo simple cria um controle reutilizável chamado `CYellowEdit`. O controle funciona da mesma forma um controle de edição regular, exceto que ele exibe texto preto em um plano de fundo amarelo. Seria fácil adicionar funções de membro que permitiriam a `CYellowEdit` controle para exibir cores diferentes.

### <a name="to-try-the-example-that-creates-a-reusable-control"></a>Para testar o exemplo que cria um controle reutilizável

1. Crie uma nova caixa de diálogo em um aplicativo existente. Para obter mais informações, consulte o [editor de caixa de diálogo](../windows/dialog-editor.md) tópico.

   Você deve ter um aplicativo no qual a desenvolver o controle reutilizável. Se você não tiver um aplicativo existente para usar, crie um aplicativo baseado em diálogo usando AppWizard.

2. Com o seu projeto carregado no Visual C++, use ClassWizard para criar uma nova classe chamada `CYellowEdit` com base em `CEdit`.

3. Adicione três variáveis de membro à sua `CYellowEdit` classe. As duas primeiras serão *COLORREF* variáveis para armazenar a cor do texto e a cor do plano de fundo. A terceira será um `CBrush` objeto que conterá o pincel para pintar a tela de fundo. O `CBrush` objeto permite que você criar o pincel de uma vez, simplesmente fazendo referência a ela depois disso e destruir o pincel automaticamente quando o `CYellowEdit` controle é destruído.

4. Inicialize as variáveis de membro, escrevendo o construtor da seguinte maneira:

    ```cpp
    CYellowEdit::CYellowEdit()
    {
        m_clrText = RGB(0, 0, 0);
        m_clrBkgnd = RGB(255, 255, 0);
        m_brBkgnd.CreateSolidBrush(m_clrBkgnd);
    }
    ```

5. Usando o ClassWizard, adicione um manipulador para o refletido WM_CTLCOLOR (mensagem) para sua `CYellowEdit` classe. Observe que o sinal de igual na frente do nome de mensagem na lista de mensagens, que você pode manipular indica que a mensagem seja refletida. Isso é descrito em [definindo um manipulador de mensagem para uma mensagem refletida](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

   ClassWizard adiciona a seguinte função de macro e esqueleto de mapa de mensagem para você:

    ```cpp
    ON_WM_CTLCOLOR_REFLECT()
    // Note: other code will be in between....

    HBRUSH CYellowEdit::CtlColor(CDC* pDC, UINT nCtlColor)
    {
        // TODO: Change any attributes of the DC here
        // TODO: Return a non-NULL brush if the
        //       parent's handler should not be called
        return NULL;
    }
    ```

6. Substitua o corpo da função com o código a seguir. O código especifica a cor do texto, a cor de plano de fundo do texto e a cor de fundo para o restante do controle.

    ```cpp
    pDC->SetTextColor(m_clrText);   // text
    pDC->SetBkColor(m_clrBkgnd);    // text bkgnd
    return m_brBkgnd;               // ctl bkgnd
    ```

7. Criar um controle de edição na caixa de diálogo e, em seguida, anexá-lo a uma variável de membro clicando duas vezes no controle de edição enquanto pressiona uma tecla de controle. Na caixa de diálogo Adicionar variável de membro, o nome da variável de término e escolha "Controle" para a categoria, em seguida, "CYellowEdit" para o tipo de variável. Não se esqueça de definir a ordem de tabulação na caixa de diálogo. Além disso, certifique-se de incluir o arquivo de cabeçalho para o `CYellowEdit` controle no arquivo de cabeçalho da caixa de diálogo.

8. Compile e execute seu aplicativo. O controle de edição terá um plano de fundo amarelo.

## <a name="see-also"></a>Consulte também

[Observações técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Observações técnicas por categoria](../mfc/technical-notes-by-category.md)
