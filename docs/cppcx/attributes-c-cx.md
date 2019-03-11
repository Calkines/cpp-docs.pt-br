---
title: Atributos (C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 5f74914ab65fdf2c1803b47665e16378991efa3c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743825"
---
# <a name="attributes-ccx"></a>Atributos (C++/CX)

Um atributo é um tipo especial de classe ref que pode ser colocado entre colchetes para tipos de tempo de execução do Windows e métodos para especificar determinados comportamentos na criação de metadados. Vários atributos predefinidos — por exemplo, [Windows::Foundation::Metadata::WebHostHidden](/uwp/api/Windows.Foundation.Metadata.WebHostHiddenAttribute)— são comumente usados em C + + c++ /CLI código CX. Este exemplo mostra como o atributo é aplicado a uma classe:

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>Atributos personalizados

Você também pode definir atributos personalizados. Atributos personalizados devem estar de acordo com essas regras de tempo de execução do Windows:

- Atributos personalizados podem conter somente campos públicos.

- Os campos de atributo personalizado podem ser inicializados quando o atributo é aplicado a uma classe.

- Um campo pode ser de um destes tipos:

   - int32 (int)

   - uint32 (int não assinado)

   - bool

   - Platform::String^

   - Windows::Foundation::HResult

   - Platform::Type^

   - classe enum pública (inclui enums definidos pelo usuário)

O exemplo a seguir mostra como definir um atributo personalizado e inicializá-lo quando você for usá-lo.

[!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]

## <a name="see-also"></a>Consulte também

[Sistema de tipos (C++/CX)](../cppcx/type-system-c-cx.md)<br/>
[Referência de linguagem do Visual C++](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Referência de namespaces](../cppcx/namespaces-reference-c-cx.md)
