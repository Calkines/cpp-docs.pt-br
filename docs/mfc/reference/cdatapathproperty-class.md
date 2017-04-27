---
title: Classe CDataPathProperty | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataPathProperty
- AFXCTL/CDataPathProperty
- AFXCTL/CDataPathProperty::CDataPathProperty
- AFXCTL/CDataPathProperty::GetControl
- AFXCTL/CDataPathProperty::GetPath
- AFXCTL/CDataPathProperty::Open
- AFXCTL/CDataPathProperty::ResetData
- AFXCTL/CDataPathProperty::SetControl
- AFXCTL/CDataPathProperty::SetPath
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], asynchronous
- OLE controls [C++], asynchronous
- CDataPathProperty class
- asynchronous controls [C++]
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
caps.latest.revision: 24
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
ms.openlocfilehash: d767cf950d8b86959aadc2fd4d77401134a6dc75
ms.lasthandoff: 02/25/2017

---
# <a name="cdatapathproperty-class"></a>Classe CDataPathProperty
Implementa uma OLE controla a propriedade que pode ser carregada de forma assíncrona.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class CDataPathProperty : public CAsyncMonikerFile  
```  
  
## <a name="members"></a>Membros  
  
### <a name="public-constructors"></a>Construtores públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|Constrói um objeto `CDataPathProperty`.|  
  
### <a name="public-methods"></a>Métodos Públicos  
  
|Nome|Descrição|  
|----------|-----------------|  
|[CDataPathProperty::GetControl](#getcontrol)|Recupera o controle OLE assíncrono associado a `CDataPathProperty` objeto.|  
|[CDataPathProperty::GetPath](#getpath)|Recupera o nome do caminho da propriedade.|  
|[CDataPathProperty::Open](#open)|Inicia o carregamento da propriedade assíncrona para o controle ActiveX (OLE) associado.|  
|[CDataPathProperty::ResetData](#resetdata)|Chamadas `CAsyncMonikerFile::OnDataAvailable` para notificar o contêiner que alterou as propriedades do controle.|  
|[CDataPathProperty::SetControl](#setcontrol)|Define o controle ActiveX (OLE) assíncrona associado à propriedade.|  
|[CDataPathProperty::SetPath](#setpath)|Define o nome do caminho da propriedade.|  
  
## <a name="remarks"></a>Comentários  
 Propriedades assíncronas são carregadas após a inicialização síncrona.  
  
 A classe `CDataPathProperty` é derivado de **CAysncMonikerFile**. Para implementar propriedades assíncronas em seus controles OLE, derive uma classe de `CDataPathProperty`e substituir [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable).  
  
 Para obter mais informações sobre como usar controles ActiveX e monikers assíncronos em aplicativos da Internet, consulte os seguintes artigos:  
  
- [Internet primeiras etapas: Controles ActiveX](../../mfc/activex-controls-on-the-internet.md)  
  
- [Internet primeiras etapas: Monikers assíncronos](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarquia de herança  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 `CDataPathProperty`  
  
## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** afxctl.h  
  
##  <a name="cdatapathproperty"></a>CDataPathProperty::CDataPathProperty  
 Constrói um objeto `CDataPathProperty`.  
  
```  
CDataPathProperty(COleControl* pControl = NULL);  
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>Parâmetros  
 `pControl`  
 Um ponteiro para o objeto de controle OLE a ser associada a essa `CDataPathProperty` objeto.  
  
 `lpszPath`  
 O caminho, que pode ser absoluta ou relativa, usado para criar um moniker assíncrona que faz referência a localização absoluta real da propriedade. `CDataPathProperty`usa URLs, não os nomes de arquivo. Se você quiser uma `CDataPathProperty` de objeto para um arquivo, preceda `file://` no caminho.  
  
### <a name="remarks"></a>Comentários  
 O `COleControl` objeto apontado por `pControl` é usado pelo **abrir** e recuperada por classes derivadas. Se `pControl` é **nulo**, o controle usado com **abrir** deve ser definida com `SetControl`. Se `lpszPath` é **nulo**, você pode passar no caminho por meio de **abrir** ou defini-lo com `SetPath`.  
  
##  <a name="getcontrol"></a>CDataPathProperty::GetControl  
 Chame essa função de membro para recuperar o `COleControl` objeto associado a `CDataPathProperty` objeto.  
  
```  
COleControl* GetControl();
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna um ponteiro para o controle OLE associado a `CDataPathProperty` objeto. **NULO** se o controle não está associado.  
  
##  <a name="getpath"></a>CDataPathProperty::GetPath  
 Chame essa função de membro para recuperar o caminho, defina quando o `CDataPathProperty` objeto foi criado ou especificado no **abrir**, ou especificada em uma chamada anterior para o `SetPath` função de membro.  
  
```  
CString GetPath() const;  
```  
  
### <a name="return-value"></a>Valor de retorno  
 Retorna o nome do caminho para a propriedade em si. Pode ser vazio se nenhum caminho foi especificado.  
  
##  <a name="open"></a>CDataPathProperty::Open  
 Chame essa função de membro para iniciar o carregamento da propriedade assíncrona para o controle associado.  
  
```  
virtual BOOL Open(
    COleControl* pControl,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszPath,  
    COleControl* pControl,
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszPath,  
    CFileException* pError = NULL);  
  
virtual BOOL Open(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parâmetros  
 `pControl`  
 Um ponteiro para o objeto de controle OLE a ser associada a essa `CDataPathProperty` objeto.  
  
 `pError`  
 Um ponteiro para uma exceção de arquivo. Se ocorrer um erro, será definido como a causa.  
  
 `lpszPath`  
 O caminho, que pode ser absoluta ou relativa, usado para criar um moniker assíncrona que faz referência a localização absoluta real da propriedade. `CDataPathProperty`usa URLs, não os nomes de arquivo. Se você quiser uma `CDataPathProperty` de objeto para um arquivo, preceda `file://` no caminho.  
  
### <a name="return-value"></a>Valor de retorno  
 Diferente de zero se for bem-sucedida; Caso contrário, 0.  
  
### <a name="remarks"></a>Comentários  
 A função tenta obter o `IBindHost` interface do controle.  
  
 Antes de chamar **abrir** sem um caminho, o valor do caminho da propriedade deve ser definido. Isso pode ser feito quando o objeto é construído, ou chamando o `SetPath` função de membro.  
  
 Antes de chamar **abrir** sem um controle, um controle ActiveX (anteriormente conhecido como um controle OLE) pode ser associado ao objeto. Isso pode ser feito quando o objeto é construído, ou chamando `SetControl`.  
  
 Todas as sobrecargas de [CAsyncMonikerFile::Open](../../mfc/reference/casyncmonikerfile-class.md#open) também estão disponíveis em `CDataPathProperty`.  
  
##  <a name="resetdata"></a>CDataPathProperty::ResetData  
 Chame essa função para obter `CAsyncMonikerFile::OnDataAvailable` para notificar o contêiner que as propriedades de controle foram alterados e todas as informações carregadas de forma assíncrona não são mais útil.  
  
```  
virtual void ResetData();
```  
  
### <a name="remarks"></a>Comentários  
 Abertura deve ser reiniciada. Classes derivadas podem substituir essa função para diferentes padrões.  
  
##  <a name="setcontrol"></a>CDataPathProperty::SetControl  
 Chame essa função de membro para associar um controle OLE assíncrono com o `CDataPathProperty` objeto.  
  
```  
void SetControl(COleControl* pControl);
```  
  
### <a name="parameters"></a>Parâmetros  
 `pControl`  
 Um ponteiro para o controle OLE assíncrono a ser associado com a propriedade.  
  
##  <a name="setpath"></a>CDataPathProperty::SetPath  
 Chame essa função de membro para definir o nome do caminho da propriedade.  
  
```  
void SetPath(LPCTSTR lpszPath);
```  
  
### <a name="parameters"></a>Parâmetros  
 `lpszPath`  
 Um caminho, que pode ser absoluto ou relativo para a propriedade que está sendo carregada de forma assíncrona. `CDataPathProperty`usa URLs, não os nomes de arquivo. Se você quiser uma `CDataPathProperty` de objeto para um arquivo, preceda `file://` no caminho.  
  
## <a name="see-also"></a>Consulte também  
 [Imagem de exemplo do MFC](../../visual-cpp-samples.md)   
 [Classe CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)   
 [Gráfico de hierarquia](../../mfc/hierarchy-chart.md)   
 [Classe CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)
