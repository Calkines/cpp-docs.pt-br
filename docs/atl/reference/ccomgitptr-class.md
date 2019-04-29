---
title: Classe CComGITPtr
ms.date: 11/04/2016
f1_keywords:
- CComGITPtr
- ATLBASE/ATL::CComGITPtr
- ATLBASE/ATL::CComGITPtr::CComGITPtr
- ATLBASE/ATL::CComGITPtr::Attach
- ATLBASE/ATL::CComGITPtr::CopyTo
- ATLBASE/ATL::CComGITPtr::Detach
- ATLBASE/ATL::CComGITPtr::GetCookie
- ATLBASE/ATL::CComGITPtr::Revoke
- ATLBASE/ATL::CComGITPtr::m_dwCookie
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
ms.openlocfilehash: bf509d027833610e4251c009d4e444dad3fdd5ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62246467"
---
# <a name="ccomgitptr-class"></a>Classe CComGITPtr

Essa classe fornece métodos para lidar com ponteiros de interface e a tabela de interface global (GIT).

## <a name="syntax"></a>Sintaxe

```
template <class T>
class CComGITPtr
```

#### <a name="parameters"></a>Parâmetros

*T*<br/>
O tipo do ponteiro da interface a ser armazenado no GIT.

## <a name="members"></a>Membros

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[CComGITPtr::CComGITPtr](#ccomgitptr)|O construtor.|
|[CComGITPtr::~CComGITPtr](#dtor)|O destruidor.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CComGITPtr::Attach](#attach)|Chame esse método para registrar o ponteiro de interface na tabela de interface global (GIT).|
|[CComGITPtr::CopyTo](#copyto)|Chame esse método para copiar a interface da tabela de interface global (GIT) para o ponteiro passado.|
|[CComGITPtr::Detach](#detach)|Chame esse método para desassociar a interface do `CComGITPtr` objeto.|
|[CComGITPtr::GetCookie](#getcookie)|Chame esse método para retornar o cookie do `CComGITPtr` objeto.|
|[CComGITPtr::Revoke](#revoke)|Chame esse método para remover o adaptador de tabela de interface global (GIT).|

### <a name="public-operators"></a>Operadores públicos

|Nome|Descrição|
|----------|-----------------|
|[CComGITPtr::operator DWORD](#operator_dword)|Retorna o cookie do `CComGITPtr` objeto.|
|[CComGITPtr::operator =](#operator_eq)|Operador de atribuição.|

### <a name="public-data-members"></a>Membros de Dados Públicos

|Nome|Descrição|
|----------|-----------------|
|[CComGITPtr::m_dwCookie](#m_dwcookie)|O cookie.|

## <a name="remarks"></a>Comentários

Objetos que o marshaler livre de agregação e precisam usar ponteiros de interface obtidos de outros objetos devem executar etapas adicionais para garantir que as interfaces são empacotadas corretamente. Normalmente, isso envolve armazenar os ponteiros de interface no GIT e Obtendo o ponteiro de GIT cada vez que ele é usado. A classe `CComGITPtr` é fornecido para ajudar você a usar ponteiros de interface armazenados em do GIT.

> [!NOTE]
>  O recurso de tabela de interface global só está disponível no Windows 95 com DCOM versão 1.1 e posterior, Windows 98, Windows NT 4.0 com Service Pack 3 e posterior e Windows 2000.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atlbase. h

##  <a name="attach"></a>  CComGITPtr::Attach

Chame esse método para registrar o ponteiro de interface na tabela de interface global (GIT).

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>Parâmetros

*p*<br/>
O ponteiro de interface a ser adicionada para o GIT.

*dwCookie*<br/>
O cookie usado para identificar o ponteiro de interface.

### <a name="return-value"></a>Valor de retorno

Retorna S_OK no êxito ou um erro HRESULT em caso de falha.

### <a name="remarks"></a>Comentários

Em compilações de depuração, um erro de asserção ocorrerá se o GIT não é válido ou se o cookie é igual a NULL.

##  <a name="ccomgitptr"></a>  CComGITPtr::CComGITPtr

O construtor.

```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```

### <a name="parameters"></a>Parâmetros

*p*<br/>
[in] Um ponteiro de interface a ser armazenado na tabela de interface global (GIT).

*git*<br/>
[in] Uma referência a um existente `CComGITPtr` objeto.

*dwCookie*<br/>
[in] Um cookie usado para identificar o ponteiro de interface.

*rv*<br/>
[in] A fonte `CComGITPtr` objeto mover dados do.

### <a name="remarks"></a>Comentários

Cria um novo `CComGITPtr` do objeto, usando opcionalmente uma existente `CComGITPtr` objeto.

O construtor utilizando *rv* é um construtor de movimentação. Os dados são movidos da fonte de *rv*e então *rv* está desmarcada.

##  <a name="dtor"></a>  CComGITPtr::~CComGITPtr

O destruidor.

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>Comentários

Remove a interface da tabela de interface global (GIT), usando [CComGITPtr::Revoke](#revoke).

##  <a name="copyto"></a>  CComGITPtr::CopyTo

Chame esse método para copiar a interface da tabela de interface global (GIT) para o ponteiro passado.

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>Parâmetros

*pp*<br/>
O ponteiro que recebe a interface.

### <a name="return-value"></a>Valor de retorno

Retorna S_OK no êxito ou um erro HRESULT em caso de falha.

### <a name="remarks"></a>Comentários

A interface do GIT é copiada para o ponteiro passado. O ponteiro deve ser liberado, o chamador quando não for mais necessário.

##  <a name="detach"></a>  CComGITPtr::Detach

Chame esse método para desassociar a interface do `CComGITPtr` objeto.

```
DWORD Detach() throw();
```

### <a name="return-value"></a>Valor de retorno

Retorna o cookie do `CComGITPtr` objeto.

### <a name="remarks"></a>Comentários

É responsabilidade do chamador para remover a interface do GIT, usando [CComGITPtr::Revoke](#revoke).

##  <a name="getcookie"></a>  CComGITPtr::GetCookie

Chame esse método para retornar o cookie do `CComGITPtr` objeto.

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>Valor de retorno

Retorna o cookie.

### <a name="remarks"></a>Comentários

O cookie é uma variável usada para identificar uma interface e sua localização.

##  <a name="m_dwcookie"></a>  CComGITPtr::m_dwCookie

O cookie.

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>Comentários

O cookie é usada para identificar uma interface e seu local de uma variável de membro.

##  <a name="operator_eq"></a>  CComGITPtr::operator =

O operador de atribuição.

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>Parâmetros

*p*<br/>
[in] Um ponteiro para uma interface.

*git*<br/>
[in] Uma referência a um `CComGITPtr` objeto.

*dwCookie*<br/>
[in] Um cookie usado para identificar o ponteiro de interface.

*rv*<br/>
[in] O `CComGITPtr` para mover dados do.

### <a name="return-value"></a>Valor de retorno

Retorna o atualizada `CComGITPtr` objeto.

### <a name="remarks"></a>Comentários

Atribui um novo valor para um `CComGITPtr` objeto, de um objeto existente ou de uma referência a uma tabela de interface global.

##  <a name="operator_dword"></a>  CComGITPtr::operator DWORD

Retorna o cookie associado a `CComGITPtr` objeto.

```
operator DWORD() const;
```

### <a name="remarks"></a>Comentários

O cookie é uma variável usada para identificar uma interface e sua localização.

##  <a name="revoke"></a>  CComGITPtr::Revoke

Chame esse método para remover a interface atual da tabela de interface global (GIT).

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>Valor de retorno

Retorna S_OK no êxito ou um erro HRESULT em caso de falha.

### <a name="remarks"></a>Comentários

Remove a interface do GIT.

## <a name="see-also"></a>Consulte também

[Marshaler livre](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[Acessando as Interfaces entre Apartments](/windows/desktop/com/accessing-interfaces-across-apartments)<br/>
[Quando usar a tabela de Interface Global](/windows/desktop/com/when-to-use-the-global-interface-table)<br/>
[Visão geral da classe](../../atl/atl-class-overview.md)
