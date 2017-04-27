---
title: Macros de mapa do objeto | Documentos do Microsoft
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
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: f03ca61c6ab3c550c316b380d34eb5fa4f3b61de
ms.lasthandoff: 02/25/2017

---
# <a name="object-map-macros"></a>Macros de mapa de objeto
Essas macros definem mapas de objeto e entradas.  
  
|||  
|-|-|  
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Permite que você especifique a descrição de texto do objeto de classe, que será inserida no mapa de objetos.|  
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Insere um objeto ATL no mapa de objetos, atualiza o registro e cria uma instância do objeto.|  
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Permite que você especifique que o objeto deve ser registrado e inicializado, mas não deve ser criáveis externamente por meio de `CoCreateInstance`.|  

## <a name="requirements"></a>Requisitos  
 **Cabeçalho:** atlcom.h  
   
##  <a name="a-namedeclareobjectdescriptiona--declareobjectdescription"></a><a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION  
 Permite que você especifique uma descrição para o objeto de classe.  
  
```
DECLARE_OBJECT_DESCRIPTION( x )
```  
  
### <a name="parameters"></a>Parâmetros  
 *x*  
 [in] Descrição do objeto de classe.  
  
### <a name="remarks"></a>Comentários  
 ATL insere essa descrição no mapa de objetos por meio de [OBJECT_ENTRY](http://msdn.microsoft.com/en-us/abd10ee2-54f0-4f94-9ec2-ddf8f4c8c8cd) macro.  
  
 `DECLARE_OBJECT_DESCRIPTION`implementa uma `GetObjectDescription` função, que você pode usar para substituir o [CComCoClass::GetObjectDescription](ccomcoclass-class.md#getobjectdescription) método.  

  
 O `GetObjectDescription` função é chamada pelo **IComponentRegistrar::GetComponents**. **IComponentRegistrar** é uma interface de automação que permite registrar e cancelar o registro de componentes individuais em uma DLL. Quando você cria um objeto de componente registrador com ATL Project Wizard, o assistente automaticamente implementará o **IComponentRegistrar** interface. **IComponentRegistrar** normalmente é usado pelo Microsoft Transaction Server.  
  
 Para obter mais informações sobre os ATL Project Wizard, consulte o artigo [criando um projeto ATL](../../atl/reference/creating-an-atl-project.md).  
  
### <a name="example"></a>Exemplo  
 [!code-cpp[NVC_ATL_Windowing&123;](../../atl/codesnippet/cpp/object-map-macros_1.h)]  
  
##  <a name="a-nameobjectentryautoa--objectentryauto"></a><a name="object_entry_auto"></a>OBJECT_ENTRY_AUTO  
 Insere um objeto ATL no mapa de objetos, atualiza o registro e cria uma instância do objeto.  
  
```
OBJECT_ENTRY_AUTO( clsid, class )
```  
  
### <a name="parameters"></a>Parâmetros  
 `clsid`  
 [in] O CLSID de uma classe COM implementado pela classe C++ chamado `class`.  
  
 `class`  
 [in] O nome da classe C++ Implementando a classe COM representado por `clsid`.  
  
### <a name="remarks"></a>Comentários  
 Macros de entrada de objeto são colocadas no escopo global do projeto para oferecer suporte à criação de uma classe, registro e inicialização.  
  
 `OBJECT_ENTRY_AUTO`Insere os ponteiros de função da classe do criador e classe do criador de fábrica de classes `CreateInstance` funções para este objeto para o mapa de objeto ATL gerado automaticamente. Quando [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver) é chamado, ele atualiza o registro do sistema para cada objeto no mapa de objetos.  

  
 A tabela a seguir descreve como as informações adicionadas ao mapa de objetos são obtidas da classe determinada como o segundo parâmetro para essa macro.  
  
|Informações de|Obtido|  
|---------------------|-------------------|  
|Registro COM|[Macros de registro](../../atl/reference/registry-macros.md)|  
|Criação da classe de fábrica|[Macros de fábrica de classe](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|Criação de instância|[Macros de agregação](../../atl/reference/aggregation-and-class-factory-macros.md)|  
|Registro de categoria de componente|[Macros de categoria](../../atl/reference/category-macros.md)|  
|Limpeza e inicialização de nível de classe|[ObjectMain](ccomobjectrootex-class.md#objectmain)|  

  
##  <a name="a-nameobjectentrynoncreateableexautoa--objectentrynoncreateableexauto"></a><a name="object_entry_non_createable_ex_auto"></a>OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO  
 Permite que você especifique que o objeto deve ser registrado e inicializado, mas não deve ser criáveis externamente por meio de `CoCreateInstance`.  
  
```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```  
  
### <a name="parameters"></a>Parâmetros  
 `clsid`  
 [in] O CLSID de uma classe COM implementado pela classe C++ chamado `class`.  
  
 `class`  
 [in] O nome da classe C++ Implementando a classe COM representado por `clsid`.  
  
### <a name="remarks"></a>Comentários  
 Macros de entrada de objeto são colocadas no escopo global do projeto para oferecer suporte à criação de uma classe, registro e inicialização.  
  
 `OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO`permite que você especifique que um objeto deve ser registrado e inicializado (consulte [OBJECT_ENTRY_AUTO](#object_entry_auto) para obter mais informações), mas não devem ser criáveis via `CoCreateInstance`.  
  
## <a name="see-also"></a>Consulte também  
 [Macros](../../atl/reference/atl-macros.md)
