---
title: 'Como: Definir e consumir enums no c++ /CLI CLI'
ms.date: 11/04/2016
helpviewer_keywords:
- enum class, specifying underlying types
ms.assetid: df8f2b91-b9d2-4fab-9be4-b1d58b8bc570
ms.openlocfilehash: 9787b7b96f83b2926c65209254c88eb56fe1a8ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387377"
---
# <a name="how-to-define-and-consume-enums-in-ccli"></a>Como: Definir e consumir enums no c++ /CLI CLI

Este tópico discute as enums no c++ /CLI CLI.

## <a name="specifying-the-underlying-type-of-an-enum"></a>Especifica o tipo subjacente de um enum

Por padrão, o tipo subjacente de uma enumeração é `int`.  No entanto, você pode especificar o tipo a ser com ou sem sinal de formas de `int`, `short`, `long`, `__int32`, ou `__int64`.  Você também pode usar `char`.

```
// mcppv2_enum_3.cpp
// compile with: /clr
public enum class day_char : char {sun, mon, tue, wed, thu, fri, sat};

int main() {
   // fully qualified names, enumerator not injected into scope
   day_char d = day_char::sun, e = day_char::mon;
   System::Console::WriteLine(d);
   char f = (char)d;
   System::Console::WriteLine(f);
   f = (char)e;
   System::Console::WriteLine(f);
   e = day_char::tue;
   f = (char)e;
   System::Console::WriteLine(f);
}
```

**Saída**

```Output
sun
0
1
2
```

## <a name="how-to-convert-between-managed-and-standard-enumerations"></a>Como converter entre enumerações gerenciadas e padrão

Não há nenhuma conversão padrão entre um enum e um tipo integral; uma conversão é necessária.

```
// mcppv2_enum_4.cpp
// compile with: /clr
enum class day {sun, mon, tue, wed, thu, fri, sat};
enum {sun, mon, tue, wed, thu, fri, sat} day2; // unnamed std enum

int main() {
   day a = day::sun;
   day2 = sun;
   if ((int)a == day2)
   // or...
   // if (a == (day)day2)
      System::Console::WriteLine("a and day2 are the same");
   else
      System::Console::WriteLine("a and day2 are not the same");
}
```

**Saída**

```Output
a and day2 are the same
```

## <a name="operators-and-enums"></a>Operadores e enumerações

Os operadores a seguir são válidos em enums no c++ /CLI CLI:

|Operador|
|--------------|
|== != \< > \<= >=|
|+ -|
|&#124; ^ & ~|
|++ --|
|sizeof|

Operadores &#124; ^ & ~ + + – são definidas apenas para enumerações com tipos, não incluindo bool subjacentes de integral.  Ambos os operandos devem ser do tipo de enumeração.

O compilador não faz nenhuma verificação estática ou dinâmica do resultado de uma operação de enumeração; uma operação pode resultar em um valor não está no intervalo de enumeradores de válido da enumeração.

> [!NOTE]
>  C++11 introduz os tipos de classe de enum em código não gerenciado que são significativamente diferentes de classes enum gerenciado no C++/CLI. Em particular, o tipo de classe de enumeração C + + 11 não suporta os mesmos operadores como o tipo de classe enum gerenciado em C++/CLI, e C++/código-fonte da CLI deve fornecer declarações de classe de um especificador de acessibilidade na enum gerenciado para distingui-los do não gerenciado (c++11) declarações de classe de enum. Para obter mais informações sobre classes enum no C++/CLI, C++/CX e c++11, see [classe enum](../extensions/enum-class-cpp-component-extensions.md).

```
// mcppv2_enum_5.cpp
// compile with: /clr
private enum class E { a, b } e, mask;
int main() {
   if ( e & mask )   // C2451 no E->bool conversion
      ;

   if ( ( e & mask ) != 0 )   // C3063 no operator!= (E, int)
      ;

   if ( ( e & mask ) != E() )   // OK
      ;
}
```

```
// mcppv2_enum_6.cpp
// compile with: /clr
private enum class day : int {sun, mon};
enum : bool {sun = true, mon = false} day2;

int main() {
   day a = day::sun, b = day::mon;
   day2 = sun;

   System::Console::WriteLine(sizeof(a));
   System::Console::WriteLine(sizeof(day2));
   a++;
   System::Console::WriteLine(a == b);
}
```

**Saída**

```Output
4
1
True
```

## <a name="see-also"></a>Consulte também

[enum class](../extensions/enum-class-cpp-component-extensions.md)
