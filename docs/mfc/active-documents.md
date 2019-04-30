---
title: Documentos ativos
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC]
- active documents [MFC], requirements
- view objects [MFC], requirements
- OLE [MFC], active documents
- views [MFC], active documents
- active documents [MFC], views
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
ms.openlocfilehash: 519dd51ab9b46adf862999104e97c6e478ccd86b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394943"
---
# <a name="active-documents"></a>Documentos ativos

Documentos ativos ampliar a tecnologia de documento composto de OLE. Essas extensões são fornecidas na forma de interfaces adicionais que gerenciam os modos de exibição, para que os objetos podem funcionar dentro de contêineres e ainda manter o controle sobre sua exibição e funções de impressão. Esse processo torna possível exibir documentos em quadros externos (como o Microsoft Office Binder ou o Microsoft Internet Explorer) e em quadros nativos (por exemplo, as portas de modo de exibição do produto).

Esta seção descreve a funcional [requisitos de documentos ativos](#requirements_for_active_documents). O documento ativo possui um conjunto de dados e tem acesso ao armazenamento em que os dados podem ser salvo e recuperados. Ele pode criar e gerenciar uma ou mais exibições em seus dados. Além de permitirem que as interfaces de ativação no local de documentos OLE e incorporação usual, o documento ativo se comunica sua capacidade de criar exibições por meio de `IOleDocument`. Por meio dessa interface, o contêiner pode pedir para criar (e possivelmente enumerar) do documento ativo pode exibir os modos de exibição. Por meio dessa interface, o documento ativo também pode fornecer informações diversas sobre si mesmo, como se ele dá suporte a vários modos de exibição ou retângulos complexos.

A seguir está o `IOleDocument` interface. Observe que o `IEnumOleDocumentViews` interface é um enumerador OLE padrão para `IOleDocumentView*` tipos.

```
interface IOleDocument : IUnknown
    {
    HRESULT CreateView(
        [in] IOleInPlaceSite *pIPSite,
        [in] IStream *pstm,
        [in] DWORD dwReserved,
        [out] IOleDocumentView **ppView);

    HRESULT GetDocMiscStatus([out] DWORD *pdwStatus);

    HRESULT EnumViews(
        [out] IEnumOleDocumentViews **ppEnum,
        [out] IOleDocumentView **ppView);
    }
```

Cada documento ativo deve ter um provedor de quadro de exibição com essa interface. Se o documento não é inserido em um contêiner, o próprio servidor de documento ativo deve fornecer o quadro de exibição. No entanto, quando o documento ativo é inserido em um contêiner de documento ativo, o contêiner fornece o quadro de exibição.

Um documento ativo pode criar um ou mais tipos de [modos de exibição](#requirements_for_view_objects) de seus dados (por exemplo, normal, de estrutura de tópicos, layout de página e assim por diante). Modos de exibição atuam como filtros por meio do qual os dados podem ser vistos. Mesmo que o documento tem apenas um tipo de exibição, você ainda pode desejar dar suporte a vários modos de exibição como um meio de oferecer suporte a novas funcionalidades de janela (por exemplo, o **nova janela** item na **janela** menu do Office aplicativos).

##  <a name="requirements_for_active_documents"></a> Requisitos para documentos ativos

Um documento ativo que pode ser exibido em um contêiner de documento ativo deve:

- Usar arquivos compostos do OLE como seu mecanismo de armazenamento implementando `IPersistStorage`.

- Suporte os recursos básicos de incorporação de OLE documentos, incluindo **criar do arquivo**. Isso exige que as interfaces `IPersistFile`, `IOleObject`, e `IDataObject`.

- Suporte a um ou mais modos de exibição, cada um deles é capaz de ativação no local. Ou seja, os modos de exibição devem oferecer suporte à interface `IOleDocumentView` , bem como as interfaces `IOleInPlaceObject` e `IOleInPlaceActiveObject` (usando o contêiner `IOleInPlaceSite` e `IOleInPlaceFrame` interfaces).

- Suporte as interfaces de padrão de documento ativo `IOleDocument`, `IOleCommandTarget`, e `IPrint`.

Dados de Conhecimento de quando e como usar as interfaces do lado do contêiner está implícita nesses requisitos.

##  <a name="requirements_for_view_objects"></a> Requisitos para objetos de exibição

Um documento ativo pode criar um ou mais modos de exibição de seus dados. Funcionalmente, essas exibições são como as portas em um método específico para exibir os dados. Se um documento ativo somente dá suporte a uma única exibição, o documento ativo e o único modo de exibição podem ser implementados usando uma única classe. `IOleDocument::CreateView` Retorna o mesmo objeto `IOleDocumentView` ponteiro de interface.

Para ser representado dentro de um contêiner de documento ativo, um componente de exibição deve suportar `IOleInPlaceObject` e `IOleInPlaceActiveObject` além `IOleDocumentView`:

```
interface IOleDocumentView : IUnknown
    {
    HRESULT SetInPlaceSite([in] IOleInPlaceSite *pIPSite);
    HRESULT GetInPlaceSite([out] IOleInPlaceSite **ppIPSite);
    HRESULT GetDocument([out] IUnknown **ppunk);
    [input_sync] HRESULT SetRect([in] LPRECT prcView);
    HRESULT GetRect([in] LPRECT prcView);
    [input_sync] HRESULT SetRectComplex(
        [in] LPRECT prcView,
        [in] LPRECT prcHScroll,
        [in] LPRECT prcVScroll,
        [in] LPRECT prcSizeBox);
    HRESULT Show([in] BOOL fShow);
    HRESULT UIActivate([in] BOOL fUIActivate);
    HRESULT Open(void);
    HRESULT CloseView([in] DWORD dwReserved);
    HRESULT SaveViewState([in] IStream *pstm);
    HRESULT ApplyViewState([in] IStream *pstm);
    HRESULT Clone(
        [in] IOleInPlaceSite *pIPSiteNew,
        [out] IOleDocumentView **ppViewNew);
    }
```

Cada exibição tem um site de exibição associada, que encapsula o quadro de exibição e a porta de exibição (HWND e uma área retangular nessa janela). O site expõe essa funcionalidade no entanto o padrão `IOleInPlaceSite` interface. Observe que é possível ter mais de uma porta de exibição em um único HWND.

Normalmente, cada tipo de exibição tem uma representação impressa diferente. Portanto, exibições e os sites do modo de exibição correspondente devem implementar as interfaces de impressão se `IPrint` e `IContinueCallback`, respectivamente. O quadro de exibição deve negociar com o provedor de exibição por meio de `IPrint` quando a impressão começará, para que os cabeçalhos, rodapés, margens e elementos relacionados são impressos corretamente. O provedor de exibição notifica o quadro de eventos relacionados à impressão por meio de `IContinueCallback`. Para obter mais informações sobre o uso dessas interfaces, consulte [impressão programática](../mfc/programmatic-printing.md).

Observe que se um documento ativo somente dá suporte a uma única exibição, em seguida, o documento ativo e o único modo de exibição podem ser implementados usando uma única classe concreta. `IOleDocument::CreateView` simplesmente retorna o mesmo objeto `IOleDocumentView` ponteiro de interface. Em resumo, não é necessário que haver duas instâncias de objeto separado quando apenas uma exibição é necessária.

Um objeto de exibição também pode ser um destino do comando. Implementando `IOleCommandTarget` um modo de exibição pode receber comandos que se originam na interface do usuário do contêiner (como **New**, **abra**, **Salvar como**,  **Impressão** sobre o **arquivo** menu; e **cópia**, **colar**, **desfazer** no **editar** menu). Para obter mais informações, consulte [tratamento de mensagem e destinos de comando](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Consulte também

[Contenção de documentos ativos](../mfc/active-document-containment.md)
