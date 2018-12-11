---
title: Classe CLinkCtrl
ms.date: 11/04/2016
f1_keywords:
- CLinkCtrl
- AFXCMN/CLinkCtrl
- AFXCMN/CLinkCtrl::CLinkCtrl
- AFXCMN/CLinkCtrl::Create
- AFXCMN/CLinkCtrl::CreateEx
- AFXCMN/CLinkCtrl::GetIdealHeight
- AFXCMN/CLinkCtrl::GetIdealSize
- AFXCMN/CLinkCtrl::GetItem
- AFXCMN/CLinkCtrl::GetItemID
- AFXCMN/CLinkCtrl::GetItemState
- AFXCMN/CLinkCtrl::GetItemUrl
- AFXCMN/CLinkCtrl::HitTest
- AFXCMN/CLinkCtrl::SetItem
- AFXCMN/CLinkCtrl::SetItemID
- AFXCMN/CLinkCtrl::SetItemState
- AFXCMN/CLinkCtrl::SetItemUrl
helpviewer_keywords:
- CLinkCtrl [MFC], CLinkCtrl
- CLinkCtrl [MFC], Create
- CLinkCtrl [MFC], CreateEx
- CLinkCtrl [MFC], GetIdealHeight
- CLinkCtrl [MFC], GetIdealSize
- CLinkCtrl [MFC], GetItem
- CLinkCtrl [MFC], GetItemID
- CLinkCtrl [MFC], GetItemState
- CLinkCtrl [MFC], GetItemUrl
- CLinkCtrl [MFC], HitTest
- CLinkCtrl [MFC], SetItem
- CLinkCtrl [MFC], SetItemID
- CLinkCtrl [MFC], SetItemState
- CLinkCtrl [MFC], SetItemUrl
ms.assetid: d1cd876a-ecca-42db-8ac4-9cd327df0cd4
ms.openlocfilehash: b24b92006b73dff2ae9f091256ef8401efc64fe9
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178039"
---
# <a name="clinkctrl-class"></a>Classe CLinkCtrl

Fornece a funcionalidade do controle SysLink comum do Windows.

## <a name="syntax"></a>Sintaxe

```
class CLinkCtrl : public CWnd
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|[CLinkCtrl::CLinkCtrl](#clinkctrl)|Constrói um objeto `CLinkCtrl`.|

### <a name="public-methods"></a>Métodos Públicos

|Nome|Descrição|
|----------|-----------------|
|[CLinkCtrl::Create](#create)|Cria um controle de link e anexa-o para um `CLinkCtrl` objeto.|
|[CLinkCtrl::CreateEx](#createex)|Cria um controle de link com estilos estendidos e anexa-o para um `CLinkCtrl` objeto.|
|[CLinkCtrl::GetIdealHeight](#getidealheight)|Recupera a altura ideal do controle de link.|
|[CLinkCtrl::GetIdealSize](#getidealsize)|Calcula a altura preferencial do texto do link para o controle de link atual, dependendo da largura do link especificado.|
|[CLinkCtrl::GetItem](#getitem)|Recupera os estados e os atributos de um item de controle de link.|
|[CLinkCtrl::GetItemID](#getitemid)|Recupera a ID de um item de controle de link.|
|[CLinkCtrl::GetItemState](#getitemstate)|Recupera o estado do item de controle de link.|
|[CLinkCtrl::GetItemUrl](#getitemurl)|Recupera a URL representada pelo item de controle de link.|
|[CLinkCtrl::HitTest](#hittest)|Determina se o usuário clicou no link especificado.|
|[CLinkCtrl::SetItem](#setitem)|Define os estados e os atributos de um item de controle de link.|
|[CLinkCtrl::SetItemID](#setitemid)|Define a ID de um item de controle de link.|
|[CLinkCtrl::SetItemState](#setitemstate)|Define o estado do item de controle de link.|
|[CLinkCtrl::SetItemUrl](#setitemurl)|Define a URL representada pelo item de controle de link.|

## <a name="remarks"></a>Comentários

Um "controle de link" fornece uma maneira conveniente de incorporar links de hipertexto em uma janela. O controle real é uma janela que renderiza o texto marcado para cima e inicia os aplicativos apropriados quando o usuário clica em um link incorporado. Vários links têm suporte dentro de um controle e podem ser acessados por um índice baseado em zero.

Esse controle (e, portanto, o `CLinkCtrl` classe) está disponível somente para programas em execução no Windows XP e versões posteriores.

Para obter mais informações, consulte [controle SysLink](/windows/desktop/Controls/syslink-overview) no SDK do Windows.

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxcmn. h

##  <a name="clinkctrl"></a>  CLinkCtrl::CLinkCtrl

Constrói um objeto `CLinkCtrl`.

```
CLinkCtrl();
```

##  <a name="create"></a>  CLinkCtrl::Create

Cria um controle de link e anexa-o para um `CLinkCtrl` objeto.

```
virtual BOOL Create(
    LPCTSTR lpszLinkMarkup,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parâmetros

*lpszLinkMarkup*<br/>
Ponteiro para uma cadeia de caracteres terminada em zero que contém a área marcada para cima do texto a ser exibido. Para obter mais informações, consulte a seção "Acesso de marcação e Link" no tópico [visão geral de controles SysLink](/windows/desktop/Controls/syslink-overview).

*dwStyle*<br/>
Especifica o estilo do controle de link. Aplica qualquer combinação de estilos de controle. Ver [estilos de controle comuns](/windows/desktop/Controls/common-control-styles) no `Windows SDK` para obter mais informações.

*Rect*<br/>
Especifica o tamanho e a posição do controle de link. Ela pode ser um [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto ou uma [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estrutura.

*pParentWnd*<br/>
Especifica a janela pai do controle de link. Ele não deve ser NULL.

*nID*<br/>
Especifica a ID. do controle de link

### <a name="return-value"></a>Valor de retorno

TRUE se a inicialização foi bem-sucedida; Caso contrário, FALSE.

### <a name="remarks"></a>Comentários

Você constrói um `CLinkCtrl` objeto em duas etapas. Primeiro, chame o construtor e, em seguida, chame `Create`, que cria o controle de link e anexa-o para o `CLinkCtrl` objeto. Se você quiser usar estilos estendidos do windows com o seu controle, chame [CLinkCtrl::CreateEx](#createex) em vez de `Create`.

A segunda forma do `Create` método é preterido. Usar o primeiro formulário que especifica o *lpszLinkMarkup* parâmetro.

### <a name="example"></a>Exemplo

O exemplo de código a seguir define duas variáveis, denominadas `m_Link1` e `m_Link2`, que são usadas para acessar dois controles de link.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>Exemplo

O exemplo de código a seguir cria um controle de link com base no local de outro controle de link. O carregador de recursos cria o primeiro controle de link quando seu aplicativo é iniciado. Quando seu aplicativo insere o método OnInitDialog, você pode criar o segundo controle de link relativo à posição do primeiro controle de link. Em seguida, você pode redimensionar o segundo controle de link para ajustar o texto que ele exibe.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

##  <a name="createex"></a>  CLinkCtrl::CreateEx

Cria um controle de link com estilos estendidos e anexa-o para um `CLinkCtrl` objeto.

```
virtual BOOL CreateEx(
    LPCTSTR lpszLinkMarkup,
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL CreateEx(DWORD  dwExStyle,
    DWORD  dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT  nID);
```

### <a name="parameters"></a>Parâmetros

*lpszLinkMarkup*<br/>
Ponteiro para uma cadeia de caracteres terminada em zero que contém a área marcada para cima do texto a ser exibido. Para obter mais informações, consulte a seção "Acesso de marcação e Link" no tópico [visão geral de controles SysLink](/windows/desktop/Controls/syslink-overview).

*dwExStyle*<br/>
Especifica o estilo estendido do controle de link. Para obter uma lista dos estilos estendidos do Windows, consulte o *dwExStyle* parâmetro para [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) no SDK do Windows.

*dwStyle*<br/>
Especifica o estilo do controle de link. Aplica qualquer combinação de estilos de controle. Para obter mais informações, consulte [estilos de controle comuns](/windows/desktop/Controls/common-control-styles) no SDK do Windows.

*Rect*<br/>
Especifica o tamanho e a posição do controle de link. Ela pode ser um [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto ou uma [RECT](/windows/desktop/api/windef/ns-windef-tagrect) estrutura.

*pParentWnd*<br/>
Especifica a janela pai do controle de link. Ele não deve ser NULL.

*nID*<br/>
Especifica a ID. do controle de link

### <a name="return-value"></a>Valor de retorno

TRUE se a inicialização foi bem-sucedida; Caso contrário, FALSE.

### <a name="remarks"></a>Comentários

Use `CreateEx` em vez de [criar](#create) para aplicar as constantes de estilo estendidos do Windows.

A segunda forma do `CreateEx` método é preterido. Usar o primeiro formulário que especifica o *lpszLinkMarkup* parâmetro.

##  <a name="getidealheight"></a>  CLinkCtrl::GetIdealHeight

Recupera a altura ideal do controle de link.

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>Valor de retorno

A altura ideal do controle, em pixels.

### <a name="remarks"></a>Comentários

Essa função membro implementa o comportamento da mensagem do Win32 [LM_GETIDEALHEIGHT](/windows/desktop/Controls/lm-getidealheight), conforme descrito no SDK do Windows.

##  <a name="getidealsize"></a>  CLinkCtrl::GetIdealSize

Calcula a altura preferencial do texto do link para o controle de link atual, dependendo da largura do link especificado.

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>Parâmetros

|Parâmetro|Descrição|
|---------------|-----------------|
|*cxMaxWidth*|[in] A largura máxima do link, em pixels.|
|[out] \* *pSize*|Um ponteiro para um Windows [tamanho](/windows/desktop/api/windef/ns-windef-tagsize) estrutura. Quando este método retorna, o *cy* membro a `SIZE` estrutura contém a altura do texto do link ideal para a largura do texto de link que é especificada pelo *cxMaxWidth*. O *cx* membro da estrutura contém a largura do texto de link que é realmente necessária.|

### <a name="return-value"></a>Valor de retorno

A altura preferencial do texto do link, em pixels. O valor de retorno é o mesmo que o valor da *cy* membro do `SIZE` estrutura.

### <a name="remarks"></a>Comentários

Para obter um exemplo de `GetIdealSize` método, consulte o exemplo na [CLinkCtrl::Create](#create).

Esse método envia o [LM_GETIDEALSIZE](/windows/desktop/Controls/lm-getidealsize) mensagem, que é descrita no SDK do Windows.

##  <a name="getitem"></a>  CLinkCtrl::GetItem

Recupera os estados e os atributos de um item de controle de link.

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>Parâmetros

*pItem*<br/>
Um ponteiro para um [LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem) estrutura para receber informações sobre o item.

### <a name="return-value"></a>Valor de retorno

Retorna verdadeiro em caso de êxito, FALSE em caso de falha.

### <a name="remarks"></a>Comentários

Essa função membro implementa o comportamento da mensagem do Win32 [LM_GETITEM](/windows/desktop/Controls/lm-getitem), conforme descrito no SDK do Windows.

##  <a name="getitemid"></a>  CLinkCtrl::GetItemID

Recupera a ID de um item de controle de link.

```
BOOL GetItemID(
    int iLink,
    CString& strID) const;

BOOL GetItemID(
    int iLink,
    LPWSTR szID,
    UINT cchID) const;
```

### <a name="parameters"></a>Parâmetros

*iLink*<br/>
O índice de um item de controle de link.

*strID*<br/>
Um [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contém a ID do item especificado.

*szID*<br/>
Uma cadeia terminada em nulo que contém a ID do item especificado.

*cchID*<br/>
O tamanho em caracteres da *szID* buffer.

### <a name="return-value"></a>Valor de retorno

Retorna verdadeiro em caso de êxito, FALSE em caso de falha.

> [!NOTE]
>  Essa função também retornará FALSE se o buffer de *szID ou strID* é menor do que MAX_LINKID_TEXT.

### <a name="remarks"></a>Comentários

Recupera a ID de um item de controle de link específico. Para obter mais informações, consulte a mensagem do Win32 [LM_GETITEM](/windows/desktop/Controls/lm-getitem) no SDK do Windows.

##  <a name="getitemstate"></a>  CLinkCtrl::GetItemState

Recupera o estado do item de controle de link.

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>Parâmetros

*iLink*<br/>
O índice de um item de controle de link.

*pnState*<br/>
O valor do item de estado especificado.

*stateMask*<br/>
Combinação de sinalizadores que descrevem quais itens de estado para obter. Para obter uma lista de valores, consulte a descrição dos `state` membro na [LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem) estrutura. Itens permitidos são idênticas àquelas permitidos em `state`.

### <a name="return-value"></a>Valor de retorno

Retorna verdadeiro em caso de êxito, FALSE em caso de falha.

### <a name="remarks"></a>Comentários

Recupera o valor do item de estado especificado de um item de controle de link específico. Para obter mais informações, consulte a mensagem do Win32 [LM_GETITEM](/windows/desktop/Controls/lm-getitem) no SDK do Windows.

##  <a name="getitemurl"></a>  CLinkCtrl::GetItemUrl

Recupera a URL representada pelo item de controle de link.

```
BOOL GetItemUrl(
    int iLink,
    CString& strUrl) const;

BOOL GetItemUrl(
    int iLink,
    LPWSTR szUrl,
    UINT cchUrl) const;
```

### <a name="parameters"></a>Parâmetros

*iLink*<br/>
O índice de um item de controle de link.

*strUrl*<br/>
Um [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contém a URL representada pelo item especificado

*szUrl*<br/>
Uma cadeia de caracteres terminada em nulo que contém a URL representada pelo item especificado

*cchUrl*<br/>
O tamanho em caracteres da *szURL* buffer.

### <a name="return-value"></a>Valor de retorno

Retorna verdadeiro em caso de êxito, FALSE em caso de falha.

> [!NOTE]
>  Essa função também retornará FALSE se o buffer de *szUrl ou strUrl* é menor do que MAX_LINKID_TEXT.

### <a name="remarks"></a>Comentários

Recupera a URL representada pelo item de controle de link especificado. Para obter mais informações, consulte a mensagem do Win32 [LM_GETITEM](/windows/desktop/Controls/lm-getitem) no SDK do Windows.

##  <a name="hittest"></a>  CLinkCtrl::HitTest

Determina se o usuário clicou no link especificado.

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>Parâmetros

*phti*<br/>
Ponteiro para um `LHITTESTINFO` estrutura que contém todas as informações sobre o link que o usuário clicou.

### <a name="return-value"></a>Valor de retorno

Retorna verdadeiro em caso de êxito, FALSE em caso de falha.

### <a name="remarks"></a>Comentários

Essa função membro implementa o comportamento da mensagem do Win32 [LM_HITTEST](/windows/desktop/Controls/lm-hittest), conforme descrito no SDK do Windows.

##  <a name="setitem"></a>  CLinkCtrl::SetItem

Define os estados e os atributos de um item de controle de link.

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>Parâmetros

*pItem*<br/>
Um ponteiro para um [LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem) estrutura que contém as informações a serem definidas.

### <a name="return-value"></a>Valor de retorno

Retorna verdadeiro em caso de êxito, FALSE em caso de falha.

### <a name="remarks"></a>Comentários

Essa função membro implementa o comportamento da mensagem do Win32 [LM_SETITEM](/windows/desktop/Controls/lm-setitem), conforme descrito no SDK do Windows.

##  <a name="setitemid"></a>  CLinkCtrl::SetItemID

Recupera a ID de um item de controle de link.

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>Parâmetros

*iLink*<br/>
O índice de um item de controle de link.

*szID*<br/>
Uma cadeia terminada em nulo que contém a ID do item especificado.

### <a name="return-value"></a>Valor de retorno

Retorna verdadeiro em caso de êxito, FALSE em caso de falha.

### <a name="remarks"></a>Comentários

Define a ID de um item de controle de link específico. Para obter mais informações, consulte a mensagem do Win32 [LM_SETITEM](/windows/desktop/Controls/lm-setitem) no SDK do Windows.

##  <a name="setitemstate"></a>  CLinkCtrl::SetItemState

Recupera o estado do item de controle de link.

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>Parâmetros

*iLink*<br/>
O índice de um item de controle de link.

*pnState*<br/>
O valor do item de estado especificado que está sendo definido.

*stateMask*<br/>
Combinação de sinalizadores que descrevem o item de estado que está sendo definido. Para obter uma lista de valores, consulte a descrição dos `state` membro na [LITEM](/windows/desktop/api/commctrl/ns-commctrl-taglitem) estrutura. Itens permitidos são idênticas àquelas permitidos em `state`.

### <a name="return-value"></a>Valor de retorno

Retorna verdadeiro em caso de êxito, FALSE em caso de falha.

### <a name="remarks"></a>Comentários

Define o valor do item de estado especificado de um item de controle de link específico. Para obter mais informações, consulte a mensagem do Win32 [LM_SETITEM](/windows/desktop/Controls/lm-setitem) no SDK do Windows.

##  <a name="setitemurl"></a>  CLinkCtrl::SetItemUrl

Define a URL representada pelo item de controle de link.

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>Parâmetros

*iLink*<br/>
O índice de um item de controle de link.

*szUrl*<br/>
Uma cadeia de caracteres terminada em nulo que contém a URL representada pelo item especificado

### <a name="return-value"></a>Valor de retorno

Retorna verdadeiro em caso de êxito, FALSE em caso de falha.

### <a name="remarks"></a>Comentários

Define a URL representada pelo item de controle de link especificado. Para obter mais informações, consulte a mensagem do Win32 [LM_SETITEM](/windows/desktop/Controls/lm-setitem) no SDK do Windows.

## <a name="see-also"></a>Consulte também

[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classe CWnd](../../mfc/reference/cwnd-class.md)
