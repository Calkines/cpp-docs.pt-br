---
title: Macros de mapa de propriedade | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
caps.latest.revision: 17
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: fbbed22766f9029456f15c4a554ae91322e6a275
ms.lasthandoff: 02/25/2017

---
# <a name="property-map-macros"></a>Macros de mapa de propriedade
Essas macros definem entradas e mapas de propriedade.  
  
|||  
|-|-|  
|[BEGIN_PROP_MAP](#begin_prop_map)|Marca o início do mapa de propriedade ATL.|  
|[PROP_DATA_ENTRY](#prop_data_entry)|Indica a extensão ou dimensões de um controle ActiveX.|  
|[PROP_ENTRY_TYPE](#prop_entry_type)|Insere uma descrição, a propriedade DISPID e a propriedade página de propriedades CLSID no mapa de propriedade.|  
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Inserir uma descrição de propriedade, a propriedade DISPID, página de propriedade CLSID, e `IDispatch` IID para o mapa de propriedade.|  
|[PROP_PAGE](#prop_page)|Insere uma página de propriedade CLSID no mapa de propriedade.|  
|[END_PROP_MAP](#end_prop_map)|Marca o fim do mapa de propriedade ATL.|  

## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** atlcom.h  
   
##  <a name="a-namebeginpropmapa--beginpropmap"></a><a name="begin_prop_map"></a>BEGIN_PROP_MAP  
 Marca o início do mapa de propriedade do objeto.  
  
```
BEGIN_PROP_MAP(theClass)
```  
  
### <a name="parameters"></a>Parâmetros  
 `theClass`  
 [in] Especifica a classe que contém o mapa de propriedade.  
  
### <a name="remarks"></a>Comentários  
 O mapa de propriedade armazena DISPIDs de propriedade, a página de propriedade CLSIDs, descrições de propriedade e `IDispatch` IIDs. Classes de [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), e [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) usar o mapa de propriedade para recuperar e definir essas informações.  
  
 Quando você cria um objeto com ATL Project Wizard, o assistente criará um mapa de propriedade vazio especificando `BEGIN_PROP_MAP` seguido por [END_PROP_MAP](#end_prop_map).  
  
 `BEGIN_PROP_MAP`não salvar a extensão (ou seja, as dimensões) de um mapa de propriedade, porque um objeto usando um mapa de propriedade não pode ter uma interface de usuário, para que ele tenha nenhuma extensão. Se o objeto for um controle ActiveX com uma interface do usuário, ele tem uma extensão. Nesse caso, você deve especificar [PROP_DATA_ENTRY](#prop_data_entry) em seu mapa de propriedade para fornecer a extensão.  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATL_Windowing&#103;](../../atl/codesnippet/cpp/property-map-macros_1.h)]  
  
##  <a name="a-namepropdataentrya--propdataentry"></a><a name="prop_data_entry"></a>PROP_DATA_ENTRY  
 Indica a extensão ou dimensões de um controle ActiveX.  
  
```
PROP_DATA_ENTRY( szDesc, member, vt)
```    
  
### <a name="parameters"></a>Parâmetros  
 `szDesc`  
 [in] A descrição da propriedade.  
  
 `member`  
 [in] O membro de dados que contém a extensão; Por exemplo, `m_sizeExtent`.  
  
 *VT*  
 [in] Especifica o tipo de VARIANTE da propriedade.  
  
### <a name="remarks"></a>Comentários  
 Esta macro faz com que o membro de dados especificado ser persistente.  
  
 Quando você cria um controle ActiveX, o assistente insere essa macro após a macro de mapa de propriedade [BEGIN_PROP_MAP](#begin_prop_map) e antes da macro de mapa de propriedade [END_PROP_MAP](#end_prop_map).  
  
### <a name="example"></a>Exemplo  
 No exemplo a seguir, a extensão do objeto ( `m_sizeExtent`) está sendo persistente.  
  
 [!code-cpp[NVC_ATL_Windowing&#131;](../../atl/codesnippet/cpp/property-map-macros_2.h)]  
  
 [!code-cpp[NVC_ATL_Windowing&132;](../../atl/codesnippet/cpp/property-map-macros_3.h)]  
  
##  <a name="a-namepropentrytypea--propentrytype"></a><a name="prop_entry_type"></a>PROP_ENTRY_TYPE  
 Use essa macro para inserir uma descrição, a propriedade DISPID e a propriedade página de propriedades CLSID no mapa de propriedade do objeto.  
  
```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```  
  
### <a name="parameters"></a>Parâmetros  
 `szDesc`  
 [in] A descrição da propriedade.  
  
 `dispid`  
 [in] DISPID da propriedade.  
  
 `clsid`  
 [in] O CLSID da página de propriedades associadas. Use o valor especial `CLSID_NULL` para uma propriedade que não tem uma página de propriedade associada.  
  
 `vt`  
 [in] O tipo da propriedade.  
  
### <a name="remarks"></a>Comentários  
 O `PROP_ENTRY` macro foi preterido e inseguro. Ele foi substituído pelo `PROP_ENTRY_TYPE`.  
  
 O [BEGIN_PROP_MAP](#begin_prop_map) macro marca o início do mapa de propriedade; o [END_PROP_MAP](#end_prop_map) macro marca o fim.  
  
### <a name="example"></a>Exemplo  
 Veja o exemplo de [BEGIN_PROP_MAP](#begin_prop_map).  
  
##  <a name="a-namepropentrytypeexa--propentrytypeex"></a><a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX  
 Semelhante ao [PROP_ENTRY_TYPE](#prop_entry_type), mas permite que você especificar um determinado IID se seu objeto oferecer suporte a várias interfaces duplas.  
  
```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```    
  
### <a name="parameters"></a>Parâmetros  
 `szDesc`  
 [in] A descrição da propriedade.  
  
 `dispid`  
 [in] DISPID da propriedade.  
  
 `clsid`  
 [in] O CLSID da página de propriedades associadas. Use o valor especial `CLSID_NULL` para uma propriedade que não tem uma página de propriedade associada.  
  
 `iidDispatch`  
 [in] O IID da interface dupla a definição da propriedade.  
  
 `vt`  
 [in] O tipo da propriedade.  
  
### <a name="remarks"></a>Comentários  
 O `PROP_ENTRY_EX` macro foi preterido e inseguro. Ele foi substituído pelo `PROP_ENTRY_TYPE_EX`.  
  
 O [BEGIN_PROP_MAP](#begin_prop_map) macro marca o início do mapa de propriedade; o [END_PROP_MAP](#end_prop_map) macro marca o fim.  
  
### <a name="example"></a>Exemplo  
 O exemplo a seguir agrupa as entradas para `IMyDual1` seguido por uma entrada para `IMyDual2`. Agrupar por interface dupla irá melhorar o desempenho.  
  
 [!code-cpp[NVC_ATL_Windowing&#133;](../../atl/codesnippet/cpp/property-map-macros_4.h)]  
  
##  <a name="a-nameproppagea--proppage"></a><a name="prop_page"></a>PROP_PAGE  
 Use essa macro para inserir uma página de propriedade CLSID no mapa de propriedade do objeto.  
  
```
PROP_PAGE(clsid)
```  
  
### <a name="parameters"></a>Parâmetros  
 `clsid`  
 [in] O CLSID de uma página de propriedades.  
  
### <a name="remarks"></a>Comentários  
 `PROP_PAGE`é semelhante ao [PROP_ENTRY_TYPE](#prop_entry_type), mas não requer uma descrição de propriedade ou DISPID.  
  
> [!NOTE]
>  Se você tiver inserido um CLSID com `PROP_ENTRY_TYPE` ou [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex), você não precisa criar uma entrada adicional com `PROP_PAGE`.  
  
 O [BEGIN_PROP_MAP](#begin_prop_map) macro marca o início do mapa de propriedade; o [END_PROP_MAP](#end_prop_map) macro marca o fim.  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATL_Windowing&#134;](../../atl/codesnippet/cpp/property-map-macros_5.h)]  
  
##  <a name="a-nameendpropmapa--endpropmap"></a><a name="end_prop_map"></a>END_PROP_MAP  
 Marca o fim do mapa de propriedade do objeto.  
  
```
END_PROP_MAP()
```  
  
### <a name="remarks"></a>Comentários  
 Quando você cria um objeto com ATL Project Wizard, o assistente criará um mapa de propriedade vazio especificando [BEGIN_PROP_MAP](#begin_prop_map) seguido por `END_PROP_MAP`.  
  
### <a name="example"></a>Exemplo  
 Veja o exemplo de [BEGIN_PROP_MAP](#begin_prop_map).  
  
## <a name="see-also"></a>Consulte também  
 [Macros](../../atl/reference/atl-macros.md)
