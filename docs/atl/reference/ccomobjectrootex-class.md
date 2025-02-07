---
title: Classe CComObjectRootEx
ms.date: 11/04/2016
f1_keywords:
- CComObjectRootEx
- ATLCOM/ATL::CComObjectRootEx
- ATLCOM/ATL::InternalAddRef
- ATLCOM/ATL::InternalRelease
- ATLCOM/ATL::Lock
- ATLCOM/ATL::Unlock
- ATLCOM/ATL::FinalConstruct
- ATLCOM/ATL::FinalRelease
- ATLCOM/ATL::OuterAddRef
- ATLCOM/ATL::OuterQueryInterface
- ATLCOM/ATL::OuterRelease
- ATLCOM/ATL::InternalQueryInterface
- ATLCOM/ATL::ObjectMain
- ATLCOM/ATL::m_dwRef
- ATLCOM/ATL::m_pOuterUnknown
helpviewer_keywords:
- reference counting
ms.assetid: 894a3d7c-2daf-4fd0-8fa4-e6a05bcfb631
ms.openlocfilehash: 8fa4e7a035ded2e1a20dd278a5d54d40252e1958
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497045"
---
# <a name="ccomobjectrootex-class"></a>Classe CComObjectRootEx

Essa classe fornece métodos para manipular o gerenciamento de contagem de referência de objeto para objetos não agregados e agregados.

## <a name="syntax"></a>Sintaxe

```
template<class ThreadModel>
class CComObjectRootEx : public CComObjectRootBase
```

#### <a name="parameters"></a>Parâmetros

*ThreadModel*<br/>
A classe cujos métodos implementam o modelo de threading desejado. Você pode escolher explicitamente o modelo de Threading definindo *ThreadModel* como [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md), [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)ou [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md). Você pode aceitar o modelo de thread padrão do servidor definindo *ThreadModel* como [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) ou [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel).

## <a name="members"></a>Membros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CComObjectRootEx](#ccomobjectrootex)|Construtor.|
|[InternalAddRef](#internaladdref)|Incrementa a contagem de referência para um objeto não agregado.|
|[InternalRelease](#internalrelease)|Decrementa a contagem de referência para um objeto não agregado.|
|[Proprietário](#lock)|Se o modelo de thread for multi-threaded, o obterá a propriedade de um objeto de seção crítica.|
|[Automático](#unlock)|Se o modelo de thread for multi-threaded, o liberará a propriedade de um objeto de seção crítica.|

### <a name="ccomobjectrootbase-methods"></a>Métodos CComObjectRootBase

|||
|-|-|
|[FinalConstruct](#finalconstruct)|Substitua em sua classe para executar qualquer inicialização exigida pelo seu objeto.|
|[FinalRelease](#finalrelease)|Substitua em sua classe para executar qualquer limpeza exigida pelo seu objeto.|
|[OuterAddRef](#outeraddref)|Incrementa a contagem de referência para um objeto agregado.|
|[OuterQueryInterface](#outerqueryinterface)|Delega para a externa `IUnknown` de um objeto agregado.|
|[OuterRelease](#outerrelease)|Decrementa a contagem de referência para um objeto agregado.|

### <a name="static-functions"></a>Funções estáticas

|||
|-|-|
|[InternalQueryInterface](#internalqueryinterface)|Delega para o `IUnknown` de um objeto não agregado.|
|[ObjectMain](#objectmain)|Chamado durante a inicialização e terminação do módulo para classes derivadas listadas no mapa de objetos.|

### <a name="data-members"></a>Membros de Dados

|||
|-|-|
|[m_dwRef](#m_dwref)|Com `m_pOuterUnknown`o, parte de uma União. Usado quando o objeto não é agregado para manter a contagem de referência `AddRef` de `Release`e.|
|[m_pOuterUnknown](#m_pouterunknown)|Com `m_dwRef`o, parte de uma União. Usado quando o objeto é agregado para manter um ponteiro para o desconhecido externo.|

## <a name="remarks"></a>Comentários

`CComObjectRootEx`manipula o gerenciamento de contagem de referência de objeto para objetos não agregados e agregados. Ela conterá a contagem de referências de objetos se o objeto não estiver sendo agregado e manterá o ponteiro para o desconhecido externo se o objeto estiver sendo agregado. Para objetos agregados, `CComObjectRootEx` os métodos podem ser usados para lidar com a falha do objeto interno a ser construído e para proteger o objeto externo da exclusão quando interfaces internas são liberadas ou o objeto interno é excluído.

Uma classe que implementa um servidor com deve herdar `CComObjectRootEx` de ou [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md).

Se a definição de classe especificar a macro [DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable) , a ATL criará `CComPolyObject<CYourClass>` uma `IClassFactory::CreateInstance` instância de quando for chamada. Durante a criação, o valor da externa Unknown é verificado. Se for NULL, `IUnknown` será implementado para um objeto não agregado. Se o desconhecido externo não for nulo, `IUnknown` será implementado para um objeto agregado.

Se sua classe não especificar a macro DECLARE_POLY_AGGREGATABLE, a ATL criará uma instância `CAggComObject<CYourClass>` do para objetos agregados ou uma instância `CComObject<CYourClass>` do para objetos não agregados.

A vantagem de usar `CComPolyObject` o é que você evita ter `CComAggObject` ambos `CComObject` e em seu módulo para lidar com os casos agregados e não agregados. Um único `CComPolyObject` objeto trata ambos os casos. Portanto, apenas uma cópia da vtable e uma cópia das funções existem no seu módulo. Se a vtable for grande, isso poderá diminuir substancialmente o tamanho do módulo. No entanto, se a vtable for pequena `CComPolyObject` , o uso do pode resultar em um tamanho de módulo ligeiramente maior porque ele não é otimizado para um objeto agregado ou `CComAggObject` não `CComObject`agregado, como são e.

Se o objeto for agregado, [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) será implementado pelo `CComAggObject` ou `CComPolyObject`. Essas classes `QueryInterface`delegam `AddRef`,, `Release` e chamam `CComObjectRootEx`para `OuterQueryInterface`' `OuterAddRef`s, `OuterRelease` e para encaminhar para o desconhecido externo. Normalmente, você substitui `CComObjectRootEx::FinalConstruct` em sua classe para criar qualquer objeto agregado e substituir `CComObjectRootEx::FinalRelease` para liberar todos os objetos agregados.

Se o objeto não for agregado, `IUnknown` será implementado pelo `CComObject` ou `CComPolyObject`. Nesse caso, as chamadas para `QueryInterface`, `AddRef`, e `Release` são delegadas a `CComObjectRootEx` `InternalQueryInterface` `InternalAddRef`, e `InternalRelease` para executar as operações reais.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** atlcom. h

##  <a name="ccomobjectrootex"></a>CComObjectRootEx::CComObjectRootEx

O construtor inicializa a contagem de referência como 0.

```
CComObjectRootEx();
```

##  <a name="finalconstruct"></a>  CComObjectRootEx::FinalConstruct

Você pode substituir esse método em sua classe derivada para executar qualquer inicialização necessária para seu objeto.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Valor de retorno

Retorne S_OK em caso de êxito ou um dos valores HRESULT de erro padrão.

### <a name="remarks"></a>Comentários

Por padrão, `CComObjectRootEx::FinalConstruct` o simplesmente retorna S_OK.

Há vantagens em executar a inicialização em `FinalConstruct` vez do construtor de sua classe:

- Não é possível retornar um código de status de um construtor, mas você pode retornar um HRESULT por `FinalConstruct`meio do valor de retorno. Quando os objetos da sua classe estão sendo criados usando a fábrica de classes padrão fornecida pela ATL, esse valor de retorno é propagado de volta para o cliente COM, permitindo que você forneça informações detalhadas sobre o erro.

- Você não pode chamar funções virtuais por meio do mecanismo de função virtual do construtor de uma classe. Chamar uma função virtual do construtor de uma classe resulta em uma chamada resolvida estaticamente para a função conforme ela é definida nesse ponto na hierarquia de herança. Chamadas para funções virtuais puras resultam em erros de vinculador.

   Sua classe não é a classe mais derivada na hierarquia de herança — ela se baseia em uma classe derivada fornecida pela ATL para fornecer algumas de suas funcionalidades. Há uma boa chance de que sua inicialização precise usar os recursos fornecidos pela classe (isso certamente é verdade quando os objetos de sua classe precisam agregar outros objetos), mas o Construtor em sua classe não tem como acessar esses recursos. O código de construção para sua classe é executado antes que a classe mais derivada seja totalmente construída.

   No entanto, `FinalConstruct` é chamado imediatamente depois que a classe mais derivada é totalmente construída, permitindo que você chame funções virtuais e use a implementação de contagem de referência fornecida pela ATL.

### <a name="example"></a>Exemplo

Normalmente, substitua esse método na classe derivada de `CComObjectRootEx` para criar qualquer objeto agregado. Por exemplo:

[!code-cpp[NVC_ATL_COM#40](../../atl/codesnippet/cpp/ccomobjectrootex-class_1.h)]

Se a construção falhar, você poderá retornar um erro. Você também pode usar a macro [DECLARE_PROTECT_FINAL_CONSTRUCT](aggregation-and-class-factory-macros.md#declare_protect_final_construct) para proteger seu objeto externo de ser excluído se, durante a criação, o objeto agregado interno incrementar a contagem de referência, e decrementar a contagem para 0.

Aqui está uma maneira típica de criar uma agregação:

- Adicione um `IUnknown` ponteiro ao seu objeto de classe e inicialize-o como NULL no construtor.

- Substitua `FinalConstruct` para criar a agregação.

- Use o `IUnknown` ponteiro que você definiu como o parâmetro para a macro [COM_INTERFACE_ENTRY_AGGREGATE](com-interface-entry-macros.md#com_interface_entry_aggregate) .

- Substitua `FinalRelease` para liberar o `IUnknown` ponteiro.

##  <a name="finalrelease"></a>CComObjectRootEx::FinalRelease

Você pode substituir esse método em sua classe derivada para executar qualquer limpeza necessária para seu objeto.

```
void FinalRelease();
```

### <a name="remarks"></a>Comentários

Por padrão, `CComObjectRootEx::FinalRelease` não faz nada.

Executar a limpeza `FinalRelease` no é preferível a adicionar código ao destruidor de sua classe, pois o objeto ainda está totalmente construído no ponto em `FinalRelease` que é chamado. Isso permite que você acesse com segurança os métodos fornecidos pela classe mais derivada. Isso é particularmente importante para a liberação de qualquer objeto agregado antes da exclusão.

##  <a name="internaladdref"></a>  CComObjectRootEx::InternalAddRef

Incrementa a contagem de referência de um objeto não agregado em 1.

```
ULONG InternalAddRef();
```

### <a name="return-value"></a>Valor de retorno

Um valor que pode ser útil para diagnóstico e teste.

### <a name="remarks"></a>Comentários

Se o modelo de thread for multi-threaded, `InterlockedIncrement` será usado para impedir que mais de um thread altere a contagem de referência ao mesmo tempo.

##  <a name="internalqueryinterface"></a>  CComObjectRootEx::InternalQueryInterface

Recupera um ponteiro para a interface solicitada.

```
static HRESULT InternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>Parâmetros

*pThis*<br/>
no Um ponteiro para o objeto que contém o mapa COM de interfaces expostas para `QueryInterface`.

*pEntries*<br/>
no Um ponteiro para a `_ATL_INTMAP_ENTRY` estrutura que acessa um mapa de interfaces disponíveis.

*iid*<br/>
no O GUID da interface que está sendo solicitada.

*ppvObject*<br/>
fora Um ponteiro para o ponteiro de interface especificado em *IID*ou NULL se a interface não for encontrada.

### <a name="return-value"></a>Valor de retorno

Um dos valores de HRESULT padrão.

### <a name="remarks"></a>Comentários

`InternalQueryInterface` somente lida com interfaces na tabela de mapa COM. Se o objeto for agregado, `InternalQueryInterface` o não delegará para o desconhecido externo. Você pode inserir interfaces na tabela de mapa com com a macro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) ou uma de suas variantes.

##  <a name="internalrelease"></a>CComObjectRootEx::InternalRelease

Decrementa a contagem de referência de um objeto não agregado em 1.

```
ULONG InternalRelease();
```

### <a name="return-value"></a>Valor de retorno

Em compilações de não depuração e depuração, essa função retorna um valor que pode ser útil para diagnóstico ou teste. O valor exato retornado depende de muitos fatores, como o sistema operacional usado, e pode ou não ser a contagem de referência.

### <a name="remarks"></a>Comentários

Se o modelo de thread for multi-threaded, `InterlockedDecrement` será usado para impedir que mais de um thread altere a contagem de referência ao mesmo tempo.

##  <a name="lock"></a>CComObjectRootEx:: Lock

Se o modelo de thread for multi-threaded, esse método chamará a função de API do Win32 [EnterCriticalSection](/windows/win32/api/synchapi/nf-synchapi-entercriticalsection), que aguarda até que o thread possa assumir a propriedade do objeto de seção crítica obtido por meio de um membro de dados privado.

```
void Lock();
```

### <a name="remarks"></a>Comentários

Quando o código protegido termina de ser executado, o thread `Unlock` deve chamar para liberar a propriedade da seção crítica.

Se o modelo de thread for de thread único, esse método não fará nada.

##  <a name="m_dwref"></a>  CComObjectRootEx::m_dwRef

Parte de uma União que acessa quatro bytes de memória.

```
long m_dwRef;
```

### <a name="remarks"></a>Comentários

Com `m_pOuterUnknown`o, parte de uma União:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Se o objeto não for agregado, a contagem de referência acessada pelo `AddRef` e `m_dwRef` `Release` será armazenada em. Se o objeto for agregado, o ponteiro para o desconhecido externo será armazenado em [m_pOuterUnknown](#m_pouterunknown).

##  <a name="m_pouterunknown"></a>  CComObjectRootEx::m_pOuterUnknown

Parte de uma União que acessa quatro bytes de memória.

```
IUnknown*
    m_pOuterUnknown;
```

### <a name="remarks"></a>Comentários

Com `m_dwRef`o, parte de uma União:

```
union {
    long m_dwRef;
    IUnknown* m_pOuterUnknown;
};
```

Se o objeto for agregado, o ponteiro para o desconhecido externo será armazenado em `m_pOuterUnknown`. Se o objeto não for agregado, a contagem de referência acessada pelo `AddRef` e `Release` será armazenada em [m_dwRef](#m_dwref).

##  <a name="objectmain"></a>CComObjectRootEx:: ObjectMain

Para cada classe listada no mapa de objetos, essa função é chamada uma vez quando o módulo é inicializado e novamente quando é encerrada.

```
static void WINAPI ObjectMain(bool bStarting);
```

### <a name="parameters"></a>Parâmetros

*bStarting*<br/>
fora O valor será TRUE se a classe estiver sendo inicializada; caso contrário, FALSE.

### <a name="remarks"></a>Comentários

O valor do parâmetro *bStarting* indica se o módulo está sendo inicializado ou encerrado. A implementação padrão de `ObjectMain` não faz nada, mas você pode substituir essa função em sua classe para inicializar ou limpar os recursos que deseja alocar para a classe. Observe que `ObjectMain` é chamado antes de qualquer instância da classe ser solicitada.

`ObjectMain`é chamado a partir do ponto de entrada da DLL, portanto, o tipo de operação que a função de ponto de entrada pode executar é restrito. Para obter mais informações sobre essas restrições, consulte [DLLs e C++ o comportamento da biblioteca de tempo de execução Visual](../../build/run-time-library-behavior.md) e [DllMain](/windows/win32/Dlls/dllmain).

### <a name="example"></a>Exemplo

[!code-cpp[NVC_ATL_COM#41](../../atl/codesnippet/cpp/ccomobjectrootex-class_2.h)]

##  <a name="outeraddref"></a>  CComObjectRootEx::OuterAddRef

Incrementa a contagem de referência do desconhecido externo de uma agregação.

```
ULONG OuterAddRef();
```

### <a name="return-value"></a>Valor de retorno

Um valor que pode ser útil para diagnóstico e teste.

##  <a name="outerqueryinterface"></a>  CComObjectRootEx::OuterQueryInterface

Recupera um ponteiro indireto para a interface solicitada.

```
HRESULT OuterQueryInterface(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parâmetros

*iid*<br/>
no O GUID da interface que está sendo solicitada.

*ppvObject*<br/>
fora Um ponteiro para o ponteiro de interface especificado em *IID*ou NULL se a agregação não oferecer suporte à interface.

### <a name="return-value"></a>Valor de retorno

Um dos valores de HRESULT padrão.

##  <a name="outerrelease"></a>CComObjectRootEx::OuterRelease

Decrementa a contagem de referência do desconhecido externo de uma agregação.

```
ULONG OuterRelease();
```

### <a name="return-value"></a>Valor de retorno

Em compilações não depuradas, sempre retorna 0. Em compilações de depuração, retorna um valor que pode ser útil para diagnóstico ou teste.

##  <a name="unlock"></a>CComObjectRootEx:: desbloquear

Se o modelo de thread for multi-threaded, esse método chamará a função de API do Win32 [LeaveCriticalSection](/windows/win32/api/synchapi/nf-synchapi-leavecriticalsection), que libera a propriedade do objeto de seção crítica obtido por meio de um membro de dados privado.

```
void Unlock();
```

### <a name="remarks"></a>Comentários

Para obter a propriedade, o thread deve `Lock`chamar. Cada chamada para `Lock` requer uma chamada correspondente para `Unlock` para liberar a propriedade da seção crítica.

Se o modelo de thread for de thread único, esse método não fará nada.

## <a name="see-also"></a>Consulte também

[Classe CComAggObject](../../atl/reference/ccomaggobject-class.md)<br/>
[Classe CComObject](../../atl/reference/ccomobject-class.md)<br/>
[Classe CComPolyObject](../../atl/reference/ccompolyobject-class.md)<br/>
[Visão geral da classe](../../atl/atl-class-overview.md)
