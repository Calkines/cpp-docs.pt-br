---
title: Classe CCachedDataPathProperty
ms.date: 11/04/2016
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
ms.openlocfilehash: e7394250c93bcc718d50f2ea9b3522256df7c820
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206776"
---
# <a name="ccacheddatapathproperty-class"></a>Classe CCachedDataPathProperty

Implementa uma controle OLE transferida de forma assíncrona e armazenada em cache em um arquivo de memória de propriedade.

## <a name="syntax"></a>Sintaxe

```
class CCachedDataPathProperty : public CDataPathProperty
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|Constrói um objeto `CCachedDataPathProperty`.|

### <a name="public-data-members"></a>Membros de Dados Públicos

|Nome|Descrição|
|----------|-----------------|
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile` objeto no qual os dados em cache.|

## <a name="remarks"></a>Comentários

Um arquivo de memória é armazenado na RAM, em vez de no disco e é útil para transferências temporárias rápido.

Junto com `CAysncMonikerFile` e `CDataPathProperty`, `CCachedDataPathProperty` fornece a funcionalidade para o uso de monikers assíncronos em controles OLE. Com o `CCachedDataPathProperty` objetos, será possível transferir dados de uma fonte de arquivo ou URL de forma assíncrona e armazená-lo em um arquivo de memória por meio de `m_Cache` variável pública. Todos os dados são armazenados no arquivo de memória e não é necessário substituir [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) , a menos que você deseja observar as notificações e responder. Por exemplo, se você estiver transferindo um grande. Substituir arquivo GIF e desejar notificar seu controle que mais dados são recebidos e ele deve ser redesenhado, `OnDataAvailable` para tornar a notificação.

A classe `CCachedDataPathProperty` é derivado de `CDataPathProperty`.

Para obter mais informações sobre como usar controles ActiveX e monikers assíncronos em aplicativos da Internet, consulte os tópicos a seguir:

- [Primeiras etapas de Internet: Controles ActiveX](../../mfc/activex-controls-on-the-internet.md)

- [Primeiras etapas de Internet: Monikers assíncronos](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Hierarquia de herança

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)

`CCachedDataPathProperty`

## <a name="requirements"></a>Requisitos

**Cabeçalho:** afxctl. h

##  <a name="ccacheddatapathproperty"></a>  CCachedDataPathProperty::CCachedDataPathProperty

Constrói um objeto `CCachedDataPathProperty`.

```
CCachedDataPathProperty(COleControl* pControl = NULL);

CCachedDataPathProperty(
    LPCTSTR lpszPath,
    COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parâmetros

*pControl*<br/>
Um ponteiro para o objeto de controle ActiveX a ser associado a este `CCachedDataPathProperty` objeto.

*lpszPath*<br/>
O caminho, que pode ser absoluto ou relativo, usado para criar um moniker assíncrono que referencia o local absoluto real da propriedade. `CCachedDataPathProperty` usa URLs, não os nomes de arquivo. Se você quiser um `CCachedDataPathProperty` de objeto para um arquivo, preceda file:// ao caminho.

### <a name="remarks"></a>Comentários

O `COleControl` objeto apontado por *pControl* é usado pelo [abra](../../mfc/reference/cdatapathproperty-class.md#open) e recuperados pelas classes derivadas. Se *pControl* for NULL, o controle usado com `Open` deve ser definido com [SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol). Se *lpszPath* for NULL, você pode passar o caminho por meio `Open` ou defini-lo com [SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath).

##  <a name="m_cache"></a>  CCachedDataPathProperty::m_Cache

Contém o nome de classe do arquivo de memória no qual dados são armazenados em cache.

```
CMemFile m_Cache;
```

### <a name="remarks"></a>Comentários

Um arquivo de memória é armazenado na RAM, em vez de no disco.

## <a name="see-also"></a>Consulte também

[Classe CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)<br/>
[Gráfico da hierarquia](../../mfc/hierarchy-chart.md)<br/>
[Classe CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)
