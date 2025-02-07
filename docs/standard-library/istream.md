---
title: '&lt;istream&gt;'
ms.date: 11/04/2016
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
helpviewer_keywords:
- istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
ms.openlocfilehash: 0ad27bf849e8d4b9188868b9a29bf423b4cafafa
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458737"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

Define a classe de modelo basic_istream, que atua como mediador de extrações para os iostreams e a classe de modelo basic_iostream, que atua como mediador de extrações e inserções. O cabeçalho também define um manipulador relacionado. Esse arquivo de cabeçalho geralmente é incluído para você por outro cabeçalho iostreams, dificilmente você precisará incluí-lo diretamente.

## <a name="syntax"></a>Sintaxe

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedefs

|Nome de tipo|Descrição|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|Um tipo `basic_iostream` especializado em **Char**.|
|[istream](../standard-library/istream-typedefs.md#istream)|Um tipo `basic_istream` especializado em **Char**.|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|Um tipo `basic_iostream` especializado em **wchar**.|
|[wistream](../standard-library/istream-typedefs.md#wistream)|Um tipo `basic_istream` especializado em **wchar**.|

### <a name="manipulators"></a>Manipuladores

|||
|-|-|
|[ws](../standard-library/istream-functions.md#ws)|Ignora o espaço em branco no fluxo.|
|[swap](../standard-library/istream-functions.md#istream_swap)|Troca dois objetos de fluxo.|

### <a name="operators"></a>Operadores

|Operador|Descrição|
|-|-|
|[operator>>](../standard-library/istream-operators.md#op_gt_gt)|Extrai caracteres e cadeias de caracteres do fluxo.|

### <a name="classes"></a>Classes

|Classe|Descrição|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|Uma classe de fluxo que pode fazer tanto entrada quanto saída.|
|[basic_istream](../standard-library/basic-istream-class.md)|A classe de modelo descreve um objeto que controla a extração de elementos e objetos codificados de um buffer de `Elem`fluxo com elementos do tipo, também conhecidos como [char_type](../standard-library/basic-ios-class.md#char_type), cujas características de caractere `Tr`são determinadas pela classe, também conhecido como [traits_type](../standard-library/basic-ios-class.md#traits_type).|

## <a name="see-also"></a>Consulte também

[Acesso Thread-Safe na Biblioteca Padrão C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programação de iostream](../standard-library/iostream-programming.md)\
[Convenções de iostreams](../standard-library/iostreams-conventions.md)
