---
title: Implementando CComObject, CComAggObject e CComPolyObject
ms.date: 11/04/2016
helpviewer_keywords:
- CComPolyObject class, implementing
- CreateInstance method
- CComAggObject class
- CComObject class, implementing
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
ms.openlocfilehash: e2413c8fb9f5722f0245883c947067387838e57f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261781"
---
# <a name="implementing-ccomobject-ccomaggobject-and-ccompolyobject"></a>Implementando CComObject, CComAggObject e CComPolyObject

As classes de modelo [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md), e [CComPolyObject](../atl/reference/ccompolyobject-class.md) sempre são as classes mais derivadas da cadeia de herança. É sua responsabilidade de lidar com todos os métodos em `IUnknown`: `QueryInterface`, `AddRef`, e `Release`. Além disso, `CComAggObject` e `CComPolyObject` (quando usado para objetos agregados) fornecem a contagem de referência especial e `QueryInterface` semântica necessária para o desconhecido interno.

Se `CComObject`, `CComAggObject`, ou `CComPolyObject` é usado depende se você declarar uma (ou nenhuma) de macros a seguir:

|Macro|Efeito|
|-----------|------------|
|DECLARE_NOT_AGGREGATABLE|Sempre usa `CComObject`.|
|DECLARE_AGGREGATABLE|Usa `CComAggObject` se o objeto for agregado e `CComObject` se não for. `CComCoClass` contém essa macro se nenhuma do DECLARE_ * macros _AGGREGATABLE são declaradas em sua classe, esse será o padrão.|
|DECLARE_ONLY_AGGREGATABLE|Sempre usa `CComAggObject`. Retorna um erro se o objeto não é agregado.|
|DECLARE_POLY_AGGREGATABLE|ATL cria uma instância de **CComPolyObject\<CYourClass >** quando `IClassFactory::CreateInstance` é chamado. Durante a criação, o valor do externo desconhecido é verificado. Se for NULL, `IUnknown` é implementada para um objeto não agregado. Se o externo desconhecido não for nulo, `IUnknown` é implementada para um objeto agregado.|

A vantagem de usar `CComAggObject` e `CComObject` é que a implementação do `IUnknown` é otimizado para o tipo de objeto que está sendo criado. Por exemplo, um objeto não agregado precisa somente uma contagem de referência, enquanto um objeto agregado precisa de uma contagem de referência para o desconhecido interno e um ponteiro para o externo desconhecido.

A vantagem de usar `CComPolyObject` é que você evite ter dois `CComAggObject` e `CComObject` em seu módulo para tratar de casos agregados e não agregados. Um único `CComPolyObject` objeto lida com ambos os casos. Isso significa que apenas uma cópia de vtable e uma cópia das funções existem em seu módulo. Se seu vtable for grande, isso pode diminuir substancialmente o tamanho do módulo. No entanto, se seu vtable for pequeno, usando `CComPolyObject` pode resultar em um tamanho de módulo ligeiramente maior porque ele não é otimizado para um objeto agregado ou não agregado, que estejam `CComAggObject` e `CComObject`.

## <a name="see-also"></a>Consulte também

[Princípios básicos de objetos COM da ATL](../atl/fundamentals-of-atl-com-objects.md)<br/>
[Macros de fábrica de classes e agregação](../atl/reference/aggregation-and-class-factory-macros.md)
