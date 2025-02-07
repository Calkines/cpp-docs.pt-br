---
title: Classe CSid
ms.date: 03/27/2019
f1_keywords:
- CSid
- ATLSECURITY/ATL::CSid
- ATLSECURITY/ATL::CSid::CSidArray
- ATLSECURITY/ATL::CSid::CSid
- ATLSECURITY/ATL::CSid::AccountName
- ATLSECURITY/ATL::CSid::Domain
- ATLSECURITY/ATL::CSid::EqualPrefix
- ATLSECURITY/ATL::CSid::GetLength
- ATLSECURITY/ATL::CSid::GetPSID
- ATLSECURITY/ATL::CSid::GetPSID_IDENTIFIER_AUTHORITY
- ATLSECURITY/ATL::CSid::GetSubAuthority
- ATLSECURITY/ATL::CSid::GetSubAuthorityCount
- ATLSECURITY/ATL::CSid::IsValid
- ATLSECURITY/ATL::CSid::LoadAccount
- ATLSECURITY/ATL::CSid::Sid
- ATLSECURITY/ATL::CSid::SidNameUse
helpviewer_keywords:
- CSid class
ms.assetid: be58b7ca-5958-49c3-a833-ca341aaaf753
ms.openlocfilehash: ed19ed3cdeb77612e20d826480ab73b9361366e9
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496445"
---
# <a name="csid-class"></a>Classe CSid

Essa classe é um wrapper para uma `SID` estrutura (identificador de segurança).

> [!IMPORTANT]
>  Essa classe e seus membros não podem ser usados em aplicativos que são executados no Windows Runtime.

## <a name="syntax"></a>Sintaxe

```
class CSid
```

## <a name="members"></a>Membros

### <a name="public-typedefs"></a>Typedefs públicos

|Nome|Descrição|
|----------|-----------------|
|[CSid::CSidArray](#csidarray)|Uma matriz de objetos de `CSid`.|

### <a name="public-constructors"></a>Construtores públicos

|Nome|Descrição|
|----------|-----------------|
|[CSid::CSid](#csid)|O construtor.|
|[CSid:: ~ CSid](#dtor)|O destruidor.|

### <a name="public-methods"></a>Métodos públicos

|Nome|Descrição|
|----------|-----------------|
|[CSid::AccountName](#accountname)|Retorna o nome da conta associada `CSid` ao objeto.|
|[CSid::Domain](#domain)|Retorna o nome do domínio associado `CSid` ao objeto.|
|[CSid::EqualPrefix](#equalprefix)|Prefixos `SID` (identificador de segurança) para igualdade.|
|[CSid::GetLength](#getlength)|Retorna o comprimento do `CSid` objeto.|
|[CSid::GetPSID](#getpsid)|Retorna um ponteiro para uma `SID` estrutura.|
|[CSid::GetPSID_IDENTIFIER_AUTHORITY](#getpsid_identifier_authority)|Retorna um ponteiro para a `SID_IDENTIFIER_AUTHORITY` estrutura.|
|[CSid::GetSubAuthority](#getsubauthority)|Retorna uma subautoridade especificada em uma `SID` estrutura.|
|[CSid::GetSubAuthorityCount](#getsubauthoritycount)|Retorna a contagem de subautoridades.|
|[CSid::IsValid](#isvalid)|Testa a `CSid` validade do objeto.|
|[CSid::LoadAccount](#loadaccount)|Atualiza o `CSid` objeto de acordo com o nome da conta e o domínio `SID` ou uma estrutura existente.|
|[CSid::Sid](#sid)|Retorna a cadeia de caracteres de ID.|
|[CSid::SidNameUse](#sidnameuse)|Retorna uma descrição do estado do `CSid` objeto.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator =](#operator_eq)|Operador de atribuição.|
|[SID de const do operador *](#operator_const_sid__star)|Converte um `CSid` objeto em um ponteiro para uma `SID` estrutura.|

### <a name="global-operators"></a>Operadores globais

|||
|-|-|
|[operador = =](#operator_eq_eq)|Testa dois objetos de descritor de segurança para igualdade|
|[operador! =](#operator_neq)|Testa dois objetos de descritor de segurança para desigualdade|
|[operador\<](#operator_lt)|Compara o valor relativo de dois objetos de descritor de segurança.|
|[> do operador](#operator_gt)|Compara o valor relativo de dois objetos de descritor de segurança.|
|[operador\<=](#operator_lt__eq)|Compara o valor relativo de dois objetos de descritor de segurança.|
|[> do operador =](#operator_gt__eq)|Compara o valor relativo de dois objetos de descritor de segurança.|

## <a name="remarks"></a>Comentários

A `SID` estrutura é uma estrutura de comprimento variável usada para identificar exclusivamente usuários ou grupos.

Os aplicativos não devem modificar `SID` a estrutura diretamente, mas sim usar os métodos fornecidos nesta classe wrapper. Consulte também [AtlGetOwnerSid](security-global-functions.md#atlgetownersid), [AtlSetGroupSid](security-global-functions.md#atlsetgroupsid), [AtlGetGroupSid](security-global-functions.md#atlgetgroupsid)e [AtlSetOwnerSid](security-global-functions.md#atlsetownersid).

Para obter uma introdução ao modelo de controle de acesso no Windows, consulte [controle de acesso](/windows/win32/SecAuthZ/access-control) no SDK do Windows.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** ATLSecurity. h

##  <a name="accountname"></a>  CSid::AccountName

Retorna o nome da conta associada `CSid` ao objeto.

```
LPCTSTR AccountName() const throw(...);
```

### <a name="return-value"></a>Valor de retorno

Retorna o LPCTSTR apontando para o nome da conta.

### <a name="remarks"></a>Comentários

Esse método tenta localizar um nome para o (identificador `SID` de segurança) especificado. Para obter detalhes completos, consulte [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Se nenhum nome de conta para `SID` o puder ser encontrado `AccountName` , retornará uma cadeia de caracteres vazia. Isso pode ocorrer se um tempo limite de rede impedir que esse método localize o nome. Ele também ocorre para identificadores de segurança sem nenhum nome de conta correspondente, como `SID` um que identifica uma sessão de entrada.

##  <a name="csid"></a>  CSid::CSid

O construtor.

```
CSid() throw();
CSid(const SID& rhs) throw(...);
CSid(const CSid& rhs) throw(...);

CSid(
    const SID_IDENTIFIER_AUTHORITY& IdentifierAuthority,
    BYTE nSubAuthorityCount,
    ...) throw(...);

explicit CSid(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

explicit CSid(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```

### <a name="parameters"></a>Parâmetros

*rhs*<br/>
Uma estrutura `CSid` de objeto `SID` ou (identificador de segurança) existente.

*IdentifierAuthority*<br/>
A autoridade.

*nSubAuthorityCount*<br/>
A contagem de subautoridades.

*pszAccountName*<br/>
O nome da conta.

*pszSystem*<br/>
O nome do sistema. Essa cadeia de caracteres pode ser o nome de um computador remoto. Se essa cadeia de caracteres for nula, o sistema local será usado.

*pSid*<br/>
Um ponteiro para uma `SID` estrutura.

### <a name="remarks"></a>Comentários

O construtor inicializa o `CSid` objeto, definindo um membro de dados interno para *SidTypeInvalid*ou copiando as `CSid`configurações de uma conta existente, `SID`ou existente.

Se a inicialização falhar, o Construtor gerará uma [classe CAtlException](../../atl/reference/catlexception-class.md).

##  <a name="dtor"></a>  CSid::~CSid

O destruidor.

```
virtual ~CSid() throw();
```

### <a name="remarks"></a>Comentários

O destruidor libera todos os recursos adquiridos pelo objeto.

##  <a name="csidarray"></a>  CSid::CSidArray

Uma matriz de objetos [CSid](../../atl/reference/csid-class.md) .

```
typedef CAtlArray<CSid> CSidArray;
```

### <a name="remarks"></a>Comentários

Este typedef especifica o tipo de matriz que pode ser usado para recuperar identificadores de segurança de uma ACL (lista de controle de acesso). Consulte [cacls:: GetAclEntries](../../atl/reference/cacl-class.md#getaclentries).

##  <a name="domain"></a>  CSid::Domain

Retorna o nome do domínio associado `CSid` ao objeto.

```
LPCTSTR Domain() const throw(...);
```

### <a name="return-value"></a>Valor de retorno

Retorna o `LPCTSTR` apontador para o domínio.

### <a name="remarks"></a>Comentários

Esse método tenta localizar um nome para o (identificador `SID` de segurança) especificado. Para obter detalhes completos, consulte [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw).

Se nenhum nome de conta para `SID` o puder ser encontrado `Domain` , retornará o domínio como uma cadeia de caracteres vazia. Isso pode ocorrer se um tempo limite de rede impedir que esse método localize o nome. Ele também ocorre para identificadores de segurança sem nenhum nome de conta correspondente, como `SID` um que identifica uma sessão de entrada.

##  <a name="equalprefix"></a>  CSid::EqualPrefix

Prefixos `SID` (identificador de segurança) para igualdade.

```
bool EqualPrefix(const SID& rhs) const throw();
bool EqualPrefix(const CSid& rhs) const throw();
```

### <a name="parameters"></a>Parâmetros

*rhs*<br/>
A `SID` estrutura ou `CSid` o objeto (identificador de segurança) a ser comparado.

### <a name="return-value"></a>Valor de retorno

Retorna verdadeiro em caso de êxito, falso em caso de falha.

### <a name="remarks"></a>Comentários

Consulte [EqualPrefixSid](/windows/win32/api/securitybaseapi/nf-securitybaseapi-equalprefixsid) no SDK do Windows para obter mais detalhes.

##  <a name="getlength"></a>  CSid::GetLength

Retorna o comprimento do `CSid` objeto.

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>Valor de retorno

Retorna o comprimento em bytes do `CSid` objeto.

### <a name="remarks"></a>Comentários

Se a `CSid` estrutura não for válida, o valor de retorno será indefinido. Antes de `GetLength`chamar, use a `CSid` função de membro [CSid:: IsValid](#isvalid) para verificar se é válido.

> [!NOTE]
>  Em depuração compila a função causará uma declaração se `CSid` o objeto não for válido.

##  <a name="getpsid"></a>  CSid::GetPSID

Retorna um ponteiro para uma `SID` estrutura (identificador de segurança).

```
const SID* GetPSID() const throw(...);
```

### <a name="return-value"></a>Valor de retorno

Retorna o endereço da `CSid` estrutura subjacente `SID` do objeto.

##  <a name="getpsid_identifier_authority"></a>  CSid::GetPSID_IDENTIFIER_AUTHORITY

Retorna um ponteiro para a `SID_IDENTIFIER_AUTHORITY` estrutura.

```
const SID_IDENTIFIER_AUTHORITY* GetPSID_IDENTIFIER_AUTHORITY() const throw();
```

### <a name="return-value"></a>Valor de retorno

Se o método tiver sucesso, ele retornará o endereço da `SID_IDENTIFIER_AUTHORITY` estrutura. Se falhar, o valor de retorno será indefinido. A falha poderá ocorrer se `CSid` o objeto não for válido; nesse caso, o método [CSid:: IsValid](#isvalid) retornará false. A função `GetLastError` pode ser chamada para obter informações de erro estendidas.

> [!NOTE]
>  Em depuração compila a função causará uma declaração se `CSid` o objeto não for válido.

##  <a name="getsubauthority"></a>  CSid::GetSubAuthority

Retorna uma subautoridade especificada em uma `SID` estrutura (identificador de segurança).

```
DWORD GetSubAuthority(DWORD nSubAuthority) const throw();
```

### <a name="parameters"></a>Parâmetros

*nSubAuthority*<br/>
A subautoridade.

### <a name="return-value"></a>Valor de retorno

Retorna a subautoridade referenciada por *nSubAuthority.* O valor de subautoridade é um RID (identificador relativo).

### <a name="remarks"></a>Comentários

O parâmetro *nSubAuthority* especifica um valor de índice que identifica o elemento de matriz de subautoridade que o método retornará. O método não executa testes de validação nesse valor. Um aplicativo pode chamar [CSid:: GetSubAuthorityCount](#getsubauthoritycount) para descobrir o intervalo de valores aceitáveis.

> [!NOTE]
>  Em depuração compila a função causará uma declaração se `CSid` o objeto não for válido.

##  <a name="getsubauthoritycount"></a>  CSid::GetSubAuthorityCount

Retorna a contagem de subautoridades.

```
UCHAR GetSubAuthorityCount() const throw();
```

### <a name="return-value"></a>Valor de retorno

Se o método tiver sucesso, o valor de retorno será a contagem de subautoridade.

Se o método falhar, o valor de retorno será indefinido. O método falhará se `CSid` o objeto for inválido. Para obter outras informações sobre o erro, chame `GetLastError`.

> [!NOTE]
>  Em depuração compila a função causará uma declaração se `CSid` o objeto não for válido.

##  <a name="isvalid"></a>  CSid::IsValid

Testa a `CSid` validade do objeto.

```
bool IsValid() const throw();
```

### <a name="return-value"></a>Valor de retorno

Retornará true se o `CSid` objeto for válido, false se não for. Não há informações de erro estendidas para esse método; Não chame `GetLastError`.

### <a name="remarks"></a>Comentários

O `IsValid` método valida o `CSid` objeto verificando se o número de revisão está dentro de um intervalo conhecido e se o número de subautons é menor que o máximo.

##  <a name="loadaccount"></a>  CSid::LoadAccount

Atualiza o `CSid` objeto de acordo com o nome e o domínio da conta ou uma estrutura de Sid (identificador de segurança) existente.

```
bool LoadAccount(
    LPCTSTR pszAccountName,
    LPCTSTR pszSystem = NULL) throw(...);

bool LoadAccount(
    const SID* pSid,
    LPCTSTR pszSystem = NULL) throw(...);
```

### <a name="parameters"></a>Parâmetros

*pszAccountName*<br/>
O nome da conta.

*pszSystem*<br/>
O nome do sistema. Essa cadeia de caracteres pode ser o nome de um computador remoto. Se essa cadeia de caracteres for nula, o sistema local será usado.

*pSid*<br/>
Um ponteiro para uma estrutura de [Sid](/windows/win32/api/winnt/ns-winnt-sid) .

### <a name="return-value"></a>Valor de retorno

Retorna verdadeiro em caso de êxito, falso em caso de falha. Para obter outras informações sobre o erro, chame `GetLastError`.

### <a name="remarks"></a>Comentários

`LoadAccount`tenta localizar um identificador de segurança para o nome especificado. Consulte [LookupAccountSid](/windows/win32/api/winbase/nf-winbase-lookupaccountsidw) para obter mais detalhes.

##  <a name="operator_eq"></a>CSid:: Operator =

Operador de atribuição.

```
CSid& operator= (const CSid& rhs) throw(...);
CSid& operator= (const SID& rhs) throw(...);
```

### <a name="parameters"></a>Parâmetros

*rhs*<br/>
O `SID` (identificador de segurança) `CSid` ou para atribuir ao `CSid` objeto.

### <a name="return-value"></a>Valor de retorno

Retorna uma referência ao objeto atualizado `CSid` .

##  <a name="operator_eq_eq"></a>CSid:: Operator = =

Testa dois objetos de descritor de segurança para igualdade.

```
bool operator==(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parâmetros

*lhs*<br/>
O `SID` (identificador de segurança) `CSid` ou que aparece no lado esquerdo do operador = =.

*rhs*<br/>
O `SID` (identificador de segurança) `CSid` ou que aparece no lado direito do operador = =.

### <a name="return-value"></a>Valor de retorno

TRUE se os descritores de segurança forem iguais, caso contrário, FALSE.

##  <a name="operator_neq"></a>CSid:: Operator! =

Testa dois objetos de descritor de segurança para desigualdade.

```
bool operator!=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parâmetros

*lhs*<br/>
O `SID` (identificador de segurança) `CSid` ou que aparece no lado esquerdo do operador! =.

*rhs*<br/>
O `SID` (identificador de segurança) `CSid` ou que aparece no lado direito do operador! =.

### <a name="return-value"></a>Valor de retorno

TRUE se os descritores de segurança não forem iguais, caso contrário, FALSE.

##  <a name="operator_lt"></a>Operador CSid::&lt;

Compara o valor relativo de dois objetos de descritor de segurança.

```
bool operator<(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parâmetros

*lhs*<br/>
O `SID` (identificador de segurança) `CSid` ou que aparece no lado esquerdo do operador! =.

*rhs*<br/>
O `SID` (identificador de segurança) `CSid` ou que aparece no lado direito do operador! =.

### <a name="return-value"></a>Valor de retorno

TRUE se o *LHS* for menor que *RHS*, caso contrário, false.

##  <a name="operator_lt__eq"></a>Operador CSid::&lt;=

Compara o valor relativo de dois objetos de descritor de segurança.

```
bool operator<=(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parâmetros

*lhs*<br/>
O `SID` (identificador de segurança) `CSid` ou que aparece no lado esquerdo do operador! =.

*rhs*<br/>
O `SID` (identificador de segurança) `CSid` ou que aparece no lado direito do operador! =.

### <a name="return-value"></a>Valor de retorno

TRUE se o *LHS* for menor ou igual ao *RHS*, caso contrário, false.

##  <a name="operator_gt"></a>Operador CSid::&gt;

Compara o valor relativo de dois objetos de descritor de segurança.

```
bool operator>(
    const CSid& lhs,
    const CSid& rhs) throw();
```

### <a name="parameters"></a>Parâmetros

*lhs*<br/>
O `SID` (identificador de segurança) `CSid` ou que aparece no lado esquerdo do operador! =.

*rhs*<br/>
O `SID` (identificador de segurança) `CSid` ou que aparece no lado direito do operador! =.

### <a name="return-value"></a>Valor de retorno

TRUE se o *LHS* for maior que *RHS*, caso contrário, false.

##  <a name="operator_gt__eq"></a>Operador CSid::&gt;=

Compara o valor relativo de dois objetos de descritor de segurança.

```
bool operator>=(
    const CSid& lhs,
    const CSid& rhs) throw());
```

### <a name="parameters"></a>Parâmetros

*lhs*<br/>
O `SID` (identificador de segurança) `CSid` ou que aparece no lado esquerdo do operador! =.

*rhs*<br/>
O `SID` (identificador de segurança) `CSid` ou que aparece no lado direito do operador! =.

### <a name="return-value"></a>Valor de retorno

TRUE se o *LHS* for maior ou igual ao *RHS*, caso contrário, false.

##  <a name="operator_const_sid__star"></a>SID CSid:: Operator const\*

Converte um `CSid` objeto em um ponteiro para uma `SID` estrutura (identificador de segurança).

```
operator const SID *() const throw(...);
```

### <a name="remarks"></a>Comentários

Retorna o endereço da `SID` estrutura.

##  <a name="sid"></a>  CSid::Sid

Retorna a `SID` estrutura (identificador de segurança) como uma cadeia de caracteres.

```
LPCTSTR Sid() const throw(...);
```

### <a name="return-value"></a>Valor de retorno

Retorna a `SID` estrutura como uma cadeia de caracteres em um formato adequado para exibição, armazenamento ou transmissão. Equivalente a [ConvertSidToStringSid](/windows/win32/api/sddl/nf-sddl-convertsidtostringsidw).

##  <a name="sidnameuse"></a>  CSid::SidNameUse

Retorna uma descrição do estado do `CSid` objeto.

```
SID_NAME_USE SidNameUse() const throw();
```

### <a name="return-value"></a>Valor de retorno

Retorna o valor do membro de dados que armazena um valor que descreve o estado do `CSid` objeto.

|Valor|Descrição|
|-----------|-----------------|
|SidTypeUser|Indica um usuário `SID` (identificador de segurança).|
|SidTypeGroup|Indica um grupo `SID`.|
|SidTypeDomain|Indica um domínio `SID`.|
|SidTypeAlias|Indica um alias `SID`.|
|SidTypeWellKnownGroup|Indica um `SID` para um grupo bem conhecido.|
|SidTypeDeletedAccount|Indica um `SID` para uma conta excluída.|
|SidTypeInvalid|Indica um inválido `SID`.|
|SidTypeUnknown|Indica um tipo `SID` desconhecido.|
|SidTypeComputer|Indica um `SID` para um computador.|

### <a name="remarks"></a>Comentários

Chame [CSid:: LoadAccount](#loadaccount) para atualizar o `CSid` objeto antes de `SidNameUse` chamar para retornar seu estado. `SidNameUse`Não altera o estado do objeto (chamando para `LookupAccountName` ou `LookupAccountSid`), mas apenas retorna o estado atual.

## <a name="see-also"></a>Consulte também

[Exemplo de segurança](../../overview/visual-cpp-samples.md)<br/>
[Visão geral da classe](../../atl/atl-class-overview.md)<br/>
[Funções globais de segurança](../../atl/reference/security-global-functions.md)<br/>
[Operadores](../../atl/reference/atl-operators.md)
