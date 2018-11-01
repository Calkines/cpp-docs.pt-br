---
title: Classe CMFCRibbonButtonsGroup
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::AddButtons
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetButton
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetCount
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetImageSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::GetRegularSize
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::HasImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::OnDrawImage
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::RemoveAll
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetImages
- AFXRIBBONBUTTONSGROUP/CMFCRibbonButtonsGroup::SetParentCategory
helpviewer_keywords:
- CMFCRibbonButtonsGroup [MFC], CMFCRibbonButtonsGroup
- CMFCRibbonButtonsGroup [MFC], AddButton
- CMFCRibbonButtonsGroup [MFC], AddButtons
- CMFCRibbonButtonsGroup [MFC], GetButton
- CMFCRibbonButtonsGroup [MFC], GetCount
- CMFCRibbonButtonsGroup [MFC], GetImageSize
- CMFCRibbonButtonsGroup [MFC], GetRegularSize
- CMFCRibbonButtonsGroup [MFC], HasImages
- CMFCRibbonButtonsGroup [MFC], OnDrawImage
- CMFCRibbonButtonsGroup [MFC], RemoveAll
- CMFCRibbonButtonsGroup [MFC], SetImages
- CMFCRibbonButtonsGroup [MFC], SetParentCategory
ms.assetid: b993d93e-fc1a-472f-a87f-1d7b7b499845
ms.openlocfilehash: 0babda16ee29671a584599699b459062c22406e6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592732"
---
# <a name="cmfcribbonbuttonsgroup-class"></a>Classe CMFCRibbonButtonsGroup

O `CMFCRibbonButtonsGroup` classe permite que você organize um conjunto de botões de faixa de opções em um grupo. Todos os botões no grupo são diretamente adjacentes uns aos outros horizontalmente e colocado em uma borda.

## <a name="syntax"></a>Sintaxe

```
class CMFCRibbonButtonsGroup : public CMFCRibbonBaseElement
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores Públicos

|Nome|Descrição|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup](#cmfcribbonbuttonsgroup)|Constrói um objeto `CMFCRibbonButtonsGroup`.|

### <a name="public-methods"></a>Métodos Públicos

|Nome|Descrição|
|----------|-----------------|
|[CMFCRibbonButtonsGroup::AddButton](#addbutton)|Adiciona um botão a um grupo.|
|[CMFCRibbonButtonsGroup::AddButtons](#addbuttons)|Adiciona uma lista de botões a um grupo.|
|[CMFCRibbonButtonsGroup::GetButton](#getbutton)|Retorna um ponteiro para o botão que está localizado em um índice especificado.|
|[CMFCRibbonButtonsGroup::GetCount](#getcount)|Retorna o número de botões no grupo.|
|[CMFCRibbonButtonsGroup::GetImageSize](#getimagesize)|Retorna o tamanho da imagem das imagens normais no grupo da faixa de opções (substitui [CMFCRibbonBaseElement::GetImageSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getimagesize).)|
|[CMFCRibbonButtonsGroup::GetRegularSize](#getregularsize)|Retorna o tamanho regular do elemento da faixa de opções (substitui [CMFCRibbonBaseElement::GetRegularSize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize).)|
|[CMFCRibbonButtonsGroup::HasImages](#hasimages)|Relatórios se o `CMFCRibbonButtonsGroup` objeto contém imagens da barra de ferramentas.|
|[CMFCRibbonButtonsGroup::OnDrawImage](#ondrawimage)|Desenha a imagem apropriada para um botão especificado, dependendo se o botão é normal, realçado ou desabilitado.|
|[CMFCRibbonButtonsGroup::RemoveAll](#removeall)|Remove todos os botões do `CMFCRibbonButtonsGroup` objeto.|
|[CMFCRibbonButtonsGroup::SetImages](#setimages)|Atribui imagens ao grupo.|
|[CMFCRibbonButtonsGroup::SetParentCategory](#setparentcategory)|Define o pai `CMFCRibbonCategory` do `CMFCRibbonButtonsGroup` objeto e todos os botões dentro dele (substitui [CMFCRibbonBaseElement::SetParentCategory](../../mfc/reference/cmfcribbonbaseelement-class.md#setparentcategory).)|

## <a name="remarks"></a>Comentários

O grupo é derivado de [CMFCBaseRibbonElement](../../mfc/reference/cmfcribbonbaseelement-class.md) e pode ser manipulado como uma única entidade. Você pode posicionar o grupo em nenhum menu do painel ou pop-up.

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra como usar vários métodos no `CMFCRibbonButtonsGroup` classe. O exemplo mostra como construir um `CMFCRibbonButtonsGroup` do objeto, atribuir imagens para o grupo de botões de faixa de opções e adicionar um botão para o grupo de botões de faixa de opções. Este trecho de código é parte do [desenhar o cliente de exemplo](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#2](../../mfc/reference/codesnippet/cpp/cmfcribbonbuttonsgroup-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButtonsGroup](../../mfc/reference/cmfcribbonbuttonsgroup-class.md)

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxribbonbuttonsgroup.h

##  <a name="addbutton"></a>  CMFCRibbonButtonsGroup::AddButton

Adiciona um botão a um grupo.

```
void AddButton(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Parâmetros

*pButton*<br/>
[in] Um ponteiro para um botão para adicionar.

##  <a name="addbuttons"></a>  CMFCRibbonButtonsGroup::AddButtons

Adiciona uma lista de botões a um grupo.

```
void AddButtons(
    const CList<CMFCRibbonBaseElement*,CMFCRibbonBaseElement*>& lstButtons);
```

### <a name="parameters"></a>Parâmetros

*lstButtons*<br/>
[in] Uma lista de ponteiros para os botões que você deseja adicionar.

##  <a name="cmfcribbonbuttonsgroup"></a>  CMFCRibbonButtonsGroup::CMFCRibbonButtonsGroup

Constrói um objeto `CMFCRibbonButtonsGroup`.

```
CMFCRibbonButtonsGroup();
CMFCRibbonButtonsGroup(CMFCRibbonBaseElement* pButton);
```

### <a name="parameters"></a>Parâmetros

*pButton*<br/>
[in] Especifica um botão para adicionar ao recém-criado `CMFCRibbonButtonsGroup` objeto.

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="getbutton"></a>  CMFCRibbonButtonsGroup::GetButton

Retorna um ponteiro para o botão que está localizado em um índice especificado.

```
CMFCRibbonBaseElement* GetButton(int i) const;
```

### <a name="parameters"></a>Parâmetros

*i*<br/>
[in] Um índice baseado em zero de um botão para retornar.

### <a name="return-value"></a>Valor de retorno

Um ponteiro para o botão que está localizado no índice especificado. NULL se o índice especificado está fora do intervalo.

### <a name="remarks"></a>Comentários

##  <a name="getcount"></a>  CMFCRibbonButtonsGroup::GetCount

Retorna o número de botões no grupo.

```
int GetCount() const;
```

### <a name="return-value"></a>Valor de retorno

O número de botões no grupo.

##  <a name="getimagesize"></a>  CMFCRibbonButtonsGroup::GetImageSize

Recupera o tamanho da imagem de origem do protegido `CMFCToolBarImages` membro `m_Images`.

```
const CSize GetImageSize() const;
```

### <a name="return-value"></a>Valor de retorno

Retorna o tamanho da imagem de origem das imagens da barra de ferramentas, se qualquer um estiver presente, ou um `CSize` de zero se não.

### <a name="remarks"></a>Comentários

##  <a name="getregularsize"></a>  CMFCRibbonButtonsGroup::GetRegularSize

Recupera o tamanho máximo possível do elemento de grupo da faixa de opções.

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parâmetros

*pDC*<br/>
[in] Ponteiro para o contexto de dispositivo do grupo da faixa de opções.

### <a name="return-value"></a>Valor de retorno

### <a name="remarks"></a>Comentários

##  <a name="hasimages"></a>  CMFCRibbonButtonsGroup::HasImages

Relatórios se o `CMFCRibbonButtonsGroup` objeto contém imagens da barra de ferramentas.

```
BOOL HasImages() const;
```

### <a name="return-value"></a>Valor de retorno

Retorna VERDADEIRO se protegido `CMFCToolBarImages` membro `m_Images` contiver imagens, ou falso se não.

### <a name="remarks"></a>Comentários

##  <a name="ondrawimage"></a>  CMFCRibbonButtonsGroup::OnDrawImage

Desenha a imagem apropriada para um botão especificado, dependendo se o botão é normal, realçado ou desabilitado.

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rectImage,
    CMFCRibbonBaseElement* pButton,
    int nImageIndex);
```

### <a name="parameters"></a>Parâmetros

*pDC*<br/>
[in] Ponteiro para o contexto de dispositivo do `CMFCRibbonButtonsGroup` objeto.

*rectImage*<br/>
[in] O retângulo no qual desenhar a imagem.

*pButton*<br/>
[in] O botão para o qual desenhar a imagem.

*nImageIndex*<br/>
[in] O índice da imagem a ser desenhado no botão (em uma das matrizes três imagem botões normal, realçado ou desabilitado).

### <a name="remarks"></a>Comentários

##  <a name="removeall"></a>  CMFCRibbonButtonsGroup::RemoveAll

Remove todos os botões do `CMFCRibbonButtonsGroup` objeto.

```
void RemoveAll();
```

### <a name="remarks"></a>Comentários

##  <a name="setimages"></a>  CMFCRibbonButtonsGroup::SetImages

Atribui imagens para o grupo de botões de faixa de opções.

```
void SetImages(
    CMFCToolBarImages* pImages,
    CMFCToolBarImages* pHotImages,
    CMFCToolBarImages* pDisabledImages);
```

### <a name="parameters"></a>Parâmetros

*pImages*<br/>
[in] Imagens normais.

*pHotImages*<br/>
[in] Imagens quentes.

*pDisabledImages*<br/>
[in] Imagens desabilitadas.

### <a name="remarks"></a>Comentários

Chamar `SetImages` antes de adicionar botões a um grupo. O número de imagens deve ser maior ou igual ao número de botões a serem adicionados ao grupo.

> [!NOTE]
>  Imagens quentes são imagens que são exibidas quando o usuário passa o mouse sobre o botão. Imagens desabilitadas são imagens que são exibidas quando o botão está desabilitado.

##  <a name="setparentcategory"></a>  CMFCRibbonButtonsGroup::SetParentCategory

Define o pai `CMFCRibbonCategory` do `CMFCRibbonButtonsGroup` objeto e todos os botões dentro dele.

```
virtual void SetParentCategory(CMFCRibbonCategory* pCategory);
```

### <a name="parameters"></a>Parâmetros

*pCategory*<br/>
[in] Ponteiro para a categoria pai para definir (os grupos com guias em controles de faixa de opções são chamados de categorias).

### <a name="remarks"></a>Comentários

## <a name="see-also"></a>Consulte também

[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classes](../../mfc/reference/mfc-classes.md)
