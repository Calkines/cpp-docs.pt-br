---
title: Classe CComCriticalSection
ms.date: 11/04/2016
f1_keywords:
- CComCriticalSection
- ATLCORE/ATL::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::CComCriticalSection
- ATLCORE/ATL::CComCriticalSection::Init
- ATLCORE/ATL::CComCriticalSection::Lock
- ATLCORE/ATL::CComCriticalSection::Term
- ATLCORE/ATL::CComCriticalSection::Unlock
- ATLCORE/ATL::CComCriticalSection::m_sec
helpviewer_keywords:
- CComCriticalSection class
ms.assetid: 44e1edd2-90be-4bfe-9739-58e8b419e7d1
ms.openlocfilehash: f3a4b50f8dd9bc460a209c47497e720529c40e58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246638"
---
# <a name="ccomcriticalsection-class"></a>Classe CComCriticalSection

Essa classe fornece métodos para obter e liberar a propriedade de um objeto de seção crítica.

## <a name="syntax"></a>Sintaxe

```
class CComCriticalSection
```

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[CComCriticalSection::CComCriticalSection](#ccomcriticalsection)|O construtor.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CComCriticalSection::Init](#init)|Cria e inicializa um objeto de seção crítica.|
|[CComCriticalSection::Lock](#lock)|Obtém a propriedade do objeto de seção crítica.|
|[CComCriticalSection::Term](#term)|Libera os recursos do sistema usados pelo objeto de seção crítica.|
|[CComCriticalSection::Unlock](#unlock)|Libera a propriedade do objeto de seção crítica.|

### <a name="public-data-members"></a>Membros de Dados Públicos

|Nome|Descrição|
|----------|-----------------|
|[CComCriticalSection::m_sec](#m_sec)|Um objeto CRITICAL_SECTION.|

## <a name="remarks"></a>Comentários

`CComCriticalSection` é semelhante à classe [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md), exceto que você deve inicializar explicitamente e liberará a seção crítica.

Normalmente, você usa `CComCriticalSection` por meio de **typedef** nome [CriticalSection](ccommultithreadmodel-class.md#criticalsection). Esse nome faz referência a `CComCriticalSection` quando [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) está sendo usado.

Ver [classe CComCritSecLock](../../atl/reference/ccomcritseclock-class.md) de uma maneira mais segura usar essa classe que chamar `Lock` e `Unlock` diretamente.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atlcore.h

##  <a name="ccomcriticalsection"></a>  CComCriticalSection::CComCriticalSection

O construtor.

```
CComCriticalSection() throw();
```

### <a name="remarks"></a>Comentários

Define o [m_sec](#m_sec) membro de dados como NULL.

##  <a name="init"></a>  CComCriticalSection::Init

Chama a função Win32 [InitializeCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsection), que inicializa o objeto de seção crítica contido na [m_sec](#m_sec) membro de dados.

```
HRESULT Init() throw();
```

### <a name="return-value"></a>Valor de retorno

Retornará S_OK no êxito, E_OUTOFMEMORY ou E_FAIL em caso de falha.

##  <a name="lock"></a>  CComCriticalSection::Lock

Chama a função Win32 [EnterCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-entercriticalsection), que aguarda até que o thread pode assumir a propriedade do objeto de seção crítica contido na [m_sec](#m_sec) membro de dados.

```
HRESULT Lock() throw();
```

### <a name="return-value"></a>Valor de retorno

Retornará S_OK no êxito, E_OUTOFMEMORY ou E_FAIL em caso de falha.

### <a name="remarks"></a>Comentários

O objeto de seção crítica deve ser inicializado pela primeira vez com uma chamada para o [Init](#init) método. Quando o código protegido finalizou a execução, o thread deve chamar [Unlock](#unlock) para liberar a propriedade da seção crítica.

##  <a name="m_sec"></a>  CComCriticalSection::m_sec

Contém um objeto de seção crítica que é usado por todos os `CComCriticalSection` métodos.

```
CRITICAL_SECTION m_sec;
```

##  <a name="term"></a>  CComCriticalSection::Term

Chama a função Win32 [DeleteCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-deletecriticalsection), que libera todos os recursos usados pelo objeto de seção crítica contido na [m_sec](#m_sec) membro de dados.

```
HRESULT Term() throw();
```

### <a name="return-value"></a>Valor de retorno

Retorna S_OK.

### <a name="remarks"></a>Comentários

Uma vez `Term` tiver sido chamado, a crítica seção não pode mais ser usada para sincronização.

##  <a name="unlock"></a>  CComCriticalSection::Unlock

Chama a função Win32 [LeaveCriticalSection](/windows/desktop/api/synchapi/nf-synchapi-leavecriticalsection), que libera a propriedade do objeto de seção crítica contido na [m_sec](#m_sec) membro de dados.

```
HRESULT Unlock() throw();
```

### <a name="return-value"></a>Valor de retorno

Retorna S_OK.

### <a name="remarks"></a>Comentários

Para obter a propriedade pela primeira vez, o thread deve chamar o [bloqueio](#lock) método. Cada chamada para `Lock` requer uma chamada correspondente para `Unlock` para liberar a propriedade da seção crítica.

## <a name="see-also"></a>Consulte também

[Classe CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)<br/>
[Visão geral da classe](../../atl/atl-class-overview.md)<br/>
[Classe CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)
