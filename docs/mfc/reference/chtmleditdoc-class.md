---
title: Classe CHtmlEditDoc
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditDoc
- AFXHTML/CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::GetView
- AFXHTML/CHtmlEditDoc::IsModified
- AFXHTML/CHtmlEditDoc::OpenURL
helpviewer_keywords:
- CHtmlEditDoc [MFC], CHtmlEditDoc
- CHtmlEditDoc [MFC], GetView
- CHtmlEditDoc [MFC], IsModified
- CHtmlEditDoc [MFC], OpenURL
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
ms.openlocfilehash: c2a00b2501647f6101fed8ed1d4cd23dad7ab209
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346181"
---
# <a name="chtmleditdoc-class"></a>Classe CHtmlEditDoc

Com o [CHtmlEditView](../../mfc/reference/chtmleditview-class.md), fornece a funcionalidade da plataforma de edição WebBrowser no contexto da arquitetura de exibição de documento do MFC.

## <a name="syntax"></a>Sintaxe

```
class AFX_NOVTABLE CHtmlEditDoc : public CDocument
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[CHtmlEditDoc::CHtmlEditDoc](#chtmleditdoc)|Constrói um objeto `CHtmlEditDoc`.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CHtmlEditDoc::GetView](#getview)|Recupera o `CHtmlEditView` objeto anexado a este documento.|
|[CHtmlEditDoc::IsModified](#ismodified)|Retorna se o controle WebBrowser de associados do modo de exibição contém um documento que foi modificado pelo usuário.|
|[CHtmlEditDoc::OpenURL](#openurl)|Abre uma URL.|

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`CHtmlEditDoc`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxhtml.h

##  <a name="chtmleditdoc"></a>  CHtmlEditDoc::CHtmlEditDoc

Constrói um objeto `CHtmlEditDoc`.

```
CHtmlEditDoc();
```

##  <a name="getview"></a>  CHtmlEditDoc::GetView

Recupera o [CHtmlEditView](../../mfc/reference/chtmleditview-class.md) objeto anexado a este documento.

```
virtual CHtmlEditView* GetView() const;
```

### <a name="return-value"></a>Valor de retorno

Retorna um ponteiro para o documento `CHtmlEditView` objeto.

##  <a name="ismodified"></a>  CHtmlEditDoc::IsModified

Retorna se o controle WebBrowser de associados do modo de exibição contém um documento que foi modificado pelo usuário.

```
virtual BOOL IsModified();
```

##  <a name="openurl"></a>  CHtmlEditDoc::OpenURL

Abre uma URL.

```
virtual BOOL OpenURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Parâmetros

*lpszURL*<br/>
A URL para abrir.

### <a name="return-value"></a>Valor de retorno

Retorna verdadeiro em caso de êxito, FALSE em caso de falha.

## <a name="see-also"></a>Consulte também

[Exemplo de HTMLEdit](../../overview/visual-cpp-samples.md)<br/>
[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)
