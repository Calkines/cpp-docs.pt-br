---
title: Membros estáticos (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- class members [C++], static
- instance constructors, static members
- class members [C++], shared
- members [C++], static data members
- static members [C++], data members
- static data members [C++]
- data members [C++], static data members
- class instances [C++], shared members
- instance constructors, shared members
- class instances [C++], static members
ms.assetid: 9cc8cf0f-d74c-46f2-8e83-42d4e42c8370
ms.openlocfilehash: 708f78c09db263584d478d16863999d4428e4891
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266940"
---
# <a name="static-members-c"></a>Membros estáticos (C++)

As classes podem conter dados estáticos de membros e funções de membros. Quando um membro de dados é declarado como **estático**, apenas uma cópia dos dados é mantida para todos os objetos da classe.

Membros de dados estáticos não fazem parte dos objetos de um determinado tipo de classe. Como resultado, a declaração de um membro de dados estáticos não é considerada uma definição. O membro de dados é declarado no escopo da classe, mas a definição é realizada no escopo do arquivo. Esses membros estáticos têm vinculação externa. O exemplo a seguir ilustra isto:

```cpp
// static_data_members.cpp
class BufferedOutput
{
public:
   // Return number of bytes written by any object of this class.
   short BytesWritten()
   {
      return bytecount;
   }

   // Reset the counter.
   static void ResetCount()
   {
      bytecount = 0;
   }

   // Static member declaration.
   static long bytecount;
};

// Define bytecount in file scope.
long BufferedOutput::bytecount;

int main()
{
}
```

No código anterior, o membro `bytecount` é declarado na classe `BufferedOutput`, mas deve ser definido fora de declaração da classe.

Os membros de dados estáticos podem ser mencionados sem fazer referência a um objeto do tipo da classe. O número de bytes gravados usando objetos `BufferedOutput` pode ser obtido da seguinte maneira:

```cpp
long nBytes = BufferedOutput::bytecount;
```

Para que o membro estático exista, não é necessário que objetos do tipo de classe existam. Membros estáticos também podem ser acessados usando a seleção de membro (**.** e **->**) operadores. Por exemplo:

```cpp
BufferedOutput Console;

long nBytes = Console.bytecount;
```

No caso anterior, a referência ao objeto (`Console`) não é avaliada. O valor retornado é o do objeto estático `bytecount`.

Os membros de dados estáticos estão sujeitos às regras de acesso do membro da classe. Portanto, o acesso particular aos membros de dados estáticos é permitido somente para funções de membro da classe e friends. Essas regras são descritas em [controle de acesso de membro](../cpp/member-access-control-cpp.md). A exceção é que os membros de dados estáticos devem ser definidos no escopo de arquivo, independentemente das suas restrições de acesso. Se o membro de dados for inicializado explicitamente, um inicializador deverá ser fornecido com a definição.

O tipo de um membro estático não é qualificado por seu nome de classe. Portanto, o tipo de `BufferedOutput::bytecount` está **longo**.

## <a name="see-also"></a>Consulte também

[Classes e Structs](../cpp/classes-and-structs-cpp.md)