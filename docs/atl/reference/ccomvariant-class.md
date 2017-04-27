---
title: Classe CComVariant | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComVariant
- ATLCOMCLI/ATL::CComVariant
- ATLCOMCLI/ATL::CComVariant::CComVariant
- ATLCOMCLI/ATL::CComVariant::Attach
- ATLCOMCLI/ATL::CComVariant::ChangeType
- ATLCOMCLI/ATL::CComVariant::Clear
- ATLCOMCLI/ATL::CComVariant::Copy
- ATLCOMCLI/ATL::CComVariant::CopyTo
- ATLCOMCLI/ATL::CComVariant::Detach
- ATLCOMCLI/ATL::CComVariant::GetSize
- ATLCOMCLI/ATL::CComVariant::ReadFromStream
- ATLCOMCLI/ATL::CComVariant::SetByRef
- ATLCOMCLI/ATL::CComVariant::WriteToStream
dev_langs:
- C++
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
caps.latest.revision: 26
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 4b01ca9da3d216603ea7efad228735edd1becbd3
ms.lasthandoff: 02/25/2017

---
# <a name="ccomvariant-class"></a>Classe CComVariant
Essa classe encapsula a `VARIANT` tipo, fornecendo um membro que indica o tipo de dados armazenados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
cpp
class CComVariant : public tagVARIANT  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CComVariant::CComVariant](#ccomvariant)|O construtor.|  
|[CComVariant:: ~ CComVariant](#dtor)|O destruidor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CComVariant::Attach](#attach)|Anexa uma **VARIANT** para o `CComVariant` objeto.|  
|[CComVariant::ChangeType](#changetype)|Converte o `CComVariant` um novo tipo de objeto.|  
|[CComVariant::Clear](#clear)|Limpa o `CComVariant` objeto.|  
|[CComVariant::Copy](#copy)|Copia uma **VARIANT** para o `CComVariant` objeto.|  
|[CComVariant::CopyTo](#copyto)|Copia o conteúdo da `CComVariant` objeto.|  
|[CComVariant::Detach](#detach)|Desanexa subjacente **VARIANT** do `CComVariant` objeto.|  
|[CComVariant::GetSize](#getsize)|Retorna o tamanho em número de bytes do conteúdo do `CComVariant` objeto.|  
|[CComVariant::ReadFromStream](#readfromstream)|Carrega um **VARIANT** de um fluxo.|  
|[CComVariant::SetByRef](#setbyref)|Inicializa o `CComVariant` objeto e define o **vt** membro **VT_BYREF**.|  
|[CComVariant::WriteToStream](#writetostream)|Salva subjacente **VARIANT** em um fluxo.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|||  
|-|-|  
|[CComVariant::operator](#operator_lt)|Indica se o `CComVariant` objeto é menor que o especificado **VARIANT**.|  
|[CComVariant::operator >](#operator_gt)|Indica se o `CComVariant` objeto é maior que o especificado **VARIANT**.|  
|[operador! =](#operator_neq)|Indica se o `CComVariant` objeto não é igual a especificado **VARIANT**.|  
|[operador =](#operator_eq)|Atribui um valor para o `CComVariant` objeto.|  
|[operador = =](#operator_eq_eq)|Indica se o `CComVariant` objeto é igual a especificado **VARIANT**.|  
  
## <a name="remarks"></a>Comentários  
 `CComVariant`encapsula o `VARIANT and VARIANTARG` tipo, que consiste em uma união e um membro que indica o tipo dos dados armazenados na União. **VARIANT**s normalmente são usados na automação.  
  
 `CComVariant`deriva de **VARIANT** tipo pode ser usado onde quer que um **VARIANT** pode ser usado. Por exemplo, você pode usar o **V_VT** macro para extrair o tipo de um `CComVariant` ou você pode acessar o **vt** membro diretamente exatamente como faria com um **VARIANT**.  
  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 `tagVARIANT`  
  
 `CComVariant`  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** atlcomcli. h  
  
##  <a name="attach"></a>CComVariant::Attach  
 Apaga com segurança o conteúdo atual do `CComVariant` de objeto, copia o conteúdo de `pSrc` para esse objeto, em seguida, define o tipo de variante de `pSrc` para `VT_EMPTY`.  
  
```
HRESULT Attach(VARIANT* pSrc);
```  
  
### <a name="parameters"></a>Parâmetros  
 `pSrc`  
 [in] Aponta para a [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) a ser anexado ao objeto.  
  
### <a name="return-value"></a>Valor de retorno  
 Um padrão `HRESULT` valor.  
  
### <a name="remarks"></a>Comentários  
 Propriedade dos dados mantidos por `pSrc` é transferido para o `CComVariant` objeto.  
  
##  <a name="ccomvariant"></a>CComVariant::CComVariant  
 Cada construtor trata a inicialização segura do `CComVariant` objeto chamando o `VariantInit` função do Win32 ou definindo o valor do objeto e o tipo de acordo com os parâmetros passados.  
  
```
CComVariant() throw();
CComVariant(const CComVariant& varSrc);
CComVariant(const VARIANT& varSrc);
CComVariant(LPCOLESTR lpszSrc);
CComVariant(LPCSTR lpszSrc);
CComVariant(bool bSrc);
CComVariant(BYTE nSrc) throw();
CComVariant(int nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned int  nSrc, VARTYPE vtSrc = VT_UI4) throw();
CComVariant(shor  nSrc) throw();
CComVariant(unsigned short nSrc) throw();
CComVariant(long  nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned long  nSrc) throw();
CComVariant(LONGLONG  nSrc) throw();
CComVariant(ULONGLONG  nSrc) throw();
CComVariant(float  fltSrc) throw();
CComVariant(double  dblSrc, VARTYPE vtSrc = VT_R8) throw();
CComVariant(CY  cySrc) throw();
CComVariant(IDispatch* pSrc) throw();
CComVariant(IUnknown* pSrc) throw();
CComVariant(const SAFEARRAY* pSrc);
CComVariant(char  cSrc) throw();
CComVariant(const CComBSTR& bstrSrc);
```  
  
### <a name="parameters"></a>Parâmetros  
 *varSrc*  
 [in] O `CComVariant` ou `VARIANT` usado para inicializar o `CComVariant` objeto. O conteúdo da variante de origem é copiado para o destino, sem conversão.  
  
 `lpszSrc`  
 [in] A cadeia de caracteres usada para inicializar o `CComVariant` objeto. Você pode passar uma terminada em zero ampla (Unicode) cadeia de caracteres para o **LPCOLESTR** versão do construtor ou uma cadeia de caracteres ANSI para o `LPCSTR` versão. Em ambos os casos, a cadeia de caracteres é convertida em Unicode `BSTR` alocados com **SysAllocString**. O tipo do `CComVariant` objeto será `VT_BSTR`.  
  
 `bSrc`  
 [in] O `bool` usado para inicializar o `CComVariant` objeto. O `bool` argumento é convertido em uma **VARIANT_BOOL** antes de serem armazenados. O tipo do `CComVariant` objeto será `VT_BOOL`.  
  
 `nSrc`  
 [in] O `int`, **bytes**, **curto**, **longo**, **LONGLONG**, **ULONGLONG**, **curto sem sinal**, `unsigned long`, ou `unsigned int` usado para inicializar o `CComVariant` objeto. The type of the `CComVariant` object will be `VT_I4`, `VT_UI1`, `VT_I2`, `VT_I4`, **VT_I8**, **VT_UI8**, **VT_UI2**, **VT_UI4**, or **VT_UI4**, respectively.  
  
 `vtSrc`  
 [in] O tipo de variante. Quando o primeiro parâmetro é `int`, os tipos válidos são `VT_I4` e **VT_INT**. Quando o primeiro parâmetro é **longo**, os tipos válidos são `VT_I4` e `VT_ERROR`. Quando o primeiro parâmetro é **duplo**, os tipos válidos são `VT_R8` e `VT_DATE`. Quando o primeiro parâmetro é `unsigned int`, os tipos válidos são **VT_UI4** e **VT_UINT**.  
  
 `fltSrc`  
 [in] O **float** usado para inicializar o `CComVariant` objeto. O tipo do `CComVariant` objeto será `VT_R4`.  
  
 `dblSrc`  
 [in] O **duplo** usado para inicializar o `CComVariant` objeto. O tipo do `CComVariant` objeto será `VT_R8`.  
  
 `cySrc`  
 [in] O **CY** usado para inicializar o `CComVariant` objeto. O tipo do `CComVariant` objeto será `VT_CY`.  
  
 `pSrc`  
 [in] O `IDispatch` ou **IUnknown** ponteiro usado para inicializar o `CComVariant` objeto. `AddRef`será chamado no ponteiro de interface. O tipo do `CComVariant` objeto será **VT_DISPATCH** ou **VT_UNKNOWN**, respectivamente.  
  
 Ou, o **SAFERRAY** ponteiro usado para inicializar o `CComVariant` objeto. Uma cópia do **SAFEARRAY** é armazenado na `CComVariant` objeto. O tipo do `CComVariant` objeto será uma combinação do tipo original a **SAFEARRAY** e **VT_ARRAY**.  
  
 `cSrc`  
 [in] O `char` usado para inicializar o `CComVariant` objeto. O tipo do `CComVariant` objeto será **VT_I1**.  
  
 `bstrSrc`  
 [in] O BSTR usado para inicializar o `CComVariant` objeto. O tipo do `CComVariant` objeto será `VT_BSTR`.  
  
### <a name="remarks"></a>Comentários  
 O destruidor gerencia limpeza chamando [CComVariant::Clear](#clear).  
  
##  <a name="dtor"></a>CComVariant:: ~ CComVariant  
 O destruidor.  
  
```
~CComVariant() throw();
```  
  
### <a name="remarks"></a>Comentários  
 Este método gerencia limpeza chamando [CComVariant::Clear](#clear).  
  
##  <a name="changetype"></a>CComVariant::ChangeType  
 Converte o `CComVariant` um novo tipo de objeto.  
  
```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```  
  
### <a name="parameters"></a>Parâmetros  
 `vtNew`  
 [in] O novo tipo para o `CComVariant` objeto.  
  
 `pSrc`  
 [in] Um ponteiro para o `VARIANT` cujo valor será convertido para o novo tipo. O valor padrão é **nulo**, ou seja, o `CComVariant` objeto será convertido em vigor.  
  
### <a name="return-value"></a>Valor de retorno  
 Um padrão `HRESULT` valor.  
  
### <a name="remarks"></a>Comentários  
 Se você passar um valor `pSrc`, `ChangeType` usará **VARIANT** como a origem para a conversão. Caso contrário, o `CComVariant` objeto será a origem.  
  
##  <a name="clear"></a>CComVariant::Clear  
 Limpa o `CComVariant` objeto chamando o `VariantClear` função do Win32.  
  
```
HRESULT Clear();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Um padrão `HRESULT` valor.  
  
### <a name="remarks"></a>Comentários  
 O destruidor automaticamente chama **limpar**.  
  
##  <a name="copy"></a>CComVariant::Copy  
 Libera o `CComVariant` de objeto e, em seguida, atribui uma cópia especificada **VARIANT**.  
  
```
HRESULT Copy(const VARIANT* pSrc);
```  
  
### <a name="parameters"></a>Parâmetros  
 `pSrc`  
 [in] Um ponteiro para o [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) a ser copiado.  
  
### <a name="return-value"></a>Valor de retorno  
 Um padrão `HRESULT` valor.  
  
##  <a name="copyto"></a>CComVariant::CopyTo  
 Copia o conteúdo da `CComVariant` objeto.  
  
```
HRESULT CopyTo(BSTR* pstrDest);
```  
  
### <a name="parameters"></a>Parâmetros  
 *pstrDest*  
 Aponta para um `BSTR` que receberão uma cópia do conteúdo do `CComVariant` objeto.  
  
### <a name="return-value"></a>Valor de retorno  
 Um padrão `HRESULT` valor.  
  
### <a name="remarks"></a>Comentários  
 O **CComVariant** objeto deve ser do tipo `VT_BSTR`.  
  
##  <a name="detach"></a>CComVariant::Detach  
 Desanexa subjacente **VARIANT** do `CComVariant` do objeto e define o tipo de objeto para `VT_EMPTY`.  
  
```
HRESULT Detach(VARIANT* pDest);
```  
  
### <a name="parameters"></a>Parâmetros  
 `pDest`  
 [out] Retorna subjacente `VARIANT` valor do objeto.  
  
### <a name="return-value"></a>Valor de retorno  
 Um padrão `HRESULT` valor.  
  
### <a name="remarks"></a>Comentários  
 Observe que o conteúdo da `VARIANT` referenciado pelo `pDest` serão apagadas automaticamente antes de ser atribuído o valor e o tipo de chamada **CComVariant** objeto.  
  
##  <a name="getsize"></a>CComVariant::GetSize  
 Tamanho fixo simples `VARIANT`s, esse método retorna o `sizeof` o tipo de dados mais `sizeof(VARTYPE)`.  
  
```
ULONG GetSize() const;
```  
  
### <a name="return-value"></a>Valor de retorno  
 O tamanho em bytes do conteúdo atual do `CComVariant` objeto.  
  
### <a name="remarks"></a>Comentários  
 Se o `VARIANT` contém um ponteiro de interface `GetSize` consulta `IPersistStream` ou `IPersistStreamInit`. Se for bem-sucedido, o valor de retorno é de 32 bits de ordem baixa do valor retornado por `GetSizeMax` mais o `sizeof` um `CLSID` e `sizeof(VARTYPE)`. Se o ponteiro de interface `NULL`, `GetSize` retorna o `sizeof` um `CLSID` mais `sizeof(VARTYPE)`. Se o tamanho total é maior do que `ULONG_MAX`, `GetSize` retorna `sizeof(VARTYPE)` que indica um erro.  
  
 Em todos os outros casos, um temporário `VARIANT` do tipo `VT_BSTR` é forçado atuais `VARIANT`. O tamanho deste `BSTR` é calculado como o tamanho do comprimento da cadeia de caracteres mais o comprimento da cadeia de caracteres em si mais o tamanho do caractere nulo mais `sizeof(VARTYPE)`. Se o `VARIANT` não podem ser forçados para um `VARIANT` do tipo `VT_BSTR`, `GetSize` retorna `sizeof(VARTYPE)`.  
  
 O tamanho retornado por esse método corresponde ao número de bytes usado por [CComVariant::WriteToStream](#writetostream) sob condições bem-sucedida.  
  
##  <a name="operator_eq"></a>CComVariant::operator =  
 Atribui um valor e um tipo correspondente para o `CComVariant` objeto.  
  
```
CComVariant& operator=(const CComVariant& varSrc);
CComVariant& operator=(const VARIANT& varSrc);
CComVariant& operator=(const CComBSTR& bstrSrc);
CComVariant& operator=(LPCOLESTR lpszSrc);
CComVariant& operator=(LPCSTR lpszSrc);
CComVariant& operator=(bool bSrc);
CComVariant& operator=(BYTE nSrc) throw();
CComVariant& operator=int nSrc) throw();
CComVariant& operator=(unsigned int nSrc) throw();
CComVariant& operator=(short nSrc) throw();
CComVariant& operator=(unsigned short nSrc) throw();
CComVariant& operator=(long nSrc) throw();
CComVariant& operator=(unsigned long nSrc) throw();
CComVariant& operator=(LONGLONG nSrc) throw();
CComVariant& operator=(ULONGLONG nSrc) throw();
CComVariant& operator=(float fltSrc) throw();
CComVariant& operator=(double dblSrc) throw();
CComVariant& operator=(CY cySrc) throw();
CComVariant& operator=(IDispatch* pSrc) throw();
CComVariant& operator=(IUnknown* pSrc) throw();
CComVariant& operator=(const SAFEARRAY* pSrc);
CComVariant& operator=(char cSrc) throw();
```  
  
### <a name="parameters"></a>Parâmetros  
 *varSrc*  
 [in] O `CComVariant` ou [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) a ser atribuído para a `CComVariant` objeto. O conteúdo da variante de origem é copiado para o destino, sem conversão.  
  
 `bstrSrc`  
 [in] O BSTR a ser atribuído ao `CComVariant` objeto. O tipo do `CComVariant` objeto será `VT_BSTR`.  
  
 `lpszSrc`  
 [in] A cadeia de caracteres a ser atribuído para a `CComVariant` objeto. Você pode passar uma terminada em zero ampla (Unicode) cadeia de caracteres para o **LPCOLESTR** versão do operador ou uma cadeia de caracteres ANSI para o `LPCSTR` versão. Em ambos os casos, a cadeia de caracteres é convertida em Unicode `BSTR` alocados com **SysAllocString**. O tipo do `CComVariant` objeto será `VT_BSTR`.  
  
 `bSrc`  
 [in] O `bool` a ser atribuído para a `CComVariant` objeto. O `bool` argumento é convertido em uma **VARIANT_BOOL** antes de serem armazenados. O tipo do `CComVariant` objeto será `VT_BOOL`.  
  
 `nSrc`  
 [in] The `int`, **BYTE**, **short**, **long**, **LONGLONG**, **ULONGLONG**, **unsigned short**, `unsigned long`, or `unsigned int` to be assigned to the `CComVariant` object. The type of the `CComVariant` object will be `VT_I4`, `VT_UI1`, `VT_I2`, `VT_I4`, **VT_I8**, **VT_UI8**, **VT_UI2**, **VT_UI4**, or **VT_UI4**, respectively.  
  
 `fltSrc`  
 [in] O **float** a ser atribuído para a `CComVariant` objeto. O tipo do `CComVariant` objeto será `VT_R4`.  
  
 `dblSrc`  
 [in] O **duplo** a ser atribuído ao `CComVariant` objeto. O tipo do `CComVariant` objeto será `VT_R8`.  
  
 `cySrc`  
 [in] O **CY** a ser atribuído para a `CComVariant` objeto. O tipo do `CComVariant` objeto será `VT_CY`.  
  
 `pSrc`  
 [in] O `IDispatch` ou **IUnknown** ponteiro a ser atribuído para a `CComVariant` objeto. `AddRef`será chamado no ponteiro de interface. O tipo do `CComVariant` objeto será **VT_DISPATCH** ou **VT_UNKNOWN**, respectivamente.  
  
 Ou, um **SAFEARRAY** ponteiro a ser atribuído para a `CComVariant` objeto. Uma cópia do **SAFEARRAY** é armazenado na `CComVariant` objeto. O tipo do `CComVariant` objeto será uma combinação do tipo original a **SAFEARRAY** e **VT_ARRAY**.  
  
 `cSrc`  
 [in] O caractere a ser atribuído ao `CComVariant` objeto. O tipo do `CComVariant` objeto será **VT_I1**.  
  
##  <a name="operator_eq_eq"></a>CComVariant::operator = =  
 Indica se o `CComVariant` objeto é igual a especificado **VARIANT**.  
  
```
bool operator==(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Comentários  
 Retorna **true** se o valor e o tipo de *varSrc* são iguais ao valor e tipo, respectivamente, do `CComVariant` objeto. Caso contrário, **false**. O operador usa a localidade padrão do usuário para executar a comparação.  
  
 O operador compara somente o valor dos tipos variantes. Ele compara cadeias de caracteres, inteiros e pontos flutuantes, mas não matrizes ou registros.  
  
##  <a name="operator_neq"></a>CComVariant::operator! =  
 Indica se o `CComVariant` objeto não é igual a especificado **VARIANT**.  
  
```
bool operator!=(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Comentários  
 Retorna **true** se o valor ou o tipo de *varSrc* não é igual ao valor ou tipo, respectivamente, do `CComVariant` objeto. Caso contrário, **false**. O operador usa a localidade padrão do usuário para executar a comparação.  
  
 O operador compara somente o valor dos tipos variantes. Ele compara cadeias de caracteres, inteiros e pontos flutuantes, mas não matrizes ou registros.  
  
##  <a name="operator_lt"></a>CComVariant::operator&lt;  
 Indica se o `CComVariant` objeto é menor que o especificado **VARIANT**.  
  
```
bool operator<(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Comentários  
 Retorna **true** se o valor de `CComVariant` objeto é menor que o valor de *varSrc*. Caso contrário, **false**. O operador usa a localidade padrão do usuário para executar a comparação.  
  
##  <a name="operator_gt"></a>CComVariant::operator&gt;  
 Indica se o `CComVariant` objeto é maior que o especificado **VARIANT**.  
  
```
bool operator>(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Comentários  
 Retorna **true** se o valor de `CComVariant` objeto é maior que o valor de *varSrc*. Caso contrário, **false**. O operador usa a localidade padrão do usuário para executar a comparação.  
  
##  <a name="readfromstream"></a>CComVariant::ReadFromStream  
 Define a base **VARIANT** para o **VARIANT** contidos em um fluxo especificado.  
  
```
HRESULT ReadFromStream(IStream* pStream);
```  
  
### <a name="parameters"></a>Parâmetros  
 `pStream`  
 [in] Um ponteiro para o [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) interface no fluxo que contém os dados.  
  
### <a name="return-value"></a>Valor de retorno  
 Um padrão `HRESULT` valor.  
  
### <a name="remarks"></a>Comentários  
 **ReadToStream** requer uma chamada anterior a [WriteToStream](#writetostream).  
  
##  <a name="setbyref"></a>CComVariant::SetByRef  
 Inicializa o `CComVariant` objeto e define o **vt** membro **VT_BYREF**.  
  
```
template < typename T >
void SetByRef(T* pT) throw();
```  
  
### <a name="parameters"></a>Parâmetros  
 `T`  
 O tipo de **VARIANT**, por exemplo, `BSTR`, `int`, ou `char`.  
  
 *pT*  
 O ponteiro usado para inicializar o `CComVariant` objeto.  
  
### <a name="remarks"></a>Comentários  
 `SetByRef`é um modelo de função que inicializa o `CComVariant` objeto ao ponteiro *pT* e define o **vt** membro **VT_BYREF**. Por exemplo:  
  
 [!code-cpp[NVC_ATL_Utilities&#76;](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]  
  
##  <a name="writetostream"></a>CComVariant::WriteToStream  
 Salva subjacente **VARIANT** em um fluxo.  
  
```
HRESULT WriteToStream(IStream* pStream);
```  
  
### <a name="parameters"></a>Parâmetros  
 `pStream`  
 [in] Um ponteiro para o [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) interface em um fluxo.  
  
### <a name="return-value"></a>Valor de retorno  
 Um padrão `HRESULT` valor.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da classe](../../atl/atl-class-overview.md)