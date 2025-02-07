---
title: Conversões padrão e conversão boxing implícita
ms.date: 11/04/2016
helpviewer_keywords:
- boxing, implicit
ms.assetid: 33f7fc7d-5674-44a2-a859-0e6a04fae519
ms.openlocfilehash: b771f9e9c1dc05fcd2ead19f5202747d7c475a09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384615"
---
# <a name="standard-conversions-and-implicit-boxing"></a>Conversões padrão e conversão boxing implícita

Uma conversão padrão será escolhida pelo compilador ao longo de uma conversão que requer boxing.

## <a name="example"></a>Exemplo

```
// clr_implicit_boxing_Std_conversion.cpp
// compile with: /clr
int f3(int ^ i) {   // requires boxing
   return 1;
}

int f3(char c) {   // no boxing required, standard conversion
   return 2;
}

int main() {
   int i = 5;
   System::Console::WriteLine(f3(i));
}
```

```Output
2
```

## <a name="see-also"></a>Consulte também

[Conversão boxing](../extensions/boxing-cpp-component-extensions.md)
