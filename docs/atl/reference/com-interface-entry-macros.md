---
title: Macros de entrada da Interface COM | Microsoft Docs
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, COM interface entry macros
ms.assetid: 19dcb768-2e1f-4b8d-a618-453a01a4bd00
caps.latest.revision: 16
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 7e9eb155d10a0a05916fc5f74cbe58fdf14b7475
ms.lasthandoff: 03/31/2017

---

# <a name="cominterfaceentry-macros"></a>Macros COM_INTERFACE_ENTRY  
 Essas macros inserirem interfaces de um objeto em seu mapa de COM para que eles possam ser acessados por `QueryInterface`. A ordem das entradas no mapa COM é que as interfaces de ordem serão verificadas para encontrar uma correspondência **IID** durante `QueryInterface`.  

 |||
 |-|-|
 |[COM_INTERFACE_ENTRY](#com_interface_entry)|Insere interfaces no mapa de interface COM.|  
|[COM_INTERFACE_ENTRY2](#com_interface_entry2)|Use esta macro para resolver a ambiguidade duas ramificações de herança.|  
|[COM_INTERFACE_ENTRY_IID](#com_interface_entry_iid)|Use esta macro para inserir a interface para o mapa COM e especifique seu IID.|  
|[COM_INTERFACE_ENTRY2_IID](#com_interface_entry2_iid)|Mesmo que [COM_INTERFACE_ENTRY2](#com_interface_entry2), exceto que você pode especificar um IID diferente.|  
|[COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate)|Quando a interface é identificado por `iid` é consultada, `COM_INTERFACE_ENTRY_AGGREGATE` encaminha para `punk`.|  
|[COM_INTERFACE_ENTRY_AGGREGATE_BLIND](#com_interface_entry_aggregate_blind)|Mesmo que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), exceto que consultar qualquer IID resulta em encaminhamento a consulta `punk`.|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate)|Mesmo que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), exceto se `punk` é **nulo**, ele cria automaticamente a agregação descrita pelo `clsid`.|  
|[COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND](#com_interface_entry_autoaggregate_blind)|Mesmo que [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), exceto que consultar qualquer IID resulta em encaminhamento a consulta `punk`e se `punk` é **nulo**, automaticamente criando a agregação descrita pelo `clsid`.|  
|[COM_INTERFACE_ENTRY_BREAK](#com_interface_entry_break)|Faz com que o programa chamar [DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297) quando a interface especificada é consultada para.|  
|[COM_INTERFACE_ENTRY_CACHED_TEAR_OFF](#com_interface_entry_cached_tear_off)|Salva os dados específicos à interface para cada instância.|  
|[COM_INTERFACE_ENTRY_TEAR_OFF](#com_interface_entry_tear_off)|Expõe as interfaces destacável.|  
|[COM_INTERFACE_ENTRY_CHAIN](#com_interface_entry_chain)|Processa o mapa COM da classe base quando o processamento atinge essa entrada no mapa de COM.|  
|[COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func)|Um mecanismo geral para a conexão do ATL `QueryInterface` lógica.|  
|[COM_INTERFACE_ENTRY_FUNC_BLIND](#com_interface_entry_func_blind)|Mesmo que [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), exceto que consultar qualquer IID resulta em uma chamada para `func`.|  
|[COM_INTERFACE_ENTRY_NOINTERFACE](#com_interface_entry_nointerface)|Retorna **E_NOINTERFACE** e termina COM o mapa processamento quando a interface especificada é consultada para.|  


## <a name="com_interface_entry"></a>COM_INTERFACE_ENTRY
Insere interfaces no mapa de interface COM.

### <a name="syntax"></a>Sintaxe

```
COM_INTERFACE_ENTRY( x )
```
### <a name="parameters"></a>Parâmetros

x [in] o nome de uma interface seu objeto de classe deriva diretamente.

### <a name="remarks"></a>Comentários
Normalmente, esse é o tipo de entrada usados com mais frequência.

### <a name="example"></a>Exemplo
```cpp
BEGIN_COM_MAP(CThisExample)
   COM_INTERFACE_ENTRY(IThisExample)
   COM_INTERFACE_ENTRY(IDispatch)
   COM_INTERFACE_ENTRY(ISupportErrorInfo)
END_COM_MAP()
```
### <a name="requirements"></a>Requisitos
**Cabeçalho:** atlcom.h
  
##  <a name="com_interface_entry2"></a>COM_INTERFACE_ENTRY2  
 Use esta macro para resolver a ambiguidade duas ramificações de herança.  
  
```
COM_INTERFACE_ENTRY2(x, x2)
```  
  
### <a name="parameters"></a>Parâmetros  
 *x*  
 [in] O nome de uma interface que você deseja expor de seu objeto.  
  
 `x2`  
 [in] O nome da ramificação da qual herança *x* é exposto.  
  
### <a name="remarks"></a>Comentários  
 Por exemplo, se você derivar seu objeto de classe de duas interfaces duplas, expor `IDispatch` usando `COM_INTERFACE_ENTRY2` como `IDispatch` pode ser obtido de qualquer uma das interfaces.  
  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATL_Windowing #118](../../atl/codesnippet/cpp/com-map-macros_2.h)]  
  
##  <a name="com_interface_entry_iid"></a>COM_INTERFACE_ENTRY_IID  
 Use esta macro para inserir a interface para o mapa COM e especifique seu IID.  
  
```
COM_INTERFACE_ENTRY_IID(iid, x)
```  
  
### <a name="parameters"></a>Parâmetros  
 `iid`  
 [in] O GUID da interface exposto.  
  
 *x*  
 [in] O nome da classe cuja vtable será exposto como a interface identificada por `iid`.  
  
 
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATL_Windowing #117](../../atl/codesnippet/cpp/com-map-macros_3.h)]  
  
##  <a name="com_interface_entry2_iid"></a>COM_INTERFACE_ENTRY2_IID  
 Mesmo que [COM_INTERFACE_ENTRY2](#com_interface_entry2), exceto que você pode especificar um IID diferente.  
  
```
COM_INTERFACE_ENTRY2_IID(iid, x, x2)
```   
  
### <a name="parameters"></a>Parâmetros  
 `iid`  
 [in] O GUID que você está especificando para a interface.  
  
 *x*  
 [in] O nome de uma interface que seu objeto de classe deriva diretamente.  
  
 `x2`  
 [in] O nome de uma segunda interface que seu objeto de classe deriva diretamente.  
  
##  <a name="com_interface_entry_aggregate"></a>COM_INTERFACE_ENTRY_AGGREGATE  
 Quando a interface é identificado por `iid` é consultada, `COM_INTERFACE_ENTRY_AGGREGATE` encaminha para `punk`.  
  
```
COM_INTERFACE_ENTRY_AGGREGATE(iid, punk)
```  
  
### <a name="parameters"></a>Parâmetros  
 `iid`  
 [in] O GUID da interface pesquisado.  
  
 `punk`  
 [in] O nome de um **IUnknown** ponteiro.  
  
### <a name="remarks"></a>Comentários  
 O `punk` parâmetro será assumido para apontar para o desconhecido interno de uma agregação ou a **nulo**, caso em que a entrada será ignorada. Normalmente, você faria **CoCreate** a agregação em `FinalConstruct`.  
  
  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATL_Windowing #112](../../atl/codesnippet/cpp/com-map-macros_4.h)]  
  
##  <a name="com_interface_entry_aggregate_blind"></a>COM_INTERFACE_ENTRY_AGGREGATE_BLIND  
 Mesmo que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), exceto que consultar qualquer IID resulta em encaminhamento a consulta `punk`.  
  
```
COM_INTERFACE_ENTRY_AGGREGATE_BLIND(punk)
```  
  
### <a name="parameters"></a>Parâmetros  
 `punk`  
 [in] O nome de um **IUnknown** ponteiro.  
  
### <a name="remarks"></a>Comentários  
 Se a consulta de interface falhar, o processamento do mapa COM continuará.  
  
  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATL_Windowing #113](../../atl/codesnippet/cpp/com-map-macros_5.h)]  
  

##  <a name="com_interface_entry_autoaggregate"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE  
 Mesmo que [COM_INTERFACE_ENTRY_AGGREGATE](#com_interface_entry_aggregate), exceto se `punk` é **nulo**, ele cria automaticamente a agregação descrita pelo `clsid`.  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE(iid, punk, clsid)
```   
  
### <a name="parameters"></a>Parâmetros  
 `iid`  
 [in] O GUID da interface pesquisado.  
  
 `punk`  
 [in] O nome de um **IUnknown** ponteiro. Deve ser um membro da classe que contém o mapa COM.  
  
 `clsid`  
 [in] O identificador da agregação que será criado se `punk` é **nulo**.  
  
### <a name="remarks"></a>Comentários  
  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATL_Windowing #114](../../atl/codesnippet/cpp/com-map-macros_6.h)]  
  
##  <a name="com_interface_entry_autoaggregate_blind"></a>COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND  
 Mesmo que [COM_INTERFACE_ENTRY_AUTOAGGREGATE](#com_interface_entry_autoaggregate), exceto que consultar qualquer IID resulta em encaminhamento a consulta `punk`e se `punk` é **nulo**, automaticamente criando a agregação descrita pelo `clsid`.  
  
```
COM_INTERFACE_ENTRY_AUTOAGGREGATE_BLIND(punk, clsid)
```  
  
### <a name="parameters"></a>Parâmetros  
 `punk`  
 [in] O nome de um **IUnknown** ponteiro. Deve ser um membro da classe que contém o mapa COM.  
  
 `clsid`  
 [in] O identificador da agregação que será criado se `punk` é **nulo**.  
  
### <a name="remarks"></a>Comentários  
 Se a consulta de interface falhar, o processamento do mapa COM continuará.  
  
  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATL_Windowing #115](../../atl/codesnippet/cpp/com-map-macros_7.h)]  
  
##  <a name="com_interface_entry_break"></a>COM_INTERFACE_ENTRY_BREAK  
 Faz com que o programa chamar [DebugBreak](http://msdn.microsoft.com/library/windows/desktop/ms679297) quando a interface especificada é consultada para.  
  
```
COM_INTERFACE_ENTRY_BREAK(x)
```  
  
### <a name="parameters"></a>Parâmetros  
 *x*  
 [in] Texto usado para construir o identificador de interface.  
  
### <a name="remarks"></a>Comentários  
 A interface IID será construído acrescentando *x* para `IID_`. Por exemplo, se *x* é `IPersistStorage`, será o IID `IID_IPersistStorage`.  
  
  
  
##  <a name="com_interface_entry_cached_tear_off"></a>COM_INTERFACE_ENTRY_CACHED_TEAR_OFF  
 Salva os dados específicos à interface para cada instância.  
  
```
COM_INTERFACE_ENTRY_CACHED_TEAR_OFF(iid, x, punk)
```   
  
### <a name="parameters"></a>Parâmetros  
 `iid`  
 [in] O GUID da interface destacável.  
  
 *x*  
 [in] O nome da classe que implementa a interface.  
  
 `punk`  
 [in] O nome de um **IUnknown** ponteiro. Deve ser um membro da classe que contém o mapa COM. Deve ser inicializado para **nulo** no construtor do objeto de classe.  
  
### <a name="remarks"></a>Comentários  
 Se a interface não for usada, isso reduz o tamanho geral da instância do objeto.  
  
  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATL_COM º 54](../../atl/codesnippet/cpp/com-map-macros_8.h)]  
  
##  <a name="com_interface_entry_tear_off"></a>COM_INTERFACE_ENTRY_TEAR_OFF  
 Expõe as interfaces destacável.  
  
```
COM_INTERFACE_ENTRY_TEAR_OFF(iid, x)
```  
  
### <a name="parameters"></a>Parâmetros  
 `iid`  
 [in] O GUID da interface destacável.  
  
 *x*  
 [in] O nome da classe que implementa a interface.  
  
### <a name="remarks"></a>Comentários  
 Uma interface destacável é implementada como um objeto separado que é criado toda vez que a interface que ele representa será consultado para. Normalmente, você criar sua interface como um destacáveis se a interface raramente é usada, pois isso salva um ponteiro vtable em cada instância do objeto principal. O destacável é excluído quando sua contagem de referência se torna zero. A classe que implementa o destacável deve ser derivada de `CComTearOffObjectBase` e têm seu próprio mapa de COM.  
  
  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATL_COM N º 1](../../atl/codesnippet/cpp/com-map-macros_1.h)]  
  
##  <a name="com_interface_entry_chain"></a>COM_INTERFACE_ENTRY_CHAIN  
 Processa o mapa COM da classe base quando o processamento atinge essa entrada no mapa de COM.  
  
```
COM_INTERFACE_ENTRY_CHAIN(classname)
```  
  
### <a name="parameters"></a>Parâmetros  
 *nome de classe*  
 [in] Uma classe base do objeto atual.  
  
### <a name="remarks"></a>Comentários  
 Por exemplo, no código a seguir:  
  
 [!code-cpp[NVC_ATL_Windowing #116](../../atl/codesnippet/cpp/com-map-macros_9.h)]  
  
 Observe que a primeira entrada no mapa COM deve ser uma interface no objeto que contém o mapa COM. Portanto, você não pode iniciar as entradas de mapa COM `COM_INTERFACE_ENTRY_CHAIN`, que faz com que o mapa COM de um objeto diferente a ser pesquisada no ponto onde **COM_INTERFACE_ENTRY_CHAIN (**`COtherObject`**)** aparece no mapa de COM do objeto. Se você deseja pesquisar o mapa COM outro objeto pela primeira vez, adicione uma entrada de interface para **IUnknown** no mapa de COM, em seguida, encadear mapa de COM do outro objeto. Por exemplo:  
  
 [!code-cpp[NVC_ATL_Windowing #111](../../atl/codesnippet/cpp/com-map-macros_10.h)]  
  
  
  
##  <a name="com_interface_entry_func"></a>COM_INTERFACE_ENTRY_FUNC  
 Um mecanismo geral para a conexão do ATL `QueryInterface` lógica.  
  
```
COM_INTERFACE_ENTRY_FUNC(iid, dw, func)
```   
  
### <a name="parameters"></a>Parâmetros  
 `iid`  
 [in] O GUID da interface exposto.  
  
 `dw`  
 [in] Um parâmetro passado para o `func`.  
  
 `func`  
 [in] O ponteiro de função que retornará `iid`.  
  
### <a name="remarks"></a>Comentários  
 Se *iid* corresponde o IID da interface consultado para, em seguida, a função especificada por `func` é chamado. A declaração da função deve ser:  
  
 `HRESULT WINAPI func(void* pv, REFIID riid, LPVOID* ppv, DWORD_PTR dw);`  
  
 Quando a função é chamada, `pv` aponta para o objeto de classe. O `riid` parâmetro refere-se a interface que está sendo consultada, `ppv` é o ponteiro para o local onde a função deve armazenar o ponteiro para a interface, e `dw` é o parâmetro especificado na entrada. A função deve definir \* `ppv` para **nulo** e retornar **E_NOINTERFACE** ou **S_FALSE** se ele optar por não retornar uma interface. Com **E_NOINTERFACE**, COM processamento de mapa é encerrado. Com **S_FALSE**, processamento de mapa COM continua, mesmo que nenhum ponteiro de interface foi retornado. Se a função retorna um ponteiro de interface, ele deverá retornar `S_OK`.  
  
  
  
##  <a name="com_interface_entry_func_blind"></a>COM_INTERFACE_ENTRY_FUNC_BLIND  
 Mesmo que [COM_INTERFACE_ENTRY_FUNC](#com_interface_entry_func), exceto que consultar qualquer IID resulta em uma chamada para `func`.  
  
```
COM_INTERFACE_ENTRY_FUNC_BLIND(dw, func)
```  
  
### <a name="parameters"></a>Parâmetros  
 `dw`  
 [in] Um parâmetro passado para o `func`.  
  
 `func`  
 [in] A função que é chamada quando esta entrada no mapa COM é processada.  
  
### <a name="remarks"></a>Comentários  
 Qualquer falha fará com que o processamento continue no mapa de COM. Se a função retorna um ponteiro de interface, ele deverá retornar `S_OK`.  
  
  
##  <a name="com_interface_entry_nointerface"></a>COM_INTERFACE_ENTRY_NOINTERFACE  
 Retorna **E_NOINTERFACE** e termina COM o mapa processamento quando a interface especificada é consultada para.  
  
```
COM_INTERFACE_ENTRY_NOINTERFACE(x)
```  
  
### <a name="parameters"></a>Parâmetros  
 *x*  
 [in] Texto usado para construir o identificador de interface.  
  
### <a name="remarks"></a>Comentários  
 Você pode usar essa macro para impedir que uma interface que está sendo usado em um caso específico. Por exemplo, você pode inserir esta macro seu COM logo antes de mapear `COM_INTERFACE_ENTRY_AGGREGATE_BLIND` para impedir que uma consulta para a interface de encaminhamento para desconhecido interna da agregação.  
  
 A interface IID será construído acrescentando *x* para `IID_`. Por exemplo, se *x* é `IPersistStorage`, será o IID `IID_IPersistStorage`.  
  
  