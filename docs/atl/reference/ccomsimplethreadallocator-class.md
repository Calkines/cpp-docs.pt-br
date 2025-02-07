---
title: Classe CComSimpleThreadAllocator
ms.date: 11/04/2016
f1_keywords:
- CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator
- ATLBASE/ATL::CComSimpleThreadAllocator::GetThread
helpviewer_keywords:
- threading [ATL], selecting threads
- ATL threads
- CComSimpleThreadAllocator class
- ATL threads, allocating
ms.assetid: 66b2166a-8c50-49fd-b8e4-7f293470327d
ms.openlocfilehash: ef1f86ca832674ba5710083b08b67f0a775a7a33
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246147"
---
# <a name="ccomsimplethreadallocator-class"></a>Classe CComSimpleThreadAllocator

Essa classe gerencia a seleção de thread para a classe `CComAutoThreadModule`.

## <a name="syntax"></a>Sintaxe

```
class CComSimpleThreadAllocator
```

## <a name="members"></a>Membros

### <a name="public-methods"></a>Métodos Públicos

|Nome|Descrição|
|----------|-----------------|
|[CComSimpleThreadAllocator::GetThread](#getthread)|Seleciona um thread.|

## <a name="remarks"></a>Comentários

`CComSimpleThreadAllocator` gerencia a seleção de thread para [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md). `CComSimpleThreadAllocator::GetThread` simplesmente percorre cada thread e retorna o outro na sequência.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atlbase. h

##  <a name="getthread"></a>  CComSimpleThreadAllocator::GetThread

Seleciona um thread, especificando o próximo segmento na sequência.

```
int GetThread(CComApartment* /* pApt */, int nThreads);
```

### <a name="parameters"></a>Parâmetros

*pApt*<br/>
Não é usado na implementação do padrão da ATL.

*nThreads*<br/>
O número máximo de threads no módulo do EXE.

### <a name="return-value"></a>Valor de retorno

Um inteiro entre zero e (*nThreads* - 1). Identifica um dos threads no módulo do EXE.

### <a name="remarks"></a>Comentários

Você pode substituir `GetThread` para fornecer um método diferente da seleção ou fazer uso do *pApt* parâmetro.

`GetThread` é chamado pelo [CComAutoThreadModule::CreateInstance](../../atl/reference/ccomautothreadmodule-class.md#createinstance).

## <a name="see-also"></a>Consulte também

[Classe CComApartment](../../atl/reference/ccomapartment-class.md)<br/>
[Visão geral da classe](../../atl/atl-class-overview.md)
