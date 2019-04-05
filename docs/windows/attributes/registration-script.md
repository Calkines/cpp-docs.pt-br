---
title: registration_script (atributo de COM do C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.registration_script
helpviewer_keywords:
- registration_script attribute
ms.assetid: 786f8072-9187-4163-a979-7a604dd4c888
ms.openlocfilehash: 0b2c4d576a699dea7772821b5635944b2663c57c
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024368"
---
# <a name="registrationscript"></a>registration_script

Executa o script de registro personalizado especificado.

## <a name="syntax"></a>Sintaxe

```cpp
[ registration_script(script) ]
```

### <a name="parameters"></a>Parâmetros

*script*<br/>
O caminho completo para um arquivo de script (. rgs) de registro personalizado. Um valor de **none**, como `script = "none"`, indica que a coclass não tem nenhum requisito de registro.

## <a name="remarks"></a>Comentários

O **registration_script** atributo C++ executa o script de registro personalizado especificado por *script*. Se esse atributo não for especificado, um arquivo. rgs padrão (que contém informações para registrar o componente) será usado. Para obter mais informações sobre arquivos. rgs, consulte [o componente de registro ATL (registrador)](../../atl/atl-registry-component-registrar.md).

Este atributo exige que o [coclass](coclass.md), [progid](progid.md), ou [vi_progid](vi-progid.md) atributo (ou outro atributo que implica uma destas opções) também ser aplicadas ao mesmo elemento.

## <a name="example"></a>Exemplo

O código a seguir especifica que o componente tem um script de registro chamado cpp_attr_ref_registration_script.rgs.

```cpp
// cpp_attr_ref_registration_script.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="REG")];

[object, uuid("d9cd196b-6836-470b-9b9b-5b04b828e5b0")]
__interface IFace {};

// requires "cpp_attr_ref_registration_script.rgs"
// create sample .RGS file "cpp_attr_ref_registration_script.rgs" if it does not exist
[ coclass, registration_script(script="cpp_attr_ref_registration_script.rgs"),
  uuid("50d3ad42-3601-4f26-8cfe-0f1f26f98f67")]
class CMyClass:public IFace {};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Atributo de contexto

|||
|-|-|
|**Aplica-se a**|**class**, **struct**|
|**Repetível**|Não|
|**Atributos obrigatórios**|Um ou mais das seguintes opções: `coclass`, `progid`, ou `vi_progid`.|
|**Atributos inválidos**|Nenhum|

Para obter mais informações sobre os contextos de atributo, consulte [contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte também

[Atributos COM](com-attributes.md)<br/>
[Atributos de classe](class-attributes.md)<br/>
[rdx](rdx.md)