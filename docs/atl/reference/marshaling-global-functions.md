---
title: Funções globais de marshaling
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
ms.openlocfilehash: cac6e316ad6b5d3f49c171c940d9129060744aee
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271900"
---
# <a name="marshaling-global-functions"></a>Funções globais de marshaling

Essas funções fornecem suporte para empacotamento e a conversão de dados de marshaling em ponteiros de interface.

> [!IMPORTANT]
>  As funções listadas na tabela a seguir não podem ser usadas em aplicativos executados no tempo de execução do Windows.

|||
|-|-|
|[AtlFreeMarshalStream](#atlfreemarshalstream)|Libera os dados de marshaling e o `IStream` ponteiro.|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|Cria um novo objeto de fluxo e realiza marshaling do ponteiro de interface especificado.|
|[AtlUnmarshalPtr](#atlunmarshalptr)|Converte o marshaling de dados do fluxo em um ponteiro de interface.|

## <a name="requirements"></a>Requisitos:

**Cabeçalho:** atlbase. h

##  <a name="atlfreemarshalstream"></a>  AtlFreeMarshalStream

Libera os dados de marshaling no fluxo e depois libera o ponteiro de fluxo.

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>Parâmetros

*pStream*<br/>
[in] Um ponteiro para o `IStream` interface em que o fluxo usado para realizar marshaling.

### <a name="example"></a>Exemplo

Veja o exemplo de [AtlMarshalPtrInProc](#atlmarshalptrinproc).

##  <a name="atlmarshalptrinproc"></a>  AtlMarshalPtrInProc

Cria um novo objeto de fluxo, grava o CLSID do proxy no fluxo e realiza o marshaling do ponteiro de interface especificado gravando os dados necessários para inicializar o proxy no fluxo.

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>Parâmetros

*pUnk*<br/>
[in] Um ponteiro para a interface para ser empacotado.

*iid*<br/>
[in] O GUID da interface que está sendo empacotado.

*ppStream*<br/>
[out] Um ponteiro para o `IStream` interface no novo objeto de fluxo usado para realizar marshaling.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

O sinalizador MSHLFLAGS_TABLESTRONG é definido para que o ponteiro pode ser empacotado para vários fluxos. O ponteiro pode também ser desempacotado várias vezes.

Se realizar marshaling falhar, o ponteiro de fluxo é liberado.

`AtlMarshalPtrInProc` só pode ser usado em um ponteiro para um objeto em processo.

### <a name="example"></a>Exemplo

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

##  <a name="atlunmarshalptr"></a>  AtlUnmarshalPtr

Converte os dados de marshaling do fluxo em um ponteiro de interface que pode ser usado pelo cliente.

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>Parâmetros

*pStream*<br/>
[in] Um ponteiro para o fluxo que está sendo desempacotado.

*iid*<br/>
[in] O GUID da interface que está sendo desempacotada.

*ppUnk*<br/>
[out] Um ponteiro para a interface desempacotada.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="example"></a>Exemplo

Veja o exemplo de [AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="see-also"></a>Consulte também

[Funções](../../atl/reference/atl-functions.md)
