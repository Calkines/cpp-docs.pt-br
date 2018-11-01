---
title: Classe CStatic
ms.date: 11/04/2016
f1_keywords:
- CStatic
- AFXWIN/CStatic
- AFXWIN/CStatic::CStatic
- AFXWIN/CStatic::Create
- AFXWIN/CStatic::DrawItem
- AFXWIN/CStatic::GetBitmap
- AFXWIN/CStatic::GetCursor
- AFXWIN/CStatic::GetEnhMetaFile
- AFXWIN/CStatic::GetIcon
- AFXWIN/CStatic::SetBitmap
- AFXWIN/CStatic::SetCursor
- AFXWIN/CStatic::SetEnhMetaFile
- AFXWIN/CStatic::SetIcon
helpviewer_keywords:
- CStatic [MFC], CStatic
- CStatic [MFC], Create
- CStatic [MFC], DrawItem
- CStatic [MFC], GetBitmap
- CStatic [MFC], GetCursor
- CStatic [MFC], GetEnhMetaFile
- CStatic [MFC], GetIcon
- CStatic [MFC], SetBitmap
- CStatic [MFC], SetCursor
- CStatic [MFC], SetEnhMetaFile
- CStatic [MFC], SetIcon
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
ms.openlocfilehash: 622172d369818a7a503945bcd3cf064662f38266
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576703"
---
# <a name="cstatic-class"></a>Classe CStatic

Fornece a funcionalidade de um controle estático do Windows.

## <a name="syntax"></a>Sintaxe

```
class CStatic : public CWnd
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|[CStatic::CStatic](#cstatic)|Constrói um objeto `CStatic`.|

### <a name="public-methods"></a>Métodos Públicos

|Nome|Descrição|
|----------|-----------------|
|[CStatic::Create](#create)|Cria o controle estático do Windows e anexa-o para o `CStatic` objeto.|
|[CStatic::DrawItem](#drawitem)|Substituição para desenhar um controle estático desenhado pelo proprietário.|
|[CStatic::GetBitmap](#getbitmap)|Recupera o identificador do bitmap definido anteriormente com [SetBitmap](#setbitmap).|
|[CStatic::GetCursor](#getcursor)|Recupera o identificador da imagem do cursor definido anteriormente com [SetCursor](#setcursor).|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Recupera o identificador do metarquivo aprimorado definido anteriormente com [SetEnhMetaFile](#setenhmetafile).|
|[CStatic::GetIcon](#geticon)|Recupera o identificador do ícone definido anteriormente com [SetIcon](#seticon).|
|[CStatic::SetBitmap](#setbitmap)|Especifica um bitmap a ser exibido no controle estático.|
|[CStatic::SetCursor](#setcursor)|Especifica uma imagem de cursor a ser exibido no controle estático.|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Especifica um metarquivo avançado a ser exibido no controle estático.|
|[CStatic::SetIcon](#seticon)|Especifica um ícone a ser exibido no controle estático.|

## <a name="remarks"></a>Comentários

Um controle estático exibe uma cadeia de caracteres de texto, caixa, retângulo, ícone, cursor, bitmap ou Metarquivo aprimorado. Ele pode ser usado para rotular, caixa ou separar a outros controles. Normalmente, um controle estático não aceita nenhuma entrada e não fornece nenhuma saída; No entanto, ele pode notificar seu pai de cliques do mouse se ela for criada com estilo SS_NOTIFY.

Crie um controle estático em duas etapas. Primeiro, chame o construtor para construir o `CStatic` do objeto e, em seguida, chamar o [Create](#create) função de membro para criar o controle estático e anexá-lo para o `CStatic` objeto.

Se você criar uma `CStatic` objeto dentro de uma caixa de diálogo (por meio de um recurso de caixa de diálogo), o `CStatic` objeto será destruído automaticamente quando o usuário fecha a caixa de diálogo.

Se você criar um `CStatic` do objeto dentro de uma janela, você também precisará destruí-lo. Um `CStatic` objeto criado na pilha de dentro de uma janela é destruído automaticamente. Se você criar o `CStatic` objeto no heap usando a **novos** função, você deve chamar **excluir** no objeto a destruí-la quando você terminar com ele.

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxwin. h

##  <a name="create"></a>  CStatic::Create

Cria o controle estático do Windows e anexa-o para o `CStatic` objeto.

```
virtual BOOL Create(
    LPCTSTR lpszText,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID = 0xffff);
```

### <a name="parameters"></a>Parâmetros

*lpszText*<br/>
Especifica o texto a ser colocado no controle. Se for NULL, nenhum texto será visível.

*dwStyle*<br/>
Especifica o estilo da janela do controle estático. Aplicar qualquer combinação de [estilos de controle estático](../../mfc/reference/styles-used-by-mfc.md#static-styles) ao controle.

*Rect*<br/>
Especifica a posição e tamanho do controle estático. Ela pode ser um `RECT` estrutura ou um `CRect` objeto.

*pParentWnd*<br/>
Especifica o `CStatic` janela pai, geralmente um `CDialog` objeto. Ele não deve ser NULL.

*nID*<br/>
Especifica a ID do controle. do controle estático

### <a name="return-value"></a>Valor de retorno

Diferente de zero se bem-sucedido; Caso contrário, 0.

### <a name="remarks"></a>Comentários

Construir um `CStatic` objeto em duas etapas. Primeiro, chame o construtor `CStatic`e, em seguida, chame `Create`, que cria o controle estático do Windows e anexa-o para o `CStatic` objeto.

Aplicar o seguinte [estilos de janela](../../mfc/reference/styles-used-by-mfc.md#window-styles) para um controle estático:

- Sempre WS_CHILD

- Normalmente, WS_VISIBLE

- WS_DISABLED raramente

Se você pretende exibir um bitmap, cursor, ícone ou metarquivo no controle estático, você precisará aplicar um dos seguintes [estilos estáticos](../../mfc/reference/styles-used-by-mfc.md#static-styles):

- SS_BITMAP usar esse estilo para bitmaps.

- SS_ICON usar esse estilo de ícones e cursores.

- SS_ENHMETAFILE usar esse estilo para metarquivos.

Para cursores, bitmaps ou ícones, você talvez queira usar o estilo a seguir:

- Use SS_CENTERIMAGE para centralizar a imagem no controle estático.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

##  <a name="cstatic"></a>  CStatic::CStatic

Constrói um objeto `CStatic`.

```
CStatic();
```

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

##  <a name="drawitem"></a>  CStatic::DrawItem

Chamado pelo framework para desenhar um controle estático desenhado pelo proprietário.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parâmetros

*lpDrawItemStruct*<br/>
Um ponteiro para um [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) estrutura. A estrutura contém informações sobre o item a ser desenhado e o tipo de desenho necessárias.

### <a name="remarks"></a>Comentários

Substituir essa função para implementar o desenho de um desenho proprietário `CStatic` objeto (o controle tem o estilo SS_OWNERDRAW).

##  <a name="getbitmap"></a>  CStatic::GetBitmap

Obtém o identificador do bitmap, definido anteriormente com [SetBitmap](#setbitmap), que é associado com `CStatic`.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Valor de retorno

Um identificador para o bitmap atual ou nulo se nenhum bitmap tiver sido definido.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="getcursor"></a>  CStatic::GetCursor

Obtém o identificador do cursor, definido anteriormente com [SetCursor](#setcursor), que é associado com `CStatic`.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Valor de retorno

Um identificador para o cursor atual ou nulo se nenhum cursor tiver sido definido.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="getenhmetafile"></a>  CStatic::GetEnhMetaFile

Obtém o identificador do metarquivo, definido anteriormente com [SetEnhMetafile](#setenhmetafile), que é associado com `CStatic`.

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>Valor de retorno

Um identificador de metarquivo avançado atual ou nulo se nenhum metarquivo avançado tiver sido definido.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="geticon"></a>  CStatic::GetIcon

Obtém o identificador do ícone, definido anteriormente com [SetIcon](#seticon), que é associado com `CStatic`.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Valor de retorno

Um identificador para o ícone atual ou nulo se nenhum ícone tiver sido definido.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

##  <a name="setbitmap"></a>  CStatic::SetBitmap

Associa um novo bitmap com o controle estático.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parâmetros

*hBitmap*<br/>
Identificador do bitmap a ser desenhada em um controle estático.

### <a name="return-value"></a>Valor de retorno

O identificador do bitmap que foi previamente associado o controle estático, ou nulo se nenhum bitmap foi associado ao controle estático.

### <a name="remarks"></a>Comentários

O bitmap será desenhado automaticamente no controle estático. Por padrão, ela será desenhada no canto superior esquerdo e o controle estático será redimensionado para o tamanho do bitmap.

Você pode usar vários janela e estilos de controle estático, incluindo estes:

- SS_BITMAP usam esse estilo sempre para bitmaps.

- Use SS_CENTERIMAGE para centralizar a imagem no controle estático. Se a imagem for maior que o controle estático, ele será recortado. Se ele for menor que o controle estático, o espaço vazio ao redor da imagem será preenchido pela cor do pixel no canto superior esquerdo do bitmap.

- O MFC fornece a classe `CBitmap`, que pode ser usado quando você tem mais com uma imagem de bitmap que apenas chamam o Win32 funcione `LoadBitmap`. `CBitmap`, que contém um tipo de objeto GDI, geralmente é usado em cooperação com o `CStatic`, que é um `CWnd` classe que é usado para exibir um objeto gráfico como um controle estático.

`CImage` é uma classe ATL/MFC que permite que mais você trabalhar facilmente com bitmaps independentes de dispositivo (DIB). Para obter mais informações, consulte [classe CImage](../../atl-mfc-shared/reference/cimage-class.md).

- Uso típico é dar `CStatic::SetBitmap` um objeto GDI que é retornado pelo operador HBITMAP de um `CBitmap` ou `CImage` objeto. O código para fazer isso se parece com a linha a seguir.

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```
O exemplo a seguir cria dois `CStatic` objetos no heap. Em seguida, carrega um com um bitmap de sistema usando `CBitmap::LoadOEMBitmap` e o outro de um arquivo usando `CImage::Load`.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="setcursor"></a>  CStatic::SetCursor

Associa uma nova imagem de cursor com o controle estático.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parâmetros

*hCursor*<br/>
Identificador do cursor a ser desenhada em um controle estático.

### <a name="return-value"></a>Valor de retorno

O identificador do cursor anteriormente associado com o controle estático, ou nulo se nenhum cursor foi associado ao controle estático.

### <a name="remarks"></a>Comentários

O cursor será desenhado automaticamente no controle estático. Por padrão, ela será desenhada no canto superior esquerdo e o controle estático será redimensionado para o tamanho do cursor.

Você pode usar vários janela e estilos de controle estático, incluindo o seguinte:

- SS_ICON usam esse estilo sempre para ícones e cursores.

- Use SS_CENTERIMAGE Centralizar no controle estático. Se a imagem for maior que o controle estático, ele será recortado. Se ele for menor que o controle estático, o espaço vazio ao redor da imagem será preenchido com a cor do plano de fundo do controle estático.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="setenhmetafile"></a>  CStatic::SetEnhMetaFile

Associa uma nova imagem de metarquivo avançado com o controle estático.

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>Parâmetros

*hMetaFile*<br/>
Identificador do metarquivo aprimorado a ser desenhada em um controle estático.

### <a name="return-value"></a>Valor de retorno

O identificador do metarquivo aprimorado anteriormente associado com o controle estático, ou nulo se nenhum Metarquivo Avançado foi associado ao controle estático.

### <a name="remarks"></a>Comentários

O metarquivo avançado será desenhado automaticamente no controle estático. O metarquivo avançado é dimensionado para ajustar o tamanho do controle estático.

Você pode usar vários janela e estilos de controle estático, incluindo o seguinte:

- SS_ENHMETAFILE usar sempre esse estilo de metarquivo avançado.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="seticon"></a>  CStatic::SetIcon

Associa uma nova imagem de ícone com o controle estático.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parâmetros

*hIcon*<br/>
Identificador do ícone a ser desenhada em um controle estático.

### <a name="return-value"></a>Valor de retorno

O identificador do ícone associado anteriormente com o controle estático, ou nulo se nenhum ícone foi associado ao controle estático.

### <a name="remarks"></a>Comentários

O ícone será desenhado automaticamente no controle estático. Por padrão, ela será desenhada no canto superior esquerdo e o controle estático será redimensionado para o tamanho do ícone.

Você pode usar vários janela e estilos de controle estático, incluindo o seguinte:

- SS_ICON usam esse estilo sempre para ícones e cursores.

- Use SS_CENTERIMAGE Centralizar no controle estático. Se a imagem for maior que o controle estático, ele será recortado. Se ele for menor que o controle estático, o espaço vazio ao redor da imagem será preenchido com a cor do plano de fundo do controle estático.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>Consulte também

[Classe CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classe CWnd](../../mfc/reference/cwnd-class.md)<br/>
[Classe CButton](../../mfc/reference/cbutton-class.md)<br/>
[Classe CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[Classe CEdit](../../mfc/reference/cedit-class.md)<br/>
[Classe CListBox](../../mfc/reference/clistbox-class.md)<br/>
[Classe CScrollBar](../../mfc/reference/cscrollbar-class.md)<br/>
[Classe CDialog](../../mfc/reference/cdialog-class.md)
