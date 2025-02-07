---
title: class (C++)
ms.date: 11/04/2016
f1_keywords:
- class_cpp
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
ms.openlocfilehash: c4ef9690a41737147354ee0976f6912c4711ff67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331071"
---
# <a name="class-c"></a>class (C++)

O **classe** palavra-chave declara um tipo de classe ou define um objeto de um tipo de classe.

## <a name="syntax"></a>Sintaxe

```
[template-spec]
class [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[ class ] tag declarators;
```

#### <a name="parameters"></a>Parâmetros

*template-spec*<br/>
Especificações de modelo opcionais. Para obter mais informações, consulte [modelos](templates-cpp.md).

*class*<br/>
O **classe** palavra-chave.

*ms-decl-spec*<br/>
Especificação de classe de armazenamento opcional. Para obter mais informações, consulte o [declspec](../cpp/declspec.md) palavra-chave.

*tag*<br/>
O nome do tipo dado à classe. A marca se torna uma palavra reservada no escopo da classe. A marca é opcional. Se omitida, uma classe anônima será definida. Para obter mais informações, consulte [tipos de classe anônima](../cpp/anonymous-class-types.md).

*base-list*<br/>
A lista opcional de classes ou estruturas da qual esta classe derivará seus membros. Ver [Classes Base](../cpp/base-classes.md) para obter mais informações. Cada nome de classe ou estrutura de base pode ser precedido por um especificador de acesso ([pública](../cpp/public-cpp.md), [privada](../cpp/private-cpp.md), [protegido](../cpp/protected-cpp.md)) e o [virtual](../cpp/virtual-cpp.md) palavra-chave. Consulte a tabela de acesso de membro [controlando o acesso a membros de classe](member-access-control-cpp.md) para obter mais informações.

*member-list*<br/>
Lista de membros da classe. Consulte a [visão geral de membros de classe](../cpp/class-member-overview.md) para obter mais informações.

*declarators*<br/>
Lista de declaradores que especifica os nomes de uma ou mais instâncias do tipo da classe. Os declaradores podem incluir listas de inicializadores se todos os membros de dados da classe estiverem **público**. Isso é mais comum em estruturas, cujos membros de dados são **pública** por padrão, que em classes. Ver [visão geral dos declaradores](../cpp/overview-of-declarators.md) para obter mais informações.

## <a name="remarks"></a>Comentários

Para obter mais informações sobre as classes em geral, consulte um dos seguintes tópicos:

- [struct](../cpp/struct-cpp.md)

- [union](../cpp/unions.md)

- [__multiple_inheritance](../cpp/inheritance-keywords.md)

- [__single_inheritance](../cpp/inheritance-keywords.md)

- [__virtual_inheritance](../cpp/inheritance-keywords.md)

Para obter informações sobre classes gerenciadas e estruturas em C++/CLI e C++/CX, consulte [Classes e Structs](../extensions/classes-and-structs-cpp-component-extensions.md)

## <a name="example"></a>Exemplo

```cpp
// class.cpp
// compile with: /EHsc
// Example of the class keyword
// Exhibits polymorphism/virtual functions.

#include <iostream>
#include <string>
#define TRUE = 1
using namespace std;

class dog
{
public:
   dog()
   {
      _legs = 4;
      _bark = true;
   }

   void setDogSize(string dogSize)
   {
      _dogSize = dogSize;
   }
   virtual void setEars(string type)      // virtual function
   {
      _earType = type;
   }

private:
   string _dogSize, _earType;
   int _legs;
   bool _bark;

};

class breed : public dog
{
public:
   breed( string color, string size)
   {
      _color = color;
      setDogSize(size);
   }

   string getColor()
   {
      return _color;
   }

   // virtual function redefined
   void setEars(string length, string type)
   {
      _earLength = length;
      _earType = type;
   }

protected:
   string _color, _earLength, _earType;
};

int main()
{
   dog mongrel;
   breed labrador("yellow", "large");
   mongrel.setEars("pointy");
   labrador.setEars("long", "floppy");
   cout << "Cody is a " << labrador.getColor() << " labrador" << endl;
}
```

## <a name="see-also"></a>Consulte também

[Palavras-chave](../cpp/keywords-cpp.md)<br/>
[Classes e Structs](../cpp/classes-and-structs-cpp.md)