---
title: "struct (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "struct"
  - "struct_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "construtores struct"
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# struct (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A palavra\-chave `struct` define um tipo de estrutura e\/ou uma variável de um tipo de estrutura.  
  
## Sintaxe  
  
```  
[template-spec] struct [ms-decl-spec] [tag [: base-list ]]  
{   
   member-list   
} [declarators];  
[struct] tag declarators;  
```  
  
#### Parâmetros  
 `template-spec`  
 Especificações de modelo opcionais.  Para obter mais informações, consulte [Especificações de modelo](../Topic/Template%20Specifications.md).  
  
 `struct`  
 A palavra\-chave `struct`.  
  
 `ms-decl-spec`  
 Especificação de classe de armazenamento opcional.  Para obter mais informações, consulte a palavra\-chave [\_\_declspec](../cpp/declspec.md).  
  
 `tag`  
 O nome do tipo dado à estrutura.  A marca se torna uma palavra reservada no escopo da estrutura.  A marca é opcional.  Se omitida, uma estrutura anônima será definida.  Para obter mais informações, consulte [Tipos anônimos de classes](../cpp/anonymous-class-types.md).  
  
 `base-list`  
 A lista opcional de classes ou estruturas de que esta estrutura derivará seus membros.  Consulte [Classes base](../cpp/base-classes.md) para obter mais informações.  Cada nome de classe base ou estrutura pode ser precedido por um especificador de acesso \([public](../cpp/public-cpp.md), [private](../Topic/private%20\(C++\).md), [protected](../Topic/protected%20\(C++\).md)\) e pela palavra\-chave [virtual](../cpp/virtual-cpp.md).  Consulte a tabela de acesso do membro em [Controlando o acesso a membros de classe](../misc/controlling-access-to-class-members.md) para obter mais informações.  
  
 `member-list`  
 Lista de membros da estrutura.  Consulte [Visão geral de membros de classe](../Topic/Class%20Member%20Overview.md) para obter mais informações.  A única diferença aqui é que `struct` é usado no lugar de `class`.  
  
 `declarators`  
 Lista de declaradores que especificam os nomes da classe.  As listas de declaradores declaram uma ou mais instâncias do tipo de estrutura.  Os declaradores podem incluir listas de inicializadores se todos os membros de dados da classe forem `public`.  Listas de inicializadores são comuns em estruturas porque membros de dados são `public` por padrão.  Consulte [Visão geral dos declaradores](../cpp/overview-of-declarators.md) para obter mais informações.  
  
## Comentários  
 Um tipo de estrutura é um tipo composto definido pelo usuário.  É composto de campos ou membros que podem ter tipos diferentes.  
  
 Em C\+\+, uma estrutura é a mesma de uma classe, porém seus membros são `public` por padrão.  
  
 Para obter mais informações sobre classes e structs gerenciadas, consulte [Classes e structs](../windows/classes-and-structs-cpp-component-extensions.md).  
  
## Usando uma estrutura  
 Em C, você deve usar explicitamente a palavra\-chave `struct` para declarar uma estrutura.  Em C\+\+, você não precisa usar a palavra\-chave `struct` depois que o tipo é definido.  
  
 Há também a opção de declarar variáveis quando o tipo de estrutura é definido colocando um ou vários nomes de variável separados por vírgulas entre a chave de fechamento e o ponto\-e\-vírgula.  
  
 As variáveis de estrutura podem ser inicializadas.  A inicialização de cada variável deve ser incluída entre chaves.  
  
 Para obter informações relacionadas, consulte [classe](../cpp/class-cpp.md), [união](../cpp/unions.md) e [enum](../cpp/enumerations-cpp.md).  
  
## Exemplo  
  
```  
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
  
## Consulte também  
 [\(NOTINBUILD\) Defining Class Types](http://msdn.microsoft.com/pt-br/e8c65425-0f3a-4dca-afc2-418c3b1e57da)