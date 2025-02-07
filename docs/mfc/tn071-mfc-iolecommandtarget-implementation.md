---
title: 'TN071: Implementação do MFC IOleCommandTarget'
ms.date: 06/28/2018
f1_keywords:
- IOleCommandTarget
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
ms.openlocfilehash: 7077211396c68750d47b91c7b2bb113370990f62
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511095"
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071: Implementação do MFC IOleCommandTarget

> [!NOTE]
> A observação técnica a seguir não foi atualizada desde que foi incluída pela primeira vez na documentação online. Como resultado, alguns procedimentos e tópicos podem estar desatualizados ou incorretos. Para obter as informações mais recentes, é recomendável que você pesquise o tópico de interesse no índice de documentação online.

A `IOleCommandTarget` interface permite que objetos e seus contêineres enviem comandos entre si. `Print`Por exemplo, as barras de ferramentas de um objeto podem conter botões para comandos como `Print Preview` `Save`, `New`,, e `Zoom`. Se esse objeto fosse inserido em um contêiner com suporte `IOleCommandTarget`, o objeto poderia habilitar seus botões e encaminhar os comandos para o contêiner para processamento quando o usuário clicou neles. Se um contêiner quisesse que o objeto incorporado fosse impresso, ele poderia fazer essa solicitação enviando um comando por meio da `IOleCommandTarget` interface do objeto inserido.

`IOleCommandTarget`é uma interface do tipo automação, na qual é usada por um cliente para invocar métodos em um servidor. No entanto `IOleCommandTarget` , o uso de economiza a sobrecarga de fazer chamadas por meio de interfaces de automação porque os programadores não `IDispatch`precisam usar o método normalmente caro `Invoke` de.

No MFC, a `IOleCommandTarget` interface é usada por servidores de documentos ativos para permitir que os contêineres de documentos ativos enviem comandos para o servidor. A classe de servidor de documento `CDocObjectServerItem`ativa,, usa mapas de interface [MFC (consulte TN038: Implementação](../mfc/tn038-mfc-ole-iunknown-implementation.md)MFC/OLE IUnknown) para implementar a `IOleCommandTarget` interface.

`IOleCommandTarget`também é implementado na `COleFrameHook` classe. `COleFrameHook`é uma classe MFC não documentada que implementa a funcionalidade de janela do quadro de contêineres de edição in-loco. `COleFrameHook`o também usa mapas de interface MFC para `IOleCommandTarget` implementar a interface. `COleFrameHook`a implementação de `IOleCommandTarget` encaminha os comandos OLE para `COleDocObjectItem`os contêineres de documento ativo derivados. Isso permite que qualquer contêiner de documento ativo do MFC receba mensagens de servidores de documentos ativos contidos.

## <a name="mfc-ole-command-maps"></a>Mapas de comando OLE MFC

Os desenvolvedores do MFC podem aproveitar `IOleCommandTarget` o usando mapas de comando OLE do MFC. Mapas de comando OLE são como mapas de mensagem porque podem ser usados para mapear comandos OLE para funções de membro da classe que contém o mapa de comando. Para fazer isso funcionar, coloque as macros no mapa de comando para especificar o grupo de comando OLE do comando que você deseja manipular, o comando OLE e a ID de comando da mensagem [WM_COMMAND](/windows/win32/menurc/wm-command) que será enviada quando o comando OLE for recebido. O MFC também fornece várias macros predefinidas para comandos OLE padrão. Para obter uma lista dos comandos OLE padrão que foram originalmente projetados para uso com Microsoft Office aplicativos, consulte a enumeração OLECMDID, que é definida em docobj. h.

Quando um comando OLE é recebido por um aplicativo MFC que contém um mapa de comando OLE, o MFC tenta encontrar a ID de comando e o grupo de comandos para o comando solicitado no mapa de comando OLE do aplicativo. Se uma correspondência for encontrada, uma mensagem WM_COMMAND será expedida para o aplicativo que contém o mapa de comando com a ID do comando solicitado. (Consulte a descrição `ON_OLECMD` abaixo.) Dessa forma, os comandos OLE expedidos para um aplicativo são convertidos em mensagens WM_COMMAND pelo MFC. Em seguida, as mensagens WM_COMMAND são roteadas pelos mapas de mensagens do aplicativo usando a arquitetura de [Roteamento de comandos](../mfc/command-routing.md) padrão do MFC.

Ao contrário dos mapas de mensagens, os mapas de comando OLE MFC não têm suporte do ClassWizard. Os desenvolvedores de MFC devem adicionar entradas de mapa de comando OLE e mapear comando OLE manualmente. Os mapas de comando OLE podem ser adicionados aos servidores de documentos ativos do MFC em qualquer classe que esteja na cadeia de roteamento de mensagens WM_COMMAND no momento em que o documento ativo estiver ativo no local em um contêiner. Essas classes incluem as classes do aplicativo derivadas de [CWinApp](../mfc/reference/cwinapp-class.md), [cvisualização](../mfc/reference/cview-class.md), [CDocument](../mfc/reference/cdocument-class.md)e [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md). Em contêineres de documento ativo, os mapas de comando OLE só podem ser adicionados à classe derivada de [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md). Além disso, em contêineres de documento ativo, as mensagens WM_COMMAND só serão expedidas para o mapa da `COleDocObjectItem`mensagem na classe derivada.

## <a name="ole-command-map-macros"></a>Macros de mapa de comando OLE

Use as macros a seguir para adicionar a funcionalidade de mapa de comando à sua classe:

```cpp
DECLARE_OLECMD_MAP ()
```

Essa macro vai na declaração de classe (normalmente no arquivo de cabeçalho) da classe que contém o mapa de comando.

```cpp
BEGIN_OLECMD_MAP(theClass, baseClass)
```

*theClass*<br/>
Nome da classe que contém o mapa de comando.

*baseClass*<br/>
Nome da classe base da classe que contém o mapa de comando.

Esta macro marca o início do mapa de comando. Use essa macro no arquivo de implementação para a classe que contém o mapa de comando.

```
END_OLECMD_MAP()
```

Esta macro marca o final do mapa de comando. Use essa macro no arquivo de implementação para a classe que contém o mapa de comando. Essa macro sempre deve seguir a macro BEGIN_OLECMD_MAP.

```
ON_OLECMD(pguid, olecmdid, id)
```

*pguid*<br/>
Ponteiro para o GUID do grupo de comandos do comando OLE. Esse parâmetro é **nulo** para o grupo de comandos OLE padrão.

*olecmdid*<br/>
ID de comando OLE do comando a ser invocado.

*id*<br/>
ID da mensagem WM_COMMAND a ser enviada ao aplicativo que contém o mapa de comando quando este comando OLE é invocado.

Use a macro ON_OLECMD no mapa de comandos para adicionar entradas para os comandos OLE que você deseja manipular. Quando os comandos OLE forem recebidos, eles serão convertidos na mensagem WM_COMMAND especificada e roteados pelo mapa de mensagens do aplicativo usando a arquitetura de roteamento de comandos padrão do MFC.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como adicionar a funcionalidade de manipulação de comando OLE a um servidor de documento ativo do MFC para manipular o comando OLE [OLECMDID_PRINT](/windows/win32/api/docobj/ne-docobj-olecmdid) . Este exemplo pressupõe que você usou AppWizard para gerar um aplicativo MFC que é um servidor de documentos ativo.

1. No arquivo `CView`de cabeçalho de sua classe derivada, adicione a macro DECLARE_OLECMD_MAP à declaração de classe.

    > [!NOTE]
    > Use a `CView`classe-derivada porque ela é uma das classes no servidor de documentos ativo que está na cadeia de roteamento de mensagens WM_COMMAND.

    ```cpp
    class CMyServerView : public CView
    {
    protected: // create from serialization only
        CMyServerView();
        DECLARE_DYNCREATE(CMyServerView)
        DECLARE_OLECMD_MAP()
        // . . .
    };
    ```

2. No arquivo de implementação para a `CView`classe derivada, adicione as macros BEGIN_OLECMD_MAP e END_OLECMD_MAP:

    ```cpp
    BEGIN_OLECMD_MAP(CMyServerView, CView)

    END_OLECMD_MAP()
    ```

3. Para manipular o comando OLE Print padrão, adicione uma macro [ON_OLECMD](reference/message-map-macros-mfc.md#on_olecmd) ao mapa de comando ESPECIFICANDO a ID de comando OLE para o comando de impressão padrão e **ID_FILE_PRINT** para o WM_COMMAND ID. **ID_FILE_PRINT** é a ID de comando de impressão padrão usada pelos aplicativos MFC gerados pelo AppWizard:

    ```
    BEGIN_OLECMD_MAP(CMyServerView, CView)
        ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)
    END_OLECMD_MAP()
    ```

Observe que uma das macros de comando OLE padrão, definida em AfxDocOb. h, pode ser usada no lugar da macro ON_OLECMD porque **OLECMDID_PRINT** é uma ID de comando OLE padrão. A macro ON_OLECMD_PRINT executará a mesma tarefa que a macro ON_OLECMD mostrada acima.

Quando um aplicativo de contêiner envia esse servidor a um comando **OLECMDID_PRINT** por meio `IOleCommandTarget` da interface do servidor, o manipulador de comando de impressão do MFC será invocado no servidor, fazendo com que o servidor imprima o aplicativo. O código do contêiner de documento ativo para invocar o comando Print adicionado nas etapas acima seria semelhante ao seguinte:

```cpp
void CContainerCntrItem::DoOleCmd()
{
    IOleCommandTarget *pCmd = NULL;
    HRESULT hr = E_FAIL;
    OLECMD ocm={OLECMDID_PRINT, 0};

    hr = m_lpObject->QueryInterface(
        IID_IOleCommandTarget,reinterpret_cast<void**>(&pCmd));

    if (FAILED(hr))
        return;

    hr = pCmd->QueryStatus(NULL, 1, &ocm, NULL);

    if (SUCCEEDED(hr) && (ocm.cmdf& OLECMDF_ENABLED))
    {
        //Command is available and enabled so call it
        COleVariant vIn;
        COleVariant vOut;
        hr = pCmd->Exec(NULL, OLECMDID_PRINT,
            OLECMDEXECOPT_DODEFAULT, &vIn, &vOut);
        ASSERT(SUCCEEDED(hr));
    }
    pCmd->Release();
}
```

## <a name="see-also"></a>Consulte também

[Observações técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Observações técnicas por categoria](../mfc/technical-notes-by-category.md)
