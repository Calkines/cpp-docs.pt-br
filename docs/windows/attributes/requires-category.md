---
title: requires_category (atributo de COM do C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.requires_category
helpviewer_keywords:
- requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
ms.openlocfilehash: e6621e2cec92eadb0ca4b4ac989b4ca7d578b2ef
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429832"
---
# <a name="requirescategory"></a>requires_category

Especifica as categorias de componente necessário da classe de destino.

## <a name="syntax"></a>Sintaxe

```cpp
[ requires_category(
  requires_category) ]
```

### <a name="parameters"></a>Parâmetros

*requires_category*<br/>
A ID da categoria necessária.

## <a name="remarks"></a>Comentários

O **requires_category** atributo C++ especifica as categorias de componentes necessárias para a classe de destino. Para obter mais informações, consulte [REQUIRED_CATEGORY](../../atl/reference/category-macros.md#required_category).

Este atributo exige que o [coclass](coclass.md), [progid](progid.md), ou [vi_progid](vi-progid.md) atributo (ou outro atributo que implica uma destas opções) também ser aplicadas ao mesmo elemento.

## <a name="example"></a>Exemplo

O código a seguir requer que o objeto implementar a categoria de controle.

```cpp
// cpp_attr_ref_requires_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLibrary")];

[ coclass, requires_category("CATID_Control"),
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]
class CMyClass {};
```

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Atributo de contexto

|||
|-|-|
|**Aplica-se a**|**classe**, **struct**|
|**Repetível**|Não|
|**Atributos obrigatórios**|Um ou mais das seguintes opções: `coclass`, `progid`, ou `vi_progid`.|
|**Atributos inválidos**|Nenhum|

Para obter mais informações sobre os contextos de atributo, consulte [contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte também

[Atributos de COM](com-attributes.md)<br/>
[implements_category](implements-category.md)