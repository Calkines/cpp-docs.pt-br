---
title: Interface IAxWinAmbientDispatch
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatch
- ATLIFACE/ATL::IAxWinAmbientDispatch
- ATLIFACE/ATL::get_AllowContextMenu
- ATLIFACE/ATL::get_AllowShowUI
- ATLIFACE/ATL::get_AllowWindowlessActivation
- ATLIFACE/ATL::get_BackColor
- ATLIFACE/ATL::get_DisplayAsDefault
- ATLIFACE/ATL::get_DocHostDoubleClickFlags
- ATLIFACE/ATL::get_DocHostFlags
- ATLIFACE/ATL::get_Font
- ATLIFACE/ATL::get_ForeColor
- ATLIFACE/ATL::get_LocaleID
- ATLIFACE/ATL::get_MessageReflect
- ATLIFACE/ATL::get_OptionKeyPath
- ATLIFACE/ATL::get_ShowGrabHandles
- ATLIFACE/ATL::get_ShowHatching
- ATLIFACE/ATL::get_UserMode
- ATLIFACE/ATL::put_AllowContextMenu
- ATLIFACE/ATL::put_AllowShowUI
- ATLIFACE/ATL::put_AllowWindowlessActivation
- ATLIFACE/ATL::put_BackColor
- ATLIFACE/ATL::put_DisplayAsDefault
- ATLIFACE/ATL::put_DocHostDoubleClickFlags
- ATLIFACE/ATL::put_DocHostFlags
- ATLIFACE/ATL::put_Font
- ATLIFACE/ATL::put_ForeColor
- ATLIFACE/ATL::put_LocaleID
- ATLIFACE/ATL::put_MessageReflect
- ATLIFACE/ATL::put_OptionKeyPath
- ATLIFACE/ATL::put_UserMode
helpviewer_keywords:
- IAxWinAmbientDispatch interface
ms.assetid: 55ba6f7b-7a3c-4792-ae47-c8a84b683ca9
ms.openlocfilehash: 85a8f1d41c6c54f94b500807a1e4ca504206f56a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276153"
---
# <a name="iaxwinambientdispatch-interface"></a>Interface IAxWinAmbientDispatch

Essa interface fornece métodos para especificar as características do controle hospedado ou contêiner.

> [!IMPORTANT]
>  Essa classe e seus membros não podem ser usados em aplicativos executados no tempo de execução do Windows.

## <a name="syntax"></a>Sintaxe

```
interface IAxWinAmbientDispatch : IDispatch
```

## <a name="members"></a>Membros

### <a name="methods"></a>Métodos

|||
|-|-|
|[get_AllowContextMenu](#get_allowcontextmenu)|O `AllowContextMenu` propriedade especifica se o controle hospedado tem permissão para exibir seu próprio menu de contexto.|
|[get_AllowShowUI](#get_allowshowui)|O `AllowShowUI` propriedade especifica se o controle hospedado tem permissão para exibir sua própria interface do usuário.|
|[get_AllowWindowlessActivation](#get_allowwindowlessactivation)|O `AllowWindowlessActivation` propriedade especifica se o contêiner permite a ativação sem janelas.|
|[get_BackColor](#get_backcolor)|O `BackColor` propriedade especifica a cor da tela de fundo ambiente do contêiner.|
|[get_DisplayAsDefault](#get_displayasdefault)|`DisplayAsDefault` é uma propriedade de ambiente que permite que um controle para descobrir se ele é o padrão de controle.|
|[get_DocHostDoubleClickFlags](#get_dochostdoubleclickflags)|O `DocHostDoubleClickFlags` propriedade especifica a operação que deve ocorrer em resposta a um clique duplo.|
|[get_DocHostFlags](#get_dochostflags)|O `DocHostFlags` propriedade especifica os recursos de interface do usuário do objeto de host.|
|[get_Font](#get_font)|O `Font` propriedade especifica a fonte do ambiente do contêiner.|
|[get_ForeColor](#get_forecolor)|O `ForeColor` propriedade especifica a cor de primeiro plano de ambiente do contêiner.|
|[get_LocaleID](#get_localeid)|O `LocaleID` propriedade especifica a ID de localidade de ambiente do contêiner.|
|[get_MessageReflect](#get_messagereflect)|O `MessageReflect` propriedade de ambiente que especifica se o contêiner refletirá as mensagens para o controle hospedado.|
|[get_OptionKeyPath](#get_optionkeypath)|O `OptionKeyPath` propriedade especifica o caminho da chave do registro nas configurações de usuário.|
|[get_ShowGrabHandles](#get_showgrabhandles)|O `ShowGrabHandles` propriedade de ambiente permite que o controle descobrir se ele deve desenhar a próprio com as alças de captura.|
|[get_ShowHatching](#get_showhatching)|O `ShowHatching` propriedade de ambiente permite que o controle descobrir se ele deve ser desenhado em si hatched.|
|[get_UserMode](#get_usermode)|O `UserMode` propriedade especifica o modo de usuário do ambiente do contêiner.|
|[put_AllowContextMenu](#put_allowcontextmenu)|O `AllowContextMenu` propriedade especifica se o controle hospedado tem permissão para exibir seu próprio menu de contexto.|
|[put_AllowShowUI](#put_allowshowui)|O `AllowShowUI` propriedade especifica se o controle hospedado tem permissão para exibir sua própria interface do usuário.|
|[put_AllowWindowlessActivation](#put_allowwindowlessactivation)|O `AllowWindowlessActivation` propriedade especifica se o contêiner permite a ativação sem janelas.|
|[put_BackColor](#put_backcolor)|O `BackColor` propriedade especifica a cor da tela de fundo ambiente do contêiner.|
|[put_DisplayAsDefault](#put_displayasdefault)|`DisplayAsDefault` é uma propriedade de ambiente que permite que um controle para descobrir se ele é o padrão de controle.|
|[put_DocHostDoubleClickFlags](#put_dochostdoubleclickflags)|O `DocHostDoubleClickFlags` propriedade especifica a operação que deve ocorrer em resposta a um clique duplo.|
|[put_DocHostFlags](#put_dochostflags)|O `DocHostFlags` propriedade especifica os recursos de interface do usuário do objeto de host.|
|[put_Font](#put_font)|O `Font` propriedade especifica a fonte do ambiente do contêiner.|
|[put_ForeColor](#put_forecolor)|O `ForeColor` propriedade especifica a cor de primeiro plano de ambiente do contêiner.|
|[put_LocaleID](#put_localeid)|O `LocaleID` propriedade especifica a ID de localidade de ambiente do contêiner.|
|[put_MessageReflect](#put_messagereflect)|O `MessageReflect` propriedade de ambiente que especifica se o contêiner refletirá as mensagens para o controle hospedado.|
|[put_OptionKeyPath](#put_optionkeypath)|O `OptionKeyPath` propriedade especifica o caminho da chave do registro nas configurações de usuário.|
|[put_UserMode](#put_usermode)|O `UserMode` propriedade especifica o modo de usuário do ambiente do contêiner.|

## <a name="remarks"></a>Comentários

Essa interface é exposta pelo controle ActiveX do ATL que objetos de hospedagem. Chame os métodos nesta interface para definir as propriedades de ambiente disponíveis para o controle hospedado ou especificar outros aspectos do comportamento do contêiner. Para complementar as propriedades fornecidas por `IAxWinAmbientDispatch`, use [IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md).

<xref:System.Windows.Forms.AxHost> tentará carregar as informações de tipo sobre `IAxWinAmbientDispatch` e `IAxWinAmbientDispatchEx` de typelib que contém o código.

Se você está vinculando ATL90.dll, **AXHost** carregará as informações de tipo de typelib na DLL.

Ver [hospedagem de AXHost de ATL usando do ActiveX controles](../../atl/hosting-activex-controls-using-atl-axhost.md) para obter mais detalhes.

## <a name="requirements"></a>Requisitos

A definição desta interface está disponível em um número de formulários, conforme mostrado na tabela a seguir.

|Tipo de definição|Arquivo|
|---------------------|----------|
|IDL|atliface.idl|
|Biblioteca de tipos|ATL.dll|
|C++|atliface (também é incluído em atlbase. H)|

##  <a name="get_allowcontextmenu"></a>  IAxWinAmbientDispatch::get_AllowContextMenu

O `AllowContextMenu` propriedade especifica se o controle hospedado tem permissão para exibir seu próprio menu de contexto.

```
STDMETHOD(get_AllowContextMenu)(VARIANT_BOOL* pbAllowContextMenu);
```

### <a name="parameters"></a>Parâmetros

*pbAllowContextMenu*<br/>
[out] O endereço de uma variável para receber o valor atual dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa VARIANT_TRUE como o valor padrão dessa propriedade.

##  <a name="get_allowshowui"></a>  IAxWinAmbientDispatch::get_AllowShowUI

O `AllowShowUI` propriedade especifica se o controle hospedado tem permissão para exibir sua própria interface do usuário.

```
STDMETHOD(get_AllowShowUI)(VARIANT_BOOL* pbAllowShowUI);
```

### <a name="parameters"></a>Parâmetros

*pbAllowShowUI*<br/>
[out] O endereço de uma variável para receber o valor atual dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa VARIANT_FALSE como o valor padrão dessa propriedade.

##  <a name="get_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::get_AllowWindowlessActivation

O `AllowWindowlessActivation` propriedade especifica se o contêiner permite a ativação sem janelas.

```
STDMETHOD(get_AllowWindowlessActivation)(VARIANT_BOOL* pbAllowWindowless);
```

### <a name="parameters"></a>Parâmetros

*pbAllowWindowless*<br/>
[out] O endereço de uma variável para receber o valor atual dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa VARIANT_TRUE como o valor padrão dessa propriedade.

##  <a name="get_backcolor"></a>  IAxWinAmbientDispatch::get_BackColor

O `BackColor` propriedade especifica a cor da tela de fundo ambiente do contêiner.

```
STDMETHOD(get_BackColor)(OLE_COLOR* pclrBackground);
```

### <a name="parameters"></a>Parâmetros

*pclrBackground*<br/>
[out] O endereço de uma variável para receber o valor atual dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa COLOR_BTNFACE ou COLOR_WINDOW como o valor padrão dessa propriedade (dependendo se o pai da janela de host é uma caixa de diálogo ou não).

##  <a name="get_displayasdefault"></a>  IAxWinAmbientDispatch::get_DisplayAsDefault

`DisplayAsDefault` é uma propriedade de ambiente que permite que um controle para descobrir se ele é o padrão de controle.

```
STDMETHOD(get_DisplayAsDefault)(VARIANT_BOOL* pbDisplayAsDefault);
```

### <a name="parameters"></a>Parâmetros

*pbDisplayAsDefault*<br/>
[out] O endereço de uma variável para receber o valor atual dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa VARIANT_FALSE como o valor padrão dessa propriedade.

##  <a name="get_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::get_DocHostDoubleClickFlags

O `DocHostDoubleClickFlags` propriedade especifica a operação que deve ocorrer em resposta a um clique duplo.

```
STDMETHOD(get_DocHostDoubleClickFlags)(DWORD* pdwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parâmetros

*pdwDocHostDoubleClickFlags*<br/>
[out] O endereço de uma variável para receber o valor atual dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa DOCHOSTUIDBLCLK_DEFAULT como o valor padrão dessa propriedade.

##  <a name="get_dochostflags"></a>  IAxWinAmbientDispatch::get_DocHostFlags

O `DocHostFlags` propriedade especifica os recursos de interface do usuário do objeto de host.

```
STDMETHOD(get_DocHostFlags)(DWORD* pdwDocHostFlags);
```

### <a name="parameters"></a>Parâmetros

*pdwDocHostFlags*<br/>
[out] O endereço de uma variável para receber o valor atual dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa DOCHOSTUIFLAG_NO3DBORDER como o valor padrão dessa propriedade.

##  <a name="get_font"></a>  IAxWinAmbientDispatch::get_Font

O `Font` propriedade especifica a fonte do ambiente do contêiner.

```
STDMETHOD(get_Font)(IFontDisp** pFont);
```

### <a name="parameters"></a>Parâmetros

*pFont*<br/>
[out] O endereço de um `IFontDisp` ponteiro de interface usado para receber o valor atual dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto ATL host usa a fonte de GUI padrão ou a fonte do sistema como o valor padrão dessa propriedade.

##  <a name="get_forecolor"></a>  IAxWinAmbientDispatch::get_ForeColor

O `ForeColor` propriedade especifica a cor de primeiro plano de ambiente do contêiner.

```
STDMETHOD(get_ForeColor)(OLE_COLOR* pclrForeground);
```

### <a name="parameters"></a>Parâmetros

*pclrForeground*<br/>
[out] O endereço de uma variável para receber o valor atual dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto ATL host usa a cor de texto da janela de sistema como o valor padrão dessa propriedade.

##  <a name="get_localeid"></a>  IAxWinAmbientDispatch::get_LocaleID

O `LocaleID` propriedade especifica a ID de localidade de ambiente do contêiner.

```
STDMETHOD(get_LocaleID)(LCID* plcidLocaleID);
```

### <a name="parameters"></a>Parâmetros

*plcidLocaleID*<br/>
[out] O endereço de uma variável para receber o valor atual dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto ATL host usa a localidade do usuário padrão como o valor padrão dessa propriedade.

Com esse método, você pode descobrir o ambiente LocalID, ou seja, o LocaleID do programa de seu controle está sendo usado no. Quando você souber o LocaleID, você pode chamar o código para carregar legendas específica de localidade, texto da mensagem de erro, e assim por diante de um arquivo de recurso ou uma DLL satélite.

##  <a name="get_messagereflect"></a>  IAxWinAmbientDispatch::get_MessageReflect

O `MessageReflect` propriedade de ambiente que especifica se o contêiner refletirá as mensagens para o controle hospedado.

```
STDMETHOD(get_MessageReflect)(VARIANT_BOOL* pbMessageReflect);
```

### <a name="parameters"></a>Parâmetros

*pbMessageReflect*<br/>
[out] O endereço de uma variável para receber o valor atual dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa VARIANT_TRUE como o valor padrão dessa propriedade.

##  <a name="get_optionkeypath"></a>  IAxWinAmbientDispatch::get_OptionKeyPath

O `OptionKeyPath` propriedade especifica o caminho da chave do registro nas configurações de usuário.

```
STDMETHOD(get_OptionKeyPath)(BSTR* pbstrOptionKeyPath);
```

### <a name="parameters"></a>Parâmetros

*pbstrOptionKeyPath*<br/>
[out] O endereço de uma variável para receber o valor atual dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

##  <a name="get_showgrabhandles"></a>  IAxWinAmbientDispatch::get_ShowGrabHandles

O `ShowGrabHandles` propriedade de ambiente permite que o controle descobrir se ele deve desenhar a próprio com as alças de captura.

```
STDMETHOD(get_ShowGrabHandles)(VARIANT_BOOL* pbShowGrabHandles);
```

### <a name="parameters"></a>Parâmetros

*pbShowGrabHandles*<br/>
[out] O endereço de uma variável para receber o valor atual dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação de objeto de host do ATL sempre retorna VARIANT_FALSE como o valor dessa propriedade.

##  <a name="get_showhatching"></a>  IAxWinAmbientDispatch::get_ShowHatching

O `ShowHatching` propriedade de ambiente permite que o controle descobrir se ele deve ser desenhado em si hatched.

```
STDMETHOD(get_ShowHatching)(VARIANT_BOOL* pbShowHatching);
```

### <a name="parameters"></a>Parâmetros

*pbShowHatching*<br/>
[out] O endereço de uma variável para receber o valor atual dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação de objeto de host do ATL sempre retorna VARIANT_FALSE como o valor dessa propriedade.

##  <a name="get_usermode"></a>  IAxWinAmbientDispatch::get_UserMode

O `UserMode` propriedade especifica o modo de usuário do ambiente do contêiner.

```
STDMETHOD(get_UserMode)(VARIANT_BOOL* pbUserMode);
```

### <a name="parameters"></a>Parâmetros

*pbUserMode*<br/>
[out] O endereço de uma variável para receber o valor atual dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa VARIANT_TRUE como o valor padrão dessa propriedade.

##  <a name="put_allowcontextmenu"></a>  IAxWinAmbientDispatch::put_AllowContextMenu

O `AllowContextMenu` propriedade especifica se o controle hospedado tem permissão para exibir seu próprio menu de contexto.

```
STDMETHOD(put_AllowContextMenu)(VARIANT_BOOL bAllowContextMenu);
```

### <a name="parameters"></a>Parâmetros

*bAllowContextMenu*<br/>
[in] O novo valor dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa VARIANT_TRUE como o valor padrão dessa propriedade.

##  <a name="put_allowshowui"></a>  IAxWinAmbientDispatch::put_AllowShowUI

O `AllowShowUI` propriedade especifica se o controle hospedado tem permissão para exibir sua própria interface do usuário.

```
STDMETHOD(put_AllowShowUI)(VARIANT_BOOL bAllowShowUI);
```

### <a name="parameters"></a>Parâmetros

*bAllowShowUI*<br/>
[in] O novo valor dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa VARIANT_FALSE como o valor padrão dessa propriedade.

##  <a name="put_allowwindowlessactivation"></a>  IAxWinAmbientDispatch::put_AllowWindowlessActivation

O `AllowWindowlessActivation` propriedade especifica se o contêiner permite a ativação sem janelas.

```
STDMETHOD(put_AllowWindowlessActivation)(VARIANT_BOOL bAllowWindowless);
```

### <a name="parameters"></a>Parâmetros

*bAllowWindowless*<br/>
[in] O novo valor dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa VARIANT_TRUE como o valor padrão dessa propriedade.

##  <a name="put_backcolor"></a>  IAxWinAmbientDispatch::put_BackColor

O `BackColor` propriedade especifica a cor da tela de fundo ambiente do contêiner.

```
STDMETHOD(put_BackColor)(OLE_COLOR clrBackground);
```

### <a name="parameters"></a>Parâmetros

*clrBackground*<br/>
[in] O novo valor dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa COLOR_BTNFACE ou COLOR_WINDOW como o valor padrão dessa propriedade (dependendo se o pai da janela de host é uma caixa de diálogo ou não).

##  <a name="put_displayasdefault"></a>  IAxWinAmbientDispatch::put_DisplayAsDefault

`DisplayAsDefault` é uma propriedade de ambiente que permite que um controle para descobrir se ele é o padrão de controle.

```
STDMETHOD(put_DisplayAsDefault)(VARIANT_BOOL bDisplayAsDefault);
```

### <a name="parameters"></a>Parâmetros

*bDisplayAsDefault*<br/>
[in] O novo valor dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa VARIANT_FALSE como o valor padrão dessa propriedade.

##  <a name="put_dochostdoubleclickflags"></a>  IAxWinAmbientDispatch::put_DocHostDoubleClickFlags

O `DocHostDoubleClickFlags` propriedade especifica a operação que deve ocorrer em resposta a um clique duplo.

```
STDMETHOD(put_DocHostDoubleClickFlags)(DWORD dwDocHostDoubleClickFlags);
```

### <a name="parameters"></a>Parâmetros

*dwDocHostDoubleClickFlags*<br/>
[in] O novo valor dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa DOCHOSTUIDBLCLK_DEFAULT como o valor padrão dessa propriedade.

##  <a name="put_dochostflags"></a>  IAxWinAmbientDispatch::put_DocHostFlags

O `DocHostFlags` propriedade especifica os recursos de interface do usuário do objeto de host.

```
STDMETHOD(put_DocHostFlags)(DWORD dwDocHostFlags);
```

### <a name="parameters"></a>Parâmetros

*dwDocHostFlags*<br/>
[in] O novo valor dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa DOCHOSTUIFLAG_NO3DBORDER como o valor padrão dessa propriedade.

##  <a name="put_font"></a>  IAxWinAmbientDispatch::put_Font

O `Font` propriedade especifica a fonte do ambiente do contêiner.

```
STDMETHOD(put_Font)(IFontDisp* pFont);
```

### <a name="parameters"></a>Parâmetros

*pFont*<br/>
[in] O novo valor dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto ATL host usa a fonte de GUI padrão ou a fonte do sistema como o valor padrão dessa propriedade.

##  <a name="put_forecolor"></a>  IAxWinAmbientDispatch::put_ForeColor

O `ForeColor` propriedade especifica a cor de primeiro plano de ambiente do contêiner.

```
STDMETHOD(put_ForeColor)(OLE_COLOR clrForeground);
```

### <a name="parameters"></a>Parâmetros

*clrForeground*<br/>
[in] O novo valor dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto ATL host usa a cor de texto da janela de sistema como o valor padrão dessa propriedade.

##  <a name="put_localeid"></a>  IAxWinAmbientDispatch::put_LocaleID

O `LocaleID` propriedade especifica a ID de localidade de ambiente do contêiner.

```
STDMETHOD(put_LocaleID)(LCID lcidLocaleID);
```

### <a name="parameters"></a>Parâmetros

*lcidLocaleID*<br/>
[in] O novo valor dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto ATL host usa a localidade do usuário padrão como o valor padrão dessa propriedade.

##  <a name="put_messagereflect"></a>  IAxWinAmbientDispatch::put_MessageReflect

O `MessageReflect` propriedade de ambiente que especifica se o contêiner refletirá as mensagens para o controle hospedado.

```
STDMETHOD(put_MessageReflect)(VARIANT_BOOL bMessageReflect);
```

### <a name="parameters"></a>Parâmetros

*bMessageReflect*<br/>
[in] O novo valor dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa VARIANT_TRUE como o valor padrão dessa propriedade.

##  <a name="put_optionkeypath"></a>  IAxWinAmbientDispatch::put_OptionKeyPath

O `OptionKeyPath` propriedade especifica o caminho da chave do registro nas configurações de usuário.

```
STDMETHOD(put_OptionKeyPath)(BSTR bstrOptionKeyPath);
```

### <a name="parameters"></a>Parâmetros

*bstrOptionKeyPath*<br/>
[in] O novo valor dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

##  <a name="put_usermode"></a>  IAxWinAmbientDispatch::put_UserMode

O `UserMode` propriedade especifica o modo de usuário do ambiente do contêiner.

```
STDMETHOD(put_UserMode)(VARIANT_BOOL bUserMode);
```

### <a name="parameters"></a>Parâmetros

*bUserMode*<br/>
[in] O novo valor dessa propriedade.

### <a name="return-value"></a>Valor de retorno

Um valor padrão de HRESULT.

### <a name="remarks"></a>Comentários

A implementação do objeto de host ATL usa VARIANT_TRUE como o valor padrão dessa propriedade.

## <a name="see-also"></a>Consulte também

[Interface IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)<br/>
[Interface IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)<br/>
[CAxWindow::QueryHost](../../atl/reference/caxwindow-class.md#queryhost)<br/>
[AtlAxGetHost](composite-control-global-functions.md#atlaxgethost)
