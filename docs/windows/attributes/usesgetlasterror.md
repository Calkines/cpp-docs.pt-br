---
title: usesgetlasterror (atributo de COM do C++)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: 9f050bbf69edf1ab8327a283299cb5e687ce5380
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032200"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

Informa ao chamador que se houver um erro ao chamar essa função, em seguida, o chamador pode, em seguida, chamar `GetLastError` para recuperar o código de erro.

## <a name="syntax"></a>Sintaxe

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>Comentários

O **usesgetlasterror** atributo C++ tem a mesma funcionalidade que o [usesgetlasterror](/windows/desktop/Midl/usesgetlasterror) atributo MIDL.

## <a name="example"></a>Exemplo

Consulte a [idl_module](idl-module.md) exemplo para obter um exemplo de como usar **usesgetlasterror**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Atributo de contexto

|||
|-|-|
|**Aplica-se a**|**módulo** atributo|
|**Repetível**|Não|
|**Atributos obrigatórios**|Nenhum|
|**Atributos inválidos**|Nenhum|

Para obter mais informações sobre os contextos de atributo, consulte [contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte também

[Atributos IDL](idl-attributes.md)