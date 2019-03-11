---
title: 'Como: Converter de um coleção .NET em um contêiner STL/CLR'
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
ms.openlocfilehash: 836623f6d539b7b28765763a3dc36d477f8c1499
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741690"
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>Como: Converter de um coleção .NET em um contêiner STL/CLR

Este tópico mostra como converter coleções do .NET para seus contêineres STL/CLR equivalentes. Por exemplo, mostraremos como converter um .NET <xref:System.Collections.Generic.List%601> para um STL/CLR [vetor](../dotnet/vector-stl-clr.md) e como converter um .NET <xref:System.Collections.Generic.Dictionary%602> para um STL/CLR [mapa](../dotnet/map-stl-clr.md), mas o procedimento é semelhante para todas as coleções e contêineres .

### <a name="to-create-a-container-from-a-collection"></a>Para criar um contêiner de uma coleção

1. Para converter uma coleção inteira, crie um contêiner STL/CLR e passa a coleção para o construtor.

   O primeiro exemplo demonstra esse procedimento.

-OU-

1. Criar um contêiner STL/CLR genérico com a criação de um [collection_adapter](../dotnet/collection-adapter-stl-clr.md) objeto. Essa classe de modelo tem uma interface de coleção do .NET como um argumento. Para verificar quais interfaces têm suporte, consulte [collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md).

1. Copie o conteúdo da coleção do .NET para o contêiner. Isso pode ser feito usando um STL/CLR [algoritmo](../dotnet/algorithm-stl-clr.md), ou por iteração pela coleção .NET e a inserção de uma cópia de cada elemento no contêiner STL/CLR.

   O segundo exemplo demonstra esse procedimento.

## <a name="example"></a>Exemplo

Neste exemplo, criamos um genérico <xref:System.Collections.Generic.List%601> e adicionar elementos de 5 a ele. Em seguida, criamos uma `vector` usando o construtor que usa um <xref:System.Collections.Generic.IEnumerable%601> como um argumento.

```
// cliext_convert_list_to_vector.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/vector>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    List<int> ^primeNumbersColl = gcnew List<int>();
    primeNumbersColl->Add(2);
    primeNumbersColl->Add(3);
    primeNumbersColl->Add(5);
    primeNumbersColl->Add(7);
    primeNumbersColl->Add(11);

    cliext::vector<int> ^primeNumbersCont =
        gcnew cliext::vector<int>(primeNumbersColl);

    Console::WriteLine("The contents of the cliext::vector are:");
    cliext::vector<int>::const_iterator it;
    for (it = primeNumbersCont->begin(); it != primeNumbersCont->end(); it++)
    {
        Console::WriteLine(*it);
    }
}
```

```Output
The contents of the cliext::vector are:
2
3
5
7
11
```

## <a name="example"></a>Exemplo

Neste exemplo, criamos um genérico <xref:System.Collections.Generic.Dictionary%602> e adicionar elementos de 5 a ele. Em seguida, criamos uma `collection_adapter` para encapsular o <xref:System.Collections.Generic.Dictionary%602> como um contêiner STL/CLR simple. Por fim, podemos criar uma `map` e copie o conteúdo do <xref:System.Collections.Generic.Dictionary%602> para o `map` iterando sobre o `collection_adapter`. Durante esse processo, criamos um novo par usando o `make_pair` funcionar e inserir o novo par de diretamente para o `map`.

```
// cliext_convert_dictionary_to_map.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/map>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    System::Collections::Generic::Dictionary<float, int> ^dict =
        gcnew System::Collections::Generic::Dictionary<float, int>();
    dict->Add(42.0, 42);
    dict->Add(13.0, 13);
    dict->Add(74.0, 74);
    dict->Add(22.0, 22);
    dict->Add(0.0, 0);

    cliext::collection_adapter<System::Collections::Generic::IDictionary<float, int>> dictAdapter(dict);
    cliext::map<float, int> aMap;
    for each (KeyValuePair<float, int> ^kvp in dictAdapter)
    {
        cliext::pair<float, int> aPair = cliext::make_pair(kvp->Key, kvp->Value);
        aMap.insert(aPair);
    }

    Console::WriteLine("The contents of the cliext::map are:");
    cliext::map<float, int>::const_iterator it;
    for (it = aMap.begin(); it != aMap.end(); it++)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", it->first, it->second);
    }
}
```

```Output
The contents of the cliext::map are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>Consulte também

[Referência de biblioteca STL/CLR](../dotnet/stl-clr-library-reference.md)<br/>
[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)<br/>
[Como: converter de um contêiner do STL/CLR em uma coleção do .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)
