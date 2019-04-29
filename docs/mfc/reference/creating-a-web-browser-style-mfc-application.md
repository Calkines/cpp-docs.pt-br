---
title: Criando um aplicativo MFC no estilo de navegador da Web
ms.date: 06/25/2018
f1_keywords:
- vc.appwiz.mfcweb.project
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
ms.openlocfilehash: 12df36188bd858f73ff4834236a19583023e5f93
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372225"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>Criando um aplicativo MFC no estilo de navegador da Web

Um aplicativo de estilo de navegador da Web pode acessar informações da Internet (como HTML ou documentos ativos) ou uma intranet, bem como pastas no sistema de arquivos local e em uma rede. Derivando a classe de exibição do aplicativo do [CHtmlView](../../mfc/reference/chtmlview-class.md), efetivamente tornar o aplicativo um navegador da Web, fornecendo o modo de exibição com o controle WebBrowser.

### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>Para criar um aplicativo de navegador da Web com base na arquitetura de documento/exibição do MFC

1. Siga as instruções em [criando um aplicativo MFC](../../mfc/reference/creating-an-mfc-application.md).

1. No Assistente de aplicativo MFC [tipo de aplicativo](../../mfc/reference/application-type-mfc-application-wizard.md) página, verifique se o **arquitetura de documento/exibição** caixa está marcada. (Você pode escolher entre **único documento** ou **vários documentos**, mas não **caixa de diálogo com base em**.)

1. Sobre o [Classes geradas de revisão](../../mfc/reference/generated-classes-mfc-application-wizard.md) página, use o **classe Base** menu suspenso para selecionar `CHtmlView`.

1. Selecione as outras opções desejadas integradas do aplicativo de esqueleto.

1. Clique em **Finalizar**.

O controle WebBrowser dá suporte à navegação na Web por meio de hiperlinks e navegação de localizador de recurso uniforme (URL). O controle mantém uma lista de histórico que permite ao usuário navegar para frente e para trás por meio de visitadas anteriormente sites, pastas e documentos. O controle diretamente manipula a navegação, hiperlinks, listas de histórico, Favoritos e segurança. Aplicativos podem usar o controle WebBrowser como um contêiner de documento ativo para documentos ativos host também. Portanto, os documentos com formatação, como planilhas do Microsoft Excel ou documentos do Word podem ser abertos e editados no local de dentro do controle WebBrowser. O controle WebBrowser também é um contêiner de controle ActiveX que pode hospedar qualquer controle ActiveX.

> [!NOTE]
>  O controle WebBrowser ActiveX (e, portanto, `CHtmlView`) está disponível somente para aplicativos em execução em versões do Windows no qual o Internet Explorer 4.0 ou posterior foi instalado.

Porque `CHtmlView` simplesmente implementa o controle de navegador da Web Microsoft, seu suporte para impressão não é como qualquer outra [CView](../../mfc/reference/cview-class.md)-as classes derivadas. Em vez disso, o controle WebBrowser implementa a interface do usuário de impressora e impressão. Como resultado, `CHtmlView` faz não dão suporte a visualização de impressão, e não fornece a estrutura para outras funções de suporte de impressão: por exemplo, [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting), [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting), e [CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting), que estão disponíveis em outros aplicativos do MFC.

`CHtmlView` atua como um wrapper para o controle de navegador da Web, que fornece um modo de exibição em uma Web ou uma página HTML de seu aplicativo. O assistente cria uma substituição para o [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) função na classe de exibição, fornecendo um link de navegação para o site do Microsoft Visual C++:

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    Navigate2(_T("http://www.msdn.microsoft.com/vstudio/"),
        NULL,
        NULL);
}
```

Você pode substituir esse site por um de seus próprios, ou você pode usar o [LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource) a função de membro para abrir uma página HTML que reside no script de recurso do projeto como o conteúdo padrão para o modo de exibição. Por exemplo:

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    LoadFromResource(IDR_HTML1);
}
```

## <a name="see-also"></a>Consulte também

[Exemplo MFC MFCIE](https://github.com/Microsoft/VCSamples)<br/>
[Assistente de aplicativo do MFC](../../mfc/reference/mfc-application-wizard.md)<br/>
[Defina propriedades de build e compilador](../../build/working-with-project-properties.md)<br/>
[Páginas de propriedade](../../build/reference/property-pages-visual-cpp.md)<br/>
[Defina propriedades de build e compilador](../../build/working-with-project-properties.md)

