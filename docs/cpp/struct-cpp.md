---
title: struct (C++)
ms.date: 11/04/2016
f1_keywords:
- struct_cpp
helpviewer_keywords:
- struct constructors
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
ms.openlocfilehash: e9ffd30dd0017e912fd7c196e2d3f0e987fb0810
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330577"
---
# <a name="struct-c"></a>struct (C++)

O **struct** palavra-chave define um tipo de estrutura e/ou uma variável de um tipo de estrutura.

## <a name="syntax"></a>Sintaxe

```
[template-spec] struct [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[struct] tag declarators;
```

#### <a name="parameters"></a>Parâmetros

*template-spec*<br/>
Especificações de modelo opcionais. Para obter mais informações, consulte [especificações de modelo](templates-cpp.md).

*struct*<br/>
O **struct** palavra-chave.

*ms-decl-spec*<br/>
Especificação de classe de armazenamento opcional. Para obter mais informações, consulte o [declspec](../cpp/declspec.md) palavra-chave.

*tag*<br/>
O nome do tipo dado à estrutura. A marca se torna uma palavra reservada no escopo da estrutura. A marca é opcional. Se omitida, uma estrutura anônima será definida. Para obter mais informações, consulte [tipos de classe anônima](../cpp/anonymous-class-types.md).

*base-list*<br/>
A lista opcional de classes ou estruturas de que esta estrutura derivará seus membros. Ver [Classes Base](../cpp/base-classes.md) para obter mais informações. Cada nome de classe ou estrutura de base pode ser precedido por um especificador de acesso ([pública](../cpp/public-cpp.md), [privada](../cpp/private-cpp.md), [protegido](../cpp/protected-cpp.md)) e o [virtual](../cpp/virtual-cpp.md) palavra-chave. Consulte a tabela de acesso de membro [controlando o acesso a membros de classe](member-access-control-cpp.md) para obter mais informações.

*member-list*<br/>
Lista de membros da estrutura. Consulte a [visão geral de membros de classe](../cpp/class-member-overview.md) para obter mais informações. A única diferença aqui é que **struct** é usado no lugar de **classe**.

*declarators*<br/>
Lista de declaradores que especificam os nomes da estrutura. As listas de declaradores declaram uma ou mais instâncias do tipo de estrutura. Os declaradores podem incluir listas de inicializadores se todos os membros de dados da estrutura são **público**. Listas de inicializadores são comuns em estruturas porque membros de dados são **pública** por padrão.  Ver [visão geral dos declaradores](../cpp/overview-of-declarators.md) para obter mais informações.

## <a name="remarks"></a>Comentários

Um tipo de estrutura é um tipo composto definido pelo usuário. É composto de campos ou membros que podem ter tipos diferentes.

No C++, uma estrutura é o mesmo que uma classe, exceto pelo fato de que seus membros são **pública** por padrão.

Para obter informações sobre classes gerenciadas e estruturas em C++/CLI, consulte [Classes e Structs](../extensions/classes-and-structs-cpp-component-extensions.md).

## <a name="using-a-structure"></a>Usando uma estrutura

Em C, você deve usar explicitamente o **struct** palavra-chave para declarar uma estrutura. No C++, você não precisará usar o **struct** palavra-chave depois que o tipo foi definido.

Há também a opção de declarar variáveis quando o tipo de estrutura é definido colocando um ou vários nomes de variável separados por vírgulas entre a chave de fechamento e o ponto-e-vírgula.

As variáveis de estrutura podem ser inicializadas. A inicialização de cada variável deve ser incluída entre chaves.

Para obter informações relacionadas, consulte [classe](../cpp/class-cpp.md), [união](../cpp/unions.md), e [enum](../cpp/enumerations-cpp.md).

## <a name="example"></a>Exemplo

```cpp
#include <iostream>
using namespace std;

struct PERSON {   // Declare PERSON struct type
    int age;   // Declare member types
    long ss;
    float weight;
    char name[25];
} family_member;   // Define object of type PERSON

struct CELL {   // Declare CELL bit field
    unsigned short character  : 8;  // 00000000 ????????
    unsigned short foreground : 3;  // 00000??? 00000000
    unsigned short intensity  : 1;  // 0000?000 00000000
    unsigned short background : 3;  // 0???0000 00000000
    unsigned short blink      : 1;  // ?0000000 00000000
} screen[25][80];       // Array of bit fields

int main() {
    struct PERSON sister;   // C style structure declaration
    PERSON brother;   // C++ style structure declaration
    sister.age = 13;   // assign values to members
    brother.age = 7;
    cout << "sister.age = " << sister.age << '\n';
    cout << "brother.age = " << brother.age << '\n';

    CELL my_cell;
    my_cell.character = 1;
    cout << "my_cell.character = " << my_cell.character;
}
// Output:
// sister.age = 13
// brother.age = 7
// my_cell.character = 1
```
