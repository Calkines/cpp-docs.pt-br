---
title: Classe CEditView
ms.date: 11/04/2016
f1_keywords:
- CEditView
- AFXEXT/CEditView
- AFXEXT/CEditView::CEditView
- AFXEXT/CEditView::FindText
- AFXEXT/CEditView::GetBufferLength
- AFXEXT/CEditView::GetEditCtrl
- AFXEXT/CEditView::GetPrinterFont
- AFXEXT/CEditView::GetSelectedText
- AFXEXT/CEditView::LockBuffer
- AFXEXT/CEditView::PrintInsideRect
- AFXEXT/CEditView::SerializeRaw
- AFXEXT/CEditView::SetPrinterFont
- AFXEXT/CEditView::SetTabStops
- AFXEXT/CEditView::UnlockBuffer
- AFXEXT/CEditView::OnFindNext
- AFXEXT/CEditView::OnReplaceAll
- AFXEXT/CEditView::OnReplaceSel
- AFXEXT/CEditView::OnTextNotFound
- AFXEXT/CEditView::dwStyleDefault
helpviewer_keywords:
- CEditView [MFC], CEditView
- CEditView [MFC], FindText
- CEditView [MFC], GetBufferLength
- CEditView [MFC], GetEditCtrl
- CEditView [MFC], GetPrinterFont
- CEditView [MFC], GetSelectedText
- CEditView [MFC], LockBuffer
- CEditView [MFC], PrintInsideRect
- CEditView [MFC], SerializeRaw
- CEditView [MFC], SetPrinterFont
- CEditView [MFC], SetTabStops
- CEditView [MFC], UnlockBuffer
- CEditView [MFC], OnFindNext
- CEditView [MFC], OnReplaceAll
- CEditView [MFC], OnReplaceSel
- CEditView [MFC], OnTextNotFound
- CEditView [MFC], dwStyleDefault
ms.assetid: bf38255c-fcbe-450c-95b2-3c5e35f86c37
ms.openlocfilehash: e9b7dea980e607c776e2d50c679042c765080fdb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506721"
---
# <a name="ceditview-class"></a>Classe CEditView

Um tipo de classe View que fornece a funcionalidade de um controle de edição do Windows e pode ser usada para implementar a funcionalidade de editor de texto simples.

## <a name="syntax"></a>Sintaxe

```
class CEditView : public CCtrlView
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[CEditView::CEditView](#ceditview)|Constrói um objeto do tipo `CEditView`.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CEditView::FindText](#findtext)|Pesquisa uma cadeia de caracteres dentro do texto.|
|[CEditView::GetBufferLength](#getbufferlength)|Obtém o comprimento do buffer de caracteres.|
|[CEditView::GetEditCtrl](#geteditctrl)|Fornece acesso à `CEdit` parte de um `CEditView` objeto (o controle de edição do Windows).|
|[CEditView::GetPrinterFont](#getprinterfont)|Recupera a fonte da impressora atual.|
|[CEditView::GetSelectedText](#getselectedtext)|Recupera a seleção de texto atual.|
|[CEditView::LockBuffer](#lockbuffer)|Bloqueia o buffer.|
|[CEditView::PrintInsideRect](#printinsiderect)|Renderiza o texto dentro de um determinado retângulo.|
|[CEditView::SerializeRaw](#serializeraw)|Serializa um `CEditView` objeto em disco como texto bruto.|
|[CEditView::SetPrinterFont](#setprinterfont)|Define uma nova fonte de impressora.|
|[CEditView::SetTabStops](#settabstops)|Define as paradas de tabulação para exibição e impressão de tela.|
|[CEditView::UnlockBuffer](#unlockbuffer)|Desbloqueia o buffer.|

### <a name="protected-methods"></a>Métodos Protegidos

|Nome|Descrição|
|----------|-----------------|
|[CEditView::OnFindNext](#onfindnext)|Localiza a próxima ocorrência de uma cadeia de texto.|
|[CEditView::OnReplaceAll](#onreplaceall)|Substitui todas as ocorrências de determinada cadeia de caracteres por uma nova cadeia de caracteres.|
|[CEditView::OnReplaceSel](#onreplacesel)|Substitui a seleção atual.|
|[CEditView::OnTextNotFound](#ontextnotfound)|Chamado quando uma operação Localizar falha ao corresponder a qualquer texto adicional.|

### <a name="public-data-members"></a>Membros de Dados Públicos

|Nome|Descrição|
|----------|-----------------|
|[CEditView::dwStyleDefault](#dwstyledefault)|Estilo padrão para objetos do tipo `CEditView`.|

## <a name="remarks"></a>Comentários

A `CEditView` classe fornece as seguintes funções adicionais:

- Imprimir.

- Localizar e substituir.

Como a `CEditView` classe é uma derivada da `CView`classe, os objetos `CEditView` da classe podem ser usados com documentos e modelos de documentos.

O `CEditView` texto de cada controle é mantido em seu próprio objeto de memória global. Seu aplicativo pode ter qualquer número de `CEditView` objetos.

Crie objetos do tipo `CEditView` se você quiser uma janela de edição com a funcionalidade adicional listada acima ou se desejar uma funcionalidade de editor de texto simples. Um `CEditView` objeto pode ocupar toda a área do cliente de uma janela. Derive suas próprias classes `CEditView` do para adicionar ou modificar a funcionalidade básica ou para declarar classes que podem ser adicionadas a um modelo de documento.

A implementação padrão da classe `CEditView` manipula os seguintes comandos: ID_EDIT_SELECT_ALL, ID_EDIT_FIND, ID_EDIT_REPLACE, ID_EDIT_REPEAT e ID_FILE_PRINT.

O limite de caracteres padrão `CEditView` para é ( \* 1024 1024-1 = 1048575). Isso pode ser alterado chamando a função EM_LIMITTEXT do controle de edição subjacente. No entanto, os limites são diferentes dependendo do sistema operacional e do tipo de controle de edição (única ou multilinha). Para obter mais informações sobre esses limites, consulte [EM_LIMITTEXT](/windows/win32/Controls/em-limittext).

Para alterar esse limite em seu controle, substitua a `OnCreate()` função para sua `CEditView` classe e insira a seguinte linha de código:

[!code-cpp[NVC_MFCDocView#65](../../mfc/codesnippet/cpp/ceditview-class_1.cpp)]

Os objetos do `CEditView` tipo (ou dos tipos derivados `CEditView`de) têm as seguintes limitações:

- `CEditView`não implementa verdadeiro o que você vê é o que você obtém (WYSIWYG) edição. Quando houver uma opção entre a legibilidade na tela e a saída impressa correspondente, `CEditView` o escolherá a legibilidade da tela.

- `CEditView`pode exibir texto somente em uma única fonte. Não há suporte para nenhuma formatação de caractere especial. Consulte classe [CRichEditView](../../mfc/reference/cricheditview-class.md) para obter mais recursos.

- A quantidade de texto `CEditView` que pode conter é limitada. Os limites são os mesmos para o `CEdit` controle.

Para obter mais informações `CEditView`sobre o, consulte [classes de exibição derivadas disponíveis no MFC](../../mfc/derived-view-classes-available-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[Cvisualização](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CEditView`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxext. h

##  <a name="ceditview"></a>CEditView:: CEditView

Constrói um objeto do tipo `CEditView`.

```
CEditView();
```

### <a name="remarks"></a>Comentários

Depois de construir o objeto, você deve chamar a função [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) antes de o controle de edição ser usado. Se você derivar uma classe `CEditView` de e adicioná-la ao modelo `CWinApp::AddDocTemplate`usando, a estrutura chamará esse construtor e `Create` a função.

##  <a name="dwstyledefault"></a>  CEditView::dwStyleDefault

Contém o estilo padrão do `CEditView` objeto.

```
static const DWORD dwStyleDefault;
```

### <a name="remarks"></a>Comentários

Passe este membro estático como o parâmetro *dwStyle* da `Create` função para obter o estilo `CEditView` padrão do objeto.

##  <a name="findtext"></a>  CEditView::FindText

Chame a `FindText` função para pesquisar o `CEditView` buffer de texto do objeto.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bNext = TRUE,
    BOOL bCase = TRUE);
```

### <a name="parameters"></a>Parâmetros

*lpszFind*<br/>
O texto a ser encontrado.

*bNext*<br/>
Especifica a direção da pesquisa. Se for TRUE, a direção da pesquisa será para o final do buffer. Se for FALSE, a direção da pesquisa será para o início do buffer.

*bCase*<br/>
Especifica se a pesquisa diferencia maiúsculas de minúsculas. Se for TRUE, a pesquisa diferenciará maiúsculas de minúsculas. Se for FALSE, a pesquisa não diferenciará maiúsculas de minúsculas.

### <a name="return-value"></a>Valor de retorno

Diferente de zero se o texto de pesquisa for encontrado; caso contrário, 0.

### <a name="remarks"></a>Comentários

Essa função pesquisa o texto no buffer para o texto especificado por *lpszFind*, começando na seleção atual, na direção especificada por *bNext*e com a sensibilidade de maiúsculas e minúsculas especificada por *bCase*. Se o texto for encontrado, ele definirá a seleção como o texto encontrado e retornará um valor diferente de zero. Se o texto não for encontrado, a função retornará 0.

Normalmente, você não precisa chamar a `FindText` função, a menos que substitua `OnFindNext`, que `FindText`chama.

##  <a name="getbufferlength"></a>  CEditView::GetBufferLength

Chame essa função de membro para obter o número de caracteres no buffer do controle de edição, não incluindo o terminador nulo.

```
UINT GetBufferLength() const;
```

### <a name="return-value"></a>Valor de retorno

O comprimento da cadeia de caracteres no buffer.

##  <a name="geteditctrl"></a>  CEditView::GetEditCtrl

Chame `GetEditCtrl` para obter uma referência ao controle de edição usado pelo modo de exibição de edição.

```
CEdit& GetEditCtrl() const;
```

### <a name="return-value"></a>Valor de retorno

Uma referência a um objeto `CEdit`.

### <a name="remarks"></a>Comentários

Esse controle é do tipo [CEdit](../../mfc/reference/cedit-class.md), para que você possa manipular o controle de edição do Windows `CEdit` diretamente usando as funções de membro.

> [!CAUTION]
>  O uso `CEdit` do objeto pode alterar o estado do controle de edição subjacente do Windows. Por exemplo, você não deve alterar as configurações da guia usando a função [CEdit::](../../mfc/reference/cedit-class.md#settabstops) SetTabStops `CEditView` porque o armazena em cache essas configurações para uso no controle de edição e na impressão. Em vez disso, use [CEditView::](#settabstops)SetTabStops.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_MFCDocView#66](../../mfc/codesnippet/cpp/ceditview-class_2.cpp)]

##  <a name="getprinterfont"></a>  CEditView::GetPrinterFont

Chame `GetPrinterFont` para obter um ponteiro para um objeto [CFont](../../mfc/reference/cfont-class.md) que descreve a fonte da impressora atual.

```
CFont* GetPrinterFont() const;
```

### <a name="return-value"></a>Valor de retorno

Um ponteiro para um `CFont` objeto que especifica a fonte da impressora atual; NULL se a fonte da impressora não tiver sido definida. O ponteiro pode ser temporário e não deve ser armazenado para uso posterior.

### <a name="remarks"></a>Comentários

Se a fonte da impressora não tiver sido definida, o comportamento de impressão padrão `CEditView` da classe será imprimir usando a mesma fonte usada para exibição.

Use essa função para determinar a fonte atual da impressora. Se não for a fonte de impressora desejada, use [CEditView:: SetPrinterFont](#setprinterfont) para alterá-la.

##  <a name="getselectedtext"></a>  CEditView::GetSelectedText

Chame `GetSelectedText` para copiar o texto selecionado em um `CString` objeto, até o final da seleção ou o caractere que precede o primeiro caractere de retorno de carro na seleção.

```
void GetSelectedText(CString& strResult) const;
```

### <a name="parameters"></a>Parâmetros

*strResult*<br/>
Uma referência ao `CString` objeto que deve receber o texto selecionado.

##  <a name="lockbuffer"></a>  CEditView::LockBuffer

Chame essa função de membro para obter um ponteiro para o buffer. O buffer não deve ser modificado.

```
LPCTSTR LockBuffer() const;
```

### <a name="return-value"></a>Valor de retorno

Um ponteiro para o buffer do controle de edição.

##  <a name="onfindnext"></a>  CEditView::OnFindNext

Pesquisa o texto no buffer para o texto especificado por *lpszFind*, na direção especificada por *bNext*, com a sensibilidade de maiúsculas e minúsculas especificada por *bCase*.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase);
```

### <a name="parameters"></a>Parâmetros

*lpszFind*<br/>
O texto a ser encontrado.

*bNext*<br/>
Especifica a direção da pesquisa. Se for TRUE, a direção da pesquisa será para o final do buffer. Se for FALSE, a direção da pesquisa será para o início do buffer.

*bCase*<br/>
Especifica se a pesquisa diferencia maiúsculas de minúsculas. Se for TRUE, a pesquisa diferenciará maiúsculas de minúsculas. Se for FALSE, a pesquisa não diferenciará maiúsculas de minúsculas.

### <a name="remarks"></a>Comentários

A pesquisa começa no início da seleção atual e é realizada por meio de uma chamada para [LocalizarTexto](#findtext). Na implementação padrão, `OnFindNext` o chama [OnTextNotFound](#ontextnotfound) se o texto não for encontrado.

Substitua `OnFindNext` para alterar a maneira como `CEditView`um objeto derivado pesquisa texto. `CEditView`chama `OnFindNext` quando o usuário escolhe o botão Localizar próximo na caixa de diálogo localização padrão.

##  <a name="onreplaceall"></a>  CEditView::OnReplaceAll

`CEditView`chama `OnReplaceAll` quando o usuário seleciona o botão Substituir tudo na caixa de diálogo Substituir padrão.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase);
```

### <a name="parameters"></a>Parâmetros

*lpszFind*<br/>
O texto a ser encontrado.

*lpszReplace*<br/>
O texto para substituir o texto de pesquisa.

*bCase*<br/>
Especifica se a pesquisa diferencia maiúsculas de minúsculas. Se for TRUE, a pesquisa diferenciará maiúsculas de minúsculas. Se for FALSE, a pesquisa não diferenciará maiúsculas de minúsculas.

### <a name="remarks"></a>Comentários

`OnReplaceAll`pesquisa o texto no buffer para o texto especificado por *lpszFind*, com a distinção de maiúsculas e minúsculas especificada por *bCase*. A pesquisa começa no início da seleção atual. Cada vez que o texto de pesquisa é encontrado, essa função substitui essa ocorrência do texto pelo texto especificado por *lpszReplace*. A pesquisa é realizada por meio de uma chamada para [LocalizarTexto](#findtext). Na implementação padrão, [OnTextNotFound](#ontextnotfound) será chamado se o texto não for encontrado.

Se a seleção atual não corresponder a *lpszFind*, a seleção será atualizada para a primeira ocorrência do texto especificado por *lpszFind* e uma substituição não será executada. Isso permite que o usuário confirme se isso é o que eles querem fazer quando a seleção não corresponde ao texto a ser substituído.

Substitua `OnReplaceAll` para alterar a maneira como `CEditView`um objeto derivado substitui o texto.

##  <a name="onreplacesel"></a>  CEditView::OnReplaceSel

`CEditView`chama `OnReplaceSel` quando o usuário seleciona o botão substituir na caixa de diálogo Substituir padrão.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parâmetros

*lpszFind*<br/>
O texto a ser encontrado.

*bNext*<br/>
Especifica a direção da pesquisa. Se for TRUE, a direção da pesquisa será para o final do buffer. Se for FALSE, a direção da pesquisa será para o início do buffer.

*bCase*<br/>
Especifica se a pesquisa diferencia maiúsculas de minúsculas. Se for TRUE, a pesquisa diferenciará maiúsculas de minúsculas. Se for FALSE, a pesquisa não diferenciará maiúsculas de minúsculas.

*lpszReplace*<br/>
O texto para substituir o texto encontrado.

### <a name="remarks"></a>Comentários

Depois de substituir a seleção, essa função pesquisa o texto no buffer para a próxima ocorrência do texto especificado por *lpszFind*, na direção especificada por *bNext*, com a distinção de maiúsculas e minúsculas especificada por *bCase*. A pesquisa é realizada por meio de uma chamada para [LocalizarTexto](#findtext). Se o texto não for encontrado, [OnTextNotFound](#ontextnotfound) será chamado.

Substitua `OnReplaceSel` para alterar a maneira como `CEditView`um objeto derivado substitui o texto selecionado.

##  <a name="ontextnotfound"></a>  CEditView::OnTextNotFound

Substitua essa função para alterar a implementação padrão, que chama a função `MessageBeep`do Windows.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parâmetros

*lpszFind*<br/>
O texto a ser encontrado.

##  <a name="printinsiderect"></a>  CEditView::PrintInsideRect

Chamada `PrintInsideRect` para imprimir texto no retângulo especificado por *rectLayout*.

```
UINT PrintInsideRect(
    CDC *pDC,
    RECT& rectLayout,
    UINT nIndexStart,
    UINT nIndexStop);
```

### <a name="parameters"></a>Parâmetros

*pDC*<br/>
Ponteiro para o contexto do dispositivo de impressora.

*rectLayout*<br/>
Referência a um objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) ou [estrutura RECT](/windows/win32/api/windef/ns-windef-rect) especificando o retângulo no qual o texto deve ser renderizado.

*nIndexStart*<br/>
Índice dentro do buffer do primeiro caractere a ser renderizado.

*nIndexStop*<br/>
Índice dentro do buffer do caractere que segue o último caractere a ser renderizado.

### <a name="return-value"></a>Valor de retorno

O índice do próximo caractere a ser impresso (ou seja, o caractere após o último caractere processado).

### <a name="remarks"></a>Comentários

Se o `CEditView` controle não tiver o estilo ES_AUTOHSCROLL, o texto será encapsulado dentro do retângulo de renderização. Se o controle tiver o estilo ES_AUTOHSCROLL, o texto será recortado na borda direita do retângulo.

O `rect.bottom` elemento do objeto *rectLayout* é alterado para que as dimensões do retângulo definam a parte do retângulo original ocupado pelo texto.

##  <a name="serializeraw"></a>  CEditView::SerializeRaw

A `SerializeRaw` chamada para fazer `CArchive` com que um objeto leia ou `CEditView` grave o texto no objeto em um arquivo de texto.

```
void SerializeRaw(CArchive& ar);
```

### <a name="parameters"></a>Parâmetros

*ar*<br/>
Referência ao `CArchive` objeto que armazena o texto serializado.

### <a name="remarks"></a>Comentários

`SerializeRaw`difere da `CEditView`implementação interna de `Serialize` em que lê e grava apenas o texto, sem dados de descrição de objeto precedentes.

##  <a name="setprinterfont"></a>  CEditView::SetPrinterFont

Chame `SetPrinterFont` para definir a fonte da impressora para a fonte especificada por *pFont*.

```
void SetPrinterFont(CFont* pFont);
```

### <a name="parameters"></a>Parâmetros

*pFont*<br/>
Um ponteiro para um objeto do tipo `CFont`. Se for NULL, a fonte usada para impressão será baseada na fonte de vídeo.

### <a name="remarks"></a>Comentários

Se você quiser que a exibição sempre use uma fonte específica para impressão, inclua uma chamada para `SetPrinterFont` na função da `OnPreparePrinting` sua classe. Essa função virtual é chamada antes que a impressão ocorra, portanto, a alteração da fonte ocorre antes que o conteúdo da exibição seja impresso.

##  <a name="settabstops"></a>  CEditView::SetTabStops

Chame essa função para definir as paradas de tabulação usadas para exibição e impressão.

```
void SetTabStops(int nTabStops);
```

### <a name="parameters"></a>Parâmetros

*nTabStops*<br/>
Largura de cada parada de tabulação, em unidades de caixa de diálogo.

### <a name="remarks"></a>Comentários

Há suporte apenas para uma única largura de parada de tabulação. ( `CEdit` objetos dão suporte a várias larguras de guia.) As larguras estão em unidades de caixa de diálogo, que são iguais a um quarto da largura média de caracteres (com base em caracteres alfabéticos maiúsculos e minúsculos) da fonte usada no momento da impressão ou exibição. Você não deve usar `CEdit::SetTabStops` o `CEditView` porque o deve armazenar em cache o valor de parada de tabulação.

Essa função modifica apenas as guias do objeto para o qual ele é chamado. Para alterar as paradas de tabulação de cada `CEditView` objeto em seu aplicativo, chame a função de `SetTabStops` cada objeto.

### <a name="example"></a>Exemplo

Esse fragmento de código define as paradas de tabulação no controle para cada quarto caractere medindo cuidadosamente a fonte usada pelo controle.

[!code-cpp[NVC_MFCDocView#67](../../mfc/codesnippet/cpp/ceditview-class_3.cpp)]

##  <a name="unlockbuffer"></a>CEditView:: UnlockBuffer

Chame essa função de membro para desbloquear o buffer.

```
void UnlockBuffer() const;
```

### <a name="remarks"></a>Comentários

Chame `UnlockBuffer` depois de terminar de usar o ponteiro retornado por [LockBuffer](#lockbuffer).

## <a name="see-also"></a>Consulte também

[Exemplo de SUPERPAD do MFC](../../overview/visual-cpp-samples.md)<br/>
[Classe CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classe CEdit](../../mfc/reference/cedit-class.md)<br/>
[Classe CDocument](../../mfc/reference/cdocument-class.md)<br/>
[Classe CDocTemplate](../../mfc/reference/cdoctemplate-class.md)<br/>
[Classe CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Classe CRichEditView](../../mfc/reference/cricheditview-class.md)
