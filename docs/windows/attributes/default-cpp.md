---
title: padrão (C++ COM atributo) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.default
dev_langs:
- C++
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2ca39b160aacdf72bb6d6131b757755f87ac22a6
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075067"
---
# <a name="default-c"></a>default (C++)

Indica que o personalizado ou dispinterface definido dentro de uma coclass representa a interface de programação padrão.

## <a name="syntax"></a>Sintaxe

```cpp
[ default(interface1, interface2) ]
```

### <a name="parameters"></a>Parâmetros

*Interface1*<br/>
A interface padrão que será disponibilizada para os ambientes de script que cria um objeto com base na classe definida com o **padrão** atributo.

Se nenhuma interface padrão for especificado, a primeira ocorrência de uma interface nonsource é usada como o padrão.

*Interface2*<br/>
(Opcional) A interface de origem padrão. Você também deve especificar essa interface com o [origem](source-cpp.md) atributo.

Se nenhuma interface de origem padrão for especificado, a primeira interface de origem é usada como o padrão.

## <a name="remarks"></a>Comentários

O **padrão** atributo C++ tem a mesma funcionalidade que o [padrão](/windows/desktop/Midl/default) atributo MIDL. O **padrão** atributo também é usado com o [caso](case-cpp.md) atributo.

## <a name="example"></a>Exemplo

O seguinte código mostra como **padrão** é usado na definição de uma coclass para especificar `ICustomDispatch` como a interface de programação padrão:

```cpp
// cpp_attr_ref_default.cpp
// compile with: /LD
#include "windows.h"
[module(name="MyLibrary")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};

[dual, uuid("9E66A291-4365-11D2-A997-00C04FA37DDB")]
__interface IDual {
   HRESULT Dual([in] long l, [out, retval] long *pLong);
};

[object, uuid("9E66A293-4365-11D2-A997-00C04FA37DDB")]
__interface ICustomDispatch : public IDispatch {
   HRESULT Dispatch([in] long l, [out, retval] long *pLong);
};

[   coclass, default(ICustomDispatch), source(IDual), uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")
]
class CClass : public ICustom, public IDual, public ICustomDispatch {
   HRESULT Custom(long l, long *pLong) { return(S_OK); }
   HRESULT Dual(long l, long *pLong) { return(S_OK); }
   HRESULT Dispatch(long l, long *pLong) { return(S_OK); }
};

int main() {
#if 0 // Can't instantiate without implementations of IUnknown/IDispatch
   CClass *pClass = new CClass;

   long llong;

   pClass->custom(1, &llong);
   pClass->dual(1, &llong);
   pClass->dispinterface(1, &llong);
   pClass->dispatch(1, &llong);

   delete pClass;
#endif
   return(0);
}
```

O [fonte](source-cpp.md) atributo também tem um exemplo de como usar **padrão**.

## <a name="requirements"></a>Requisitos

### <a name="attribute-context"></a>Atributo de contexto

|||
|-|-|
|**Aplica-se a**|**classe**, **struct**, membro de dados|
|**Repetível**|Não|
|**Atributos obrigatórios**|**coclass** (quando aplicado a **classe** ou **struct**)|
|**Atributos inválidos**|Nenhum|

Para obter mais informações, consulte [contextos de atributo](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Consulte também

[Atributos de IDL](idl-attributes.md)<br/>
[Atributos de classe](class-attributes.md)<br/>
[coclass](coclass.md)