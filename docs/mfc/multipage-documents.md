---
title: Documentos multipágina
ms.date: 11/19/2018
helpviewer_keywords:
- pagination [MFC]
- overriding [MFC], View class functions for printing
- OnPrepareDC method [MFC]
- CPrintInfo structure [MFC], multipage documents
- OnEndPrinting method [MFC]
- protocols [MFC], printing protocol
- document pages vs. printer pages [MFC]
- printer mode [MFC]
- printing [MFC], multipage documents
- printers [MFC], printer mode
- documents [MFC], printing
- OnPreparePrinting method [MFC]
- OnPrint method [MFC]
- DoPreparePrinting method and pagination [MFC]
- OnDraw method [MFC], printing
- pagination [MFC], printing multipage documents
- printing [MFC], protocol
- pages [MFC], printing
- OnBeginPrinting method [MFC]
- multipage documents [MFC]
- printing [MFC], pagination
- documents [MFC], paginating
ms.assetid: 69626b86-73ac-4b74-b126-9955034835ef
ms.openlocfilehash: 81e03657977d31827c5c7c3d3272e3d4255a4a8b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295000"
---
# <a name="multipage-documents"></a>Documentos multipágina

Este artigo descreve o protocolo de impressão do Windows e explica como imprimir documentos que contêm mais de uma página. O artigo aborda os seguintes tópicos:

- [Protocolo de impressão](#_core_the_printing_protocol)

- [Substituindo funções de exibição de classe](#_core_overriding_view_class_functions)

- [Paginação](#_core_pagination)

- [Páginas de impressora vs. páginas do documento](#_core_printer_pages_vs.._document_pages)

- [Paginação de tempo de impressão](#_core_print.2d.time_pagination)

##  <a name="_core_the_printing_protocol"></a> O protocolo de impressão

Para imprimir um documento de várias páginas, o framework e o modo de exibição interagem da seguinte maneira. Primeiro o framework exibe a **impressão** caixa de diálogo, cria um contexto de dispositivo para a impressora e chama o [StartDoc](../mfc/reference/cdc-class.md#startdoc) função de membro da [CDC](../mfc/reference/cdc-class.md) objeto. Em seguida, para cada página do documento, o framework chama o [StartPage](../mfc/reference/cdc-class.md#startpage) função de membro da `CDC` objeto, instrui o objeto de exibição para imprimir a página e chamadas a [EndPage](../mfc/reference/cdc-class.md#endpage) função de membro. Se o modo de impressora deve ser alterado antes de iniciar uma página específica, o modo de exibição chama [ResetDC](../mfc/reference/cdc-class.md#resetdc), quais atualizações a [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) estrutura que contém as novas informações de modo de impressora. Quando todo o documento tiver sido impresso, o framework chama o [EndDoc](../mfc/reference/cdc-class.md#enddoc) função de membro.

##  <a name="_core_overriding_view_class_functions"></a> Substituindo funções de exibição de classe

O [CView](../mfc/reference/cview-class.md) classe define várias funções de membro que chamado pelo framework durante a impressão. Ao substituir essas funções em sua classe de exibição, você deve fornecer as conexões entre a lógica de impressão da estrutura e a lógica de impressão da sua classe de exibição. A tabela a seguir lista essas funções de membro.

### <a name="cviews-overridable-functions-for-printing"></a>Funções de substituível do CView para impressão

|Nome|Motivo para substituição|
|----------|---------------------------|
|[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)|Para inserir valores na caixa de diálogo Imprimir, especialmente o tamanho do documento|
|[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)|Para alocar fontes ou outros recursos GDI|
|[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)|Para ajustar os atributos do contexto do dispositivo para uma determinada página, ou para fazer a paginação de tempo de impressão|
|[OnPrint](../mfc/reference/cview-class.md#onprint)|Para uma determinada página de impressão|
|[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)|Para desalocar recursos GDI|

Você pode fazer o processamento relacionados à impressão em outras funções, bem, mas essas funções são aqueles que orientam o processo de impressão.

A figura a seguir ilustra as etapas envolvidas no processo de impressão e mostra onde cada um dos `CView`impressão do membro são chamadas de funções. O restante deste artigo explica a maioria dessas etapas mais detalhadamente. Outras partes do processo de impressão são descritas no artigo [alocar recursos de GDI](../mfc/allocating-gdi-resources.md).

![Imprimindo o processo de loop](../mfc/media/vc37c71.gif "processo de loop de impressão") <br/>
O Loop de impressão

##  <a name="_core_pagination"></a> Paginação

O framework armazena grande parte das informações sobre um trabalho de impressão em um [CPrintInfo](../mfc/reference/cprintinfo-structure.md) estrutura. Muitos dos valores no `CPrintInfo` pertencem à paginação; esses valores são acessíveis como mostrado na tabela a seguir.

### <a name="page-number-information-stored-in-cprintinfo"></a>Informações de número de páginas armazenadas em CPrintInfo

|Variável de membro ou<br /><br /> nomes de função|Número da página referenciado|
|-----------------------------------------------|----------------------------|
|`GetMinPage`/`SetMinPage`|Primeira página do documento|
|`GetMaxPage`/`SetMaxPage`|Última página do documento|
|`GetFromPage`|Primeira página a ser impressa|
|`GetToPage`|Última página a ser impressa|
|`m_nCurPage`|Página que está sendo impressa|

Início de números de página em 1, ou seja, a primeira página é numerada 1, não em 0. Para obter mais informações sobre esses e outros membros da [CPrintInfo](../mfc/reference/cprintinfo-structure.md), consulte o *referência da MFC*.

No início do processo de impressão, o framework chama o modo de exibição [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) função de membro, passando um ponteiro para um `CPrintInfo` estrutura. O Assistente de aplicativo fornece uma implementação de `OnPreparePrinting` que chama [DoPreparePrinting](../mfc/reference/cview-class.md#doprepareprinting), outra função de membro de `CView`. `DoPreparePrinting` é a função que exibe a caixa de diálogo Imprimir e cria um contexto de dispositivo de impressora.

Neste ponto, o aplicativo não sabe quantas páginas estão no documento. Ele usa os valores padrão 1 e 0xFFFF para os números da primeira e última página do documento. Se você souber quantas páginas possui seu documento, substituir `OnPreparePrinting` e chame [SetMaxPage]--brokenlink--(reference/cprintinfo-class.md#setmaxpage) para o `CPrintInfo` estrutura antes de enviá-lo para `DoPreparePrinting`. Isso lhe permite especificar o tamanho do documento.

`DoPreparePrinting` em seguida, exibe a caixa de diálogo de impressão. Ao retornar, o `CPrintInfo` estrutura contém os valores especificados pelo usuário. Se o usuário desejar imprimir apenas um intervalo selecionado de páginas, ele pode especificar o início e final de números de página na caixa de diálogo Imprimir. O framework recupera esses valores usando o `GetFromPage` e `GetToPage` funções de [CPrintInfo](../mfc/reference/cprintinfo-structure.md). Se o usuário não especificar um intervalo de páginas, o framework chama `GetMinPage` e `GetMaxPage` e usa os valores retornados para imprimir o documento inteiro.

Para cada página de um documento a ser impresso, o framework chama duas funções de membro em sua classe de exibição [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) e [OnPrint](../mfc/reference/cview-class.md#onprint)e passa cada função dois parâmetros: um ponteiro para um [ CDC](../mfc/reference/cdc-class.md) objeto e um ponteiro para um `CPrintInfo` estrutura. Cada vez que a estrutura chama `OnPrepareDC` e `OnPrint`, ele passa um valor diferente na *m_nCurPage* membro do `CPrintInfo` estrutura. Dessa forma a estrutura informa o modo de exibição ao qual página deve ser impresso.

O [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) função de membro também é usada para exibição na tela. Ele faz ajustes ao contexto de dispositivo antes que ocorra de desenho. `OnPrepareDC` serve a uma função semelhante na impressão, mas há algumas diferenças: primeiro, o `CDC` objeto representa um contexto de dispositivo de impressora em vez de um contexto de dispositivo da tela e, segundo, um `CPrintInfo` objeto é passado como um segundo parâmetro. (Esse parâmetro é **nulo** quando `OnPrepareDC` é chamado para exibição na tela.) Substituir `OnPrepareDC` fazer ajustes para o contexto de dispositivo com base em qual página está sendo impresso. Por exemplo, você pode mover a origem do visor e a região de recorte para garantir que a parte apropriada do documento será impressa.

O [OnPrint](../mfc/reference/cview-class.md#onprint) executa a função de membro a impressão real da página. O artigo [como padrão impressão é feito](../mfc/how-default-printing-is-done.md) mostra como o framework chama [OnDraw](../mfc/reference/cview-class.md#ondraw) com um contexto de dispositivo de impressora para executar a impressão. Mais precisamente, a estrutura chama `OnPrint` com um `CPrintInfo` estrutura e um contexto de dispositivo, e `OnPrint` passa o contexto de dispositivo para `OnDraw`. Substituir `OnPrint` para executar qualquer processamento que deve ser feito somente durante a impressão e não para a exibição de tela. Por exemplo, para imprimir os cabeçalhos ou rodapés de páginas (consulte o artigo [cabeçalhos e rodapés](../mfc/headers-and-footers.md) para obter mais informações). Em seguida, chame `OnDraw` de substituição do `OnPrint` para fazer a renderização comum tanto a exibição de tela e impressão.

O fato de que `OnDraw` faz a renderização para ambos tela de exibição e impressão significa que seu aplicativo é WYSIWYG: "O que você vê o que você obterá." No entanto, suponha que você não estiver escrevendo um aplicativo WYSIWYG. Por exemplo, considere um texto de editor que usa uma fonte em negrito para impressão, mas exibe códigos de controle para indicar o texto em negrito na tela. Nessa situação, você deve usar `OnDraw` estritamente para exibição na tela. Quando você substitui `OnPrint`, substitua a chamada para `OnDraw` com uma chamada para uma função de desenho separada. Essa função desenha o documento a maneira como ele aparece no papel, usando os atributos que você não são exibidos na tela.

##  <a name="_core_printer_pages_vs.._document_pages"></a> Vs de páginas de impressora. Páginas do documento

Quando você se referem aos números de página, às vezes, é necessário fazer a distinção entre o conceito da impressora de uma página e o conceito de um documento de uma página. Do ponto de vista da impressora, uma página é uma folha de papel. No entanto, uma folha de papel não necessariamente é igual a uma página do documento. Por exemplo, se você estiver imprimindo um boletim informativo, em que as folhas devem ser dobradas, uma folha de papel pode conter os dois as primeira e última páginas do documento, lado a lado. Da mesma forma, se você estiver imprimindo uma planilha, o documento não consistem em páginas em todos os. Em vez disso, uma folha de papel pode conter linhas de 1 a 20, colunas de 6 a 10.

A página todos os números das [CPrintInfo](../mfc/reference/cprintinfo-structure.md) estrutura se referem às páginas de impressora. A estrutura chama `OnPrepareDC` e `OnPrint` uma vez para cada folha de papel que passará por meio da impressora. Quando você substitui o [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) de função para especificar o tamanho do documento, você deve usar as páginas de impressora. Se não houver uma correspondência (ou seja, uma página da impressora é igual a uma página de documento), em seguida, isso é fácil. Se, por outro lado, as páginas de documento e páginas de impressora não correspondem diretamente, você deve converter entre eles. Por exemplo, considere a impressão de uma planilha. Ao substituir `OnPreparePrinting`, você deve calcular quantas folhas de papel será necessárias para imprimir toda a planilha e, em seguida, use esse valor ao chamar o `SetMaxPage` função de membro de `CPrintInfo`. Da mesma forma, ao substituir `OnPrepareDC`, você deve traduzir *m_nCurPage* dentro do intervalo de linhas e colunas que aparecerão nessa planilha específica e, em seguida, ajustar adequadamente a origem do visor.

##  <a name="_core_print.2d.time_pagination"></a> Paginação de tempo de impressão

Em algumas situações, sua classe de exibição pode não saber antecipadamente quanto tempo o documento é até que ele realmente foi impresso. Por exemplo, suponha que seu aplicativo não estiver WYSIWYG, portanto, comprimento de um documento na tela não corresponde ao seu tamanho quando impresso.

Isso faz com que um problema quando você substitui [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) para a sua classe de exibição: você não pode passar um valor para o `SetMaxPage` função da [CPrintInfo](../mfc/reference/cprintinfo-structure.md) estrutura, porque você não sabe o tamanho de um documento. Se o usuário não especificar um número de página para parar em usando a caixa de diálogo Imprimir, o framework não sabe quando parar o loop de impressão. É a única maneira de determinar quando parar o loop de impressão imprimir o documento e ver quando ele termina. Sua classe de exibição deve verificar o final do documento enquanto ele está sendo impressa e, em seguida, informar a estrutura quando o final for atingido.

A estrutura se baseia em sua classe de exibição [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) função para informá-lo quando parar. Após cada chamada para `OnPrepareDC`, a estrutura verifica um membro do `CPrintInfo` estrutura chamada *m_bContinuePrinting*. Seu valor padrão é **TRUE.** Desde que ela permaneça assim, o framework continua o loop de impressão. Se ele for definido como **falsos**, as paradas de estrutura. Para realizar a paginação de tempo de impressão, substitua `OnPrepareDC` para verificar se o final do documento foi atingido e definirão *m_bContinuePrinting* ao **FALSE** quando ele tem.

A implementação padrão de `OnPrepareDC` define *m_bContinuePrinting* à **falso** se a página atual é maior que 1. Isso significa que se o tamanho do documento não foi especificado, o framework pressupõe que o documento é uma página longa. Uma consequência disso é que você deve ter cuidado se você chamar a versão da classe base do `OnPrepareDC`. Não presuma que *m_bContinuePrinting* serão **verdadeiro** depois de chamar a versão da classe base.

### <a name="what-do-you-want-to-know-more-about"></a>O que você deseja saber mais sobre

- [Cabeçalhos e rodapés](../mfc/headers-and-footers.md)

- [Alocando recursos GDI](../mfc/allocating-gdi-resources.md)

## <a name="see-also"></a>Consulte também

[Imprimindo](../mfc/printing.md)<br/>
[Classe CView](../mfc/reference/cview-class.md)<br/>
[Classe CDC](../mfc/reference/cdc-class.md)
