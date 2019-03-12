---
title: '&lt;value&gt; (Visual C++)'
ms.date: 11/04/2016
f1_keywords:
- value
- <value>
helpviewer_keywords:
- value C++ XML tag
- <value> C++ XML tag
ms.assetid: 0ba0a0d5-bcd7-4862-a169-83f2721ad80e
ms.openlocfilehash: 6add2d7fb6676d631a03d5f6e1764ebf221b4c52
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57742503"
---
# <a name="ltvaluegt-visual-c"></a>&lt;value&gt; (Visual C++)

A marcação \<value> permite descrever uma propriedade e os métodos do acessador de propriedade. Observe que, quando você adicionar uma propriedade com um assistente de código no ambiente de desenvolvimento integrado do Visual Studio, ele adicionará uma marcação [\<summary>](../ide/summary-visual-cpp.md) à nova propriedade. Então, você deve adicionar manualmente uma marca \<value> para descrever o valor que a propriedade representa.

## <a name="syntax"></a>Sintaxe

```
<value>property-description</value>
```

#### <a name="parameters"></a>Parâmetros

*property-description*<br/>
Uma descrição da propriedade.

## <a name="remarks"></a>Comentários

Compile com [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

```
// xml_value_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_value_tag.dll
using namespace System;
/// Text for class Employee.
public ref class Employee {
private:
   String ^ name;
   /// <value>Name accesses the value of the name data member</value>
public:
   property String ^ Name {
      String ^ get() {
         return name;
      }
      void set(String ^ i) {
         name = i;
      }
   }
};
```

## <a name="see-also"></a>Consulte também

[Documentação XML](../ide/xml-documentation-visual-cpp.md)
