---
title: "Construtores (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "construtores [C++]"
  - "construtores de instância"
  - "objetos [C++], criando"
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Construtores (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Um construtor é um tipo de função de membro que inicializa uma instância de sua classe.  Um construtor tem o mesmo nome que a classe e nenhum valor de retorno.  Um construtor pode ter qualquer número de parâmetros e uma classe pode ter qualquer número de construtores sobrecarregados.  Construtores podem ter qualquer acessibilidade pública, protegida ou privada.  Se você não definir nenhum construtor, o compilador gerará um construtor padrão que não usa nenhum parâmetro; Você pode substituir esse comportamento ao declarar um construtor padrão como excluído.  
  
## Neste tópico  
  
-   [Ordem de construção](#order_of_construction)  
  
-   [Listas de membros](../cpp/constructors-cpp.md#member_lists)  
  
-   [Construtores explícitos](../cpp/constructors-cpp.md#explicit_constructors)  
  
-   [Construtores padrão](../cpp/constructors-cpp.md#default_constructors)  
  
-   [Construtores de cópia e movimentação](../cpp/constructors-cpp.md#copy_and_move_constructors)  
  
-   [Construtores explicitamente usados como padrão e excluídos](../cpp/constructors-cpp.md#explicitly_defaulted_and_deleted_constructors)  
  
-   [Construtores em classes derivadas](../cpp/constructors-cpp.md#constructors_in_derived_classes)  
  
-   [Construtores para as classes que têm várias heranças](../cpp/constructors-cpp.md#constructors_for_classes_that_have_multiple_inheritance)  
  
-   [Funções virtuais em construtores](../cpp/constructors-cpp.md#virtual_functions_in_constructors)  
  
-   [Construtores e classes compostas](../cpp/constructors-cpp.md#constructors_in_composite_classes)  
  
-   [Construtores de delegação](../cpp/constructors-cpp.md#delegating_constructors)  
  
-   [Herança de construtores (C++ 11)](../cpp/constructors-cpp.md#inheriting_constructors)  
  
-   [Regras para declarar construtores](../cpp/constructors-cpp.md#rules_for_declaring_constructors)  
  
-   Construtores padrão e de cópia  
  
-   [Chamar explicitamente construtores](../cpp/constructors-cpp.md#explicitly_invoking_constructors)  
  
##  <a name="order_of_construction"></a> Ordem de construção  
 Um construtor executa seu trabalho nesta ordem:  
  
1.  Chama a classe base e os construtores membros na ordem da declaração.  
  
2.  Se a classe for derivada de classes base virtuais, ela inicializará os ponteiros de base virtuais do objeto.  
  
3.  Se a classe tiver ou herdar funções virtuais, ela inicializará os ponteiros de função virtual do objeto.  Os ponteiros de função virtual apontam para a tabela de função virtual da classe para permitir a associação de chamadas de função virtual ao código.  
  
4.  Executa qualquer código no corpo de sua função.  
  
 O exemplo a seguir mostra a ordem em que a classe base e os construtores membros são chamados no construtor para uma classe derivada.  Primeiro, o construtor de base é chamado, depois os membros da classe base são inicializados na ordem em que aparecem na declaração de classe e, em seguida, o construtor derivado é chamado.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class Contained1 {  
public:  
    Contained1() {  
        cout << "Contained1 constructor." << endl;  
    }  
};  
  
class Contained2 {  
public:  
    Contained2() {  
        cout << "Contained2 constructor." << endl;  
    }  
};  
  
class Contained3 {  
public:  
    Contained3() {  
        cout << "Contained3 constructor." << endl;  
    }  
};  
  
class BaseContainer {  
public:  
    BaseContainer() {  
        cout << "BaseContainer constructor." << endl;  
    }  
private:  
    Contained1 c1;  
    Contained2 c2;  
};  
  
class DerivedContainer : public BaseContainer {  
public:  
    DerivedContainer() : BaseContainer() {  
        cout << "DerivedContainer constructor." << endl;  
    }  
private:  
    Contained3 c3;  
};  
  
int main() {  
    DerivedContainer dc;  
    int x = 3;  
}  
  
```  
  
 Este é o resultado:  
  
```  
Contained1 constructor.  
Contained2 constructor.  
BaseContainer constructor.  
Contained3 constructor.  
DerivedContainer constructor.  
```  
  
 Se um construtor gerar uma exceção, a ordem de destruição será a inversa da ordem de construção:  
  
1.  O código no corpo da função de construtor é liberado.  
  
2.  Os objetos de classe base e de membros são destruídos, na ordem inversa da declaração.  
  
3.  Se o construtor não for representante, todos os objetos da classe base e membros completamente construídos serão destruídos.  No entanto, como o próprio objeto não está totalmente construído, o destruidor não é executado.  
  
##  <a name="member_lists"></a> Listas de membros  
 Inicialize membros de classe de argumentos de construtor usando uma lista de inicializadores de membro.  Esse método usa*inicialização direta*que é mais eficiente do que usando operadores de atribuição dentro do corpo do construtor.  
  
```cpp  
class Box {  
public:  
    Box(int width, int length, int height)   
        : m_width(width), m_length(length), m_height(height) // member init list  
    {}  
    int Volume() {return m_width * m_length * m_height; }  
private:  
    int m_width;  
    int m_length;  
    int m_height;  
  
};  
  
```  
  
 Crie um objeto de caixa:  
  
```  
Box b(42, 21, 12);  
cout << "The volume is " << b.Volume();  
```  
  
##  <a name="explicit_constructors"></a> Construtores explícitos  
 Se uma classe tem um construtor com um único parâmetro, ou se todos os parâmetros exceto um tem um valor padrão, o tipo de parâmetro pode ser convertido implicitamente no tipo de classe.  Por exemplo, se o`Box`classe tem um construtor como este:  
  
```  
Box(int size): m_width(size), m_length(size), m_height(size){}  
```  
  
 É possível inicializar uma caixa como esta:  
  
```  
Box b = 42;  
```  
  
 Ou passar um int para uma função que usa uma caixa:  
  
```  
class ShippingOrder  
{  
public:  
    ShippingOrder(Box b, double postage) : m_box(b), m_postage(postage){}  
  
private:  
    Box m_box;  
    double m_postage;  
}  
//elsewhere...  
    ShippingOrder so(42, 10.8);  
  
```  
  
 Essas conversões podem ser útil em alguns casos, mas com mais freqüência eles podem levar a erros sutis mas graves no seu código.  Como regra geral, você deve usar o`explicit`palavra\-chave em um construtor \(e operadores definidos pelo usuário\) para evitar esse tipo de conversão implícita de tipos:  
  
```  
  
explicit Box(int size): m_width(size), m_length(size), m_height(size){}  
```  
  
 Quando o construtor explícito, essa linha causa um erro do compilador:`ShippingOrder so(42, 10.8);`.  Para obter mais informações, consulte[Conversões](../cpp/user-defined-type-conversions-cpp.md).  
  
##  <a name="default_constructors"></a> Construtores padrão  
 *Construtores padrão*não ter parâmetros; eles seguem regras ligeiramente diferentes:  
  
 Construtores padrão são um do*funções de membro especial*; se nenhum construtor for declarado em uma classe, o compilador fornece um construtor padrão:  
  
```cpp  
class Box {  
    Box(int width, int length, int height)   
        : m_width(width), m_length(length), m_height(height){}  
};  
  
int main(){  
  
    Box box1{}; // call compiler-generated default ctor  
    Box box2;   // call compiler-generated default ctor  
}  
```  
  
 Quando você chama um construtor padrão e tenta usar parênteses, é emitido um aviso:  
  
```cpp  
class myclass{};  
int main(){  
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)  
}  
```  
  
 Este é um exemplo do problema Most Vexing Parse.  Como a expressão de exemplo pode ser interpretada como a declaração de uma função ou como invocação de um construtor padrão, e como os analisadores de C\+\+ preferem as declarações a outras coisas, a expressão é tratada como uma declaração de função.  Para obter mais informações, consulte [Most Vexing Parse](http://en.wikipedia.org/wiki/Most_vexing_parse).  
  
 Se algum construtor não padrão for declarado, o compilador não fornecerá um construtor padrão:  
  
```cpp  
class Box {  
    Box(int width, int length, int height)   
        : m_width(width), m_length(length), m_height(height){}  
};  
private:  
    int m_width;  
    int m_length;  
    int m_height;  
  
};  
  
int main(){  
  
    Box box1(1, 2, 3);  
    Box box2{ 2, 3, 4 };  
    Box box4;     // compiler error C2512: no appropriate default constructor available  
}  
  
```  
  
 Se uma classe não tiver um construtor padrão, uma matriz de objetos dessa classe não poderá ser construída usando apenas a sintaxe de colchete.  Por exemplo, dado o bloco de códigos anterior, uma matriz de caixas não pode ser declarada assim:  
  
```cpp  
Box boxes[3];    // compiler error C2512: no appropriate default constructor available  
  
```  
  
 No entanto, você pode usar um conjunto de listas de inicializadores para inicializar uma matriz de caixas:  
  
```cpp  
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };  
```  
  
##  <a name="copy_and_move_constructors"></a> Construtores de cópia e movimentação  
 Um*Construtor de cópia*é uma função de membro especial que utiliza como entrada uma referência a um objeto do mesmo tipo e faz uma cópia dele.  Para obter mais informações, consulte[construtores de cópia e operadores de atribuição de cópia \(C\+\+\)](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md).  Uma mudança também é que um construtor de função de membro especial move a propriedade de um objeto existente para uma nova variável sem copiar os dados originais.  Para obter mais informações, consulte[Mover construtores e operadores de atribuição Move \(C\+\+\)](http://msdn.microsoft.com/pt-br/1442de5f-37a5-42a1-83a6-ec9cfe0414db)e[Operadores de construtores de movimento e de atribuição de movimento \(C\+\+\)](../Topic/Move%20Constructors%20and%20Move%20Assignment%20Operators%20\(C++\).md).  
  
##  <a name="explicitly_defaulted_and_deleted_constructors"></a> Construtores explicitamente usados como padrão e excluídos  
 Padronizar explicitamente construtores de cópia, construtores padrão, mover construtores, operadores de atribuição de copiar, mover os operadores de atribuição e destruidores.  Você pode excluir todas as funções de membro especial explicitamente.  Para obter mais informações, consulte[Funções explicitamente usadas como padrão e excluídas](../Topic/Explicitly%20Defaulted%20and%20Deleted%20Functions.md).  
  
##  <a name="constructors_in_derived_classes"></a> Construtores em classes derivadas  
 Um construtor de classe derivada sempre chama um construtor de classe base, de modo que possa confiar em classes base completamente construídas antes que qualquer trabalho adicional seja feito.  Os construtores de classe base são chamados por ordem derivação – por exemplo, se ClassA é derivada de ClassB, que é derivada de ClassC, o construtor de ClassC é chamado primeiro, depois o construtor de ClassB e, por fim, o construtor de ClassA.  
  
 Se uma classe base não tiver um construtor padrão, você deverá fornecer os parâmetros do construtor de classe base no construtor de classe derivada:  
  
```cpp  
class Box {  
public:  
    Box(int width, int length, int height){  
       m_width = width;  
       m_length = length;  
       m_height = height;  
    }  
  
private:  
    int m_width;  
    int m_length;  
    int m_height;  
};  
  
class StorageBox : public Box {  
public:  
    StorageBox(int width, int length, int height, const string label&) : Box(width, length, height){  
        m_label = label;  
    }  
private:  
    string m_label;  
};  
  
int main(){  
  
    const string aLabel = "aLabel";  
    StorageBox sb(1, 2, 3, aLabel);  
}   
```  
  
### Construtores para as classes que têm várias heranças  
 Se uma classe for derivada de várias classes base, os construtores de classe base serão chamados na ordem em que estão listados na declaração da classe derivada:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class BaseClass1 {  
public:  
    BaseClass1() {  
        cout << "BaseClass1 constructor." << endl;  
    }  
};  
class BaseClass2 {  
public:  
    BaseClass2() {  
        cout << "BaseClass2 constructor." << endl;  
    }  
};  
class BaseClass3{  
public:  
    BaseClass3() {  
        cout << "BaseClass3 constructor." << endl;  
    }  
};  
class DerivedClass : public BaseClass1, public BaseClass2, public BaseClass3  {  
public:  
    DerivedClass() {  
        cout << "DerivedClass constructor." << endl;  
    }  
};  
  
int main() {  
    DerivedClass dc;  
}  
  
```  
  
 O seguinte resultado é esperado:  
  
```  
BaseClass1 constructor.  
BaseClass2 constructor.  
BaseClass3 constructor.  
DerivedClass constructor.  
```  
  
##  <a name="virtual_functions_in_constructors"></a> Funções virtuais em construtores  
 Recomendamos que você seja cuidadoso ao chamar funções virtuais nos construtores.  Como o construtor da classe base é sempre chamado antes do construtor de classe derivada, a função que é chamada no construtor de base é a versão da classe base, não a versão da classe derivada.  No exemplo a seguir, construir `DerivedClass` faz com que a implementação de `BaseClass` de `print_it()` seja executada antes que o construtor de `DerivedClass` faça com que a implementação de `DerivedClass` de `print_it()` seja executada:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class BaseClass{  
public:  
    BaseClass(){  
        print_it();  
    }  
    virtual void print_it() {  
        cout << "BaseClass print_it" << endl;  
    }  
};  
  
class DerivedClass : public BaseClass {  
public:  
    DerivedClass() {  
        print_it();  
    }  
    virtual void print_it(){  
        cout << "Derived Class print_it" << endl;  
    }  
};  
  
int main() {  
  
    DerivedClass dc;  
}  
```  
  
 Este é o resultado:  
  
```  
BaseClass print_it  
Derived Class print_it  
```  
  
##  <a name="constructors_in_composite_classes"></a> Construtores e classes compostas  
 As classes que contêm membros do tipo classe são conhecidas como *classes compostas*.  Quando um membro do tipo classe de uma classe composta é criado, o construtor é chamado antes do próprio construtor da classe.  Quando uma classe contida não possuir um construtor padrão, você deverá usar uma lista de inicialização no construtor da classe composta.  No exemplo anterior de `StorageBox`, se você alterar o tipo da variável de membro `m_label` para uma nova classe `Label`, deverá chamar o construtor da classe base e inicializar a variável `m_label` no construtor `StorageBox`:  
  
```cpp  
class Label {  
public:  
    Label(const string& name, const string& address) { m_name = name; m_address = address; }  
    string m_name;  
    string m_address;  
};  
  
class StorageBox : public Box {  
public:  
    StorageBox(int width, int length, int height, Label label)   
        : Box(width, length, height), m_label(label){}  
private:  
    Label m_label;  
};  
  
int main(){  
// passing a named Label  
    Label label1{ "some_name", "some_address" };  
    StorageBox sb1(1, 2, 3, label1);  
  
    // passing a temporary label  
    StorageBox sb2(3, 4, 5, Label{ "another name", "another address" });  
  
    // passing a temporary label as an initializer list  
    StorageBox sb3(1, 2, 3, {"myname", "myaddress"});  
}  
```  
  
##  <a name="delegating_constructors"></a> Construtores de delegação  
 Um *construtor de delegação* chama um construtor diferente na mesma classe para fazer algum de trabalho de inicialização.  No exemplo a seguir, a classe derivada tem três construtores – o segundo construtor delega o primeiro, e o terceiro construtor delega o segundo:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
class ConstructorDestructor {  
public:  
    ConstructorDestructor() {  
        cout << "ConstructorDestructor default constructor." << endl;  
    }  
    ConstructorDestructor(int int1) {  
        cout << "ConstructorDestructor constructor with 1 int." << endl;  
    }  
    ConstructorDestructor(int int1, int int2) : ConstructorDestructor(int1) {  
        cout << "ConstructorDestructor constructor with 2 ints." << endl;  
  
        throw exception();  
    }  
    ConstructorDestructor(int int1, int int2, int int3) : ConstructorDestructor(int1, int2) {  
        cout << "ConstructorDestructor constructor with 3 ints." << endl;  
    }  
    ~ConstructorDestructor() {  
        cout << "ConstructorDestructor destructor." << endl;  
    }  
};  
  
int main() {  
    ConstructorDestructor dc(1, 2, 3);  
}  
  
```  
  
 Este é o resultado:  
  
```  
ConstructorDestructor constructor with 1 int.  
ConstructorDestructor constructor with 2 ints.  
ConstructorDestructor constructor with 3 ints.  
```  
  
 O objeto criado pelos construtores é inicializado totalmente assim que o construtor é concluído.  `DerivedContainer(int int1)` tem êxito, mas `DerivedContainer(int int1, int int2)` falha e o destruidor é chamado.  
  
```cpp  
class ConstructorDestructor {  
public:  
    ConstructorDestructor() {  
        cout << "ConstructorDestructor default constructor." << endl;  
    }  
    ConstructorDestructor(int int1) {  
        cout << "ConstructorDestructor constructor with 1 int." << endl;  
    }  
    ConstructorDestructor(int int1, int int2) : ConstructorDestructor(int1) {  
        cout << "ConstructorDestructor constructor with 2 ints." << endl;  
        throw exception();  
    }  
    ConstructorDestructor(int int1, int int2, int int3) : ConstructorDestructor(int1, int2) {  
        cout << "ConstructorDestructor constructor with 3 ints." << endl;  
    }  
  
    ~ConstructorDestructor() {  
        cout << "ConstructorDestructor destructor." << endl;  
    }  
};  
  
int main() {  
  
    try {  
        ConstructorDestructor cd{ 1, 2, 3 };  
    }  
    catch (const exception& ex){  
    }  
}  
  
```  
  
 Saída:  
  
```  
ConstructorDestructor constructor with 1 int.  
ConstructorDestructor constructor with 2 ints.  
ConstructorDestructor destructor.  
```  
  
 Para obter mais informações, consulte[Inicialização uniforme e delegação de construtores](../cpp/uniform-initialization-and-delegating-constructors.md).  
  
##  <a name="inheriting_constructors"></a> Herança de construtores \(C\+\+ 11\)  
 Uma classe derivada herda os construtores de uma classe base direta usando uma declaração, como mostrado no exemplo a seguir:  
  
```  
#include <iostream>  
using namespace std;  
  
class Base  
{  
public:      
    Base() { cout << "Base()" << endl; }  
    Base(const Base& other) { cout << "Base(Base&)" << endl; }  
    explicit Base(int i) : num(i) { cout << "Base(int)" << endl; }  
    explicit Base(char c) : letter(c) { cout << "Base(char)" << endl; }  
  
private:  
    int num;  
    char letter;  
};  
  
class Derived : Base  
{  
public:  
    // Inherit all constructors from Base  
    using Base::Base;  
  
private:  
    // Can't initialize newMember from Base constructors.  
    int newMember{ 0 };  
};  
  
int main(int argc, char argv[])  
{  
    cout << "Derived d1(5) calls: ";   
    Derived d1(5);  
    cout << "Derived d1('c') calls: ";  
    Derived d2('c');  
    cout << "Derived d3 = d2 calls: " ;  
    Derived d3 = d2;  
    cout << "Derived d4 calls: ";  
    Derived d4;   
  
    // Keep console open in debug mode:  
    cout << endl << "Press Enter to exit.";  
    char in[1];  
    cin.getline(in, 1);  
    return 0;  
}  
  
/* Output:  
Derived d1(5) calls: Base(int)  
Derived d1('c') calls: Base(char)  
Derived d3 = d2 calls: Base(Base&)  
Derived d4 calls: Base()  
  
Press Enter to exit.  
  
```  
  
 A instrução using traz para o escopo de todos os construtores da classe base, exceto aqueles que tenham uma assinatura idêntica a construtores na classe derivada.  Em geral, é melhor usar construtores, quando a classe derivada não declarar nenhum membro de dados novo ou construtores de herança.  
  
 Um modelo de classe pode herdar todos os construtores de um argumento de tipo, se esse tipo Especifica uma classe base:  
  
```  
template< typename T >  
class Derived : T {  
    using T::T;   // declare the constructors from T  
    // ...  
};  
  
```  
  
 Uma classe derivada não pode herdar de várias classes base se essas classes base têm construtores que possuem uma assinatura idêntica.  
  
##  <a name="rules_for_declaring_constructors"></a> Regras para declarar construtores  
 Um construtor tem o mesmo nome de sua classe.  Qualquer número de construtores pode ser declarado, sujeito às regras de funções sobrecarregadas.  \(Para obter mais informações, consulte [Sobrecarga](../misc/overloading-cpp.md).\)  
  
 A `argument-declaration-list` pode ficar em branco.  
  
 O C\+\+ define dois tipos especiais dos construtores, os construtores padrão e de cópia, descritos na tabela a seguir.  
  
### Construtores padrão e de cópia  
  
|Tipo de construção|Arguments|Finalidade|  
|------------------------|---------------|----------------|  
|Construtor padrão|Pode ser chamado sem argumentos|Construir um objeto padrão do tipo de classe|  
|Construtor de cópia|Pode aceitar um único argumento de referência ao mesmo tipo de classe|Copiar objetos do tipo de classe|  
  
 Os construtores padrão podem ser chamados sem argumentos.  No entanto, você pode declarar um construtor padrão com uma lista de argumentos, desde que todos os argumentos tenham opções.  Da mesma forma, os construtores de cópia devem aceitar um único argumento de referência ao mesmo tipo de classe.  Mais argumentos podem ser fornecidos, contanto que todos os argumentos subsequentes tenham opções.  
  
 Se você não fornecer construtores, o compilador tentará gerar um construtor padrão.  Se você não fornecer um construtor de cópia, o compilador tentará gerar um.  Esses construtores gerados pelo compilador são considerados funções de membro públicas.  Um erro será gerado se você especificar um construtor de cópia com um primeiro argumento que é um objeto e não uma referência.  
  
 Um construtor padrão gerado pelo compilador configura o objeto \(inicializa vftables e vbtables, como descrito anteriormente\), e ele chama os construtores padrão para classes base e membros, mas não executa nenhuma outra ação.  Os construtores de classe base e de membro são chamados somente se existirem, forem acessíveis e não ambíguos.  
  
 Um construtor de cópia gerado pelo compilador configura um novo objeto e executa uma cópia de membro do conteúdo do objeto a ser copiado.  Se os construtores de classe base ou de membro existirem, eles serão chamados; caso contrário, a cópia bit a bit será executada.  
  
 Se todas as classes base e membro de uma classe`type`têm construtores de cópia que aceitam um**const**argumento, o construtor de cópia gerado pelo compilador aceitará um único argumento do tipo**const**`type`**&**.  Caso contrário, o construtor de cópia gerado pelo compilador aceitará um único argumento do tipo`type`**&**.  
  
 Você pode usar um construtor para inicializar um objeto **const** ou `volatile`, mas o construtor em si não pode ser declarado como **const** ou `volatile`.  A única classe de armazenamento válida para um construtor é **inline**; o uso de qualquer outro modificador de classe de armazenamento, incluindo a palavra\-chave `__declspec`, com um construtor causa um erro do compilador.  
  
 A convenção de chamada stdcall é usada em funções de membro estático e funções globais declaradas com o**stdcall**palavra\-chave e que não use uma lista de argumentos variável.  Quando você usa o**stdcall**palavra\-chave em uma função de membro não estático, como um construtor, o compilador usará a convenção de chamada thiscall. "  
  
 Os construtores de classes base não são herdados por classes derivadas.  Quando um objeto de tipo de classe derivada é criado, é construído a partir dos componentes da classe base; depois passa para os componentes da classe derivada.  O compilador usa cada construtor de classe base, pois essa parte do objeto completo é inicializada \(exceto nos casos de derivação virtual, conforme descrito em [Inicializando classes base](../misc/initializing-base-classes.md)\).  
  
##  <a name="explicitly_invoking_constructors"></a> Chamar explicitamente construtores  
 Os construtores podem ser chamados explicitamente em um programa para criar objetos de um tipo específico.  Por exemplo, para criar dois objetos `Point` que descrevem as extremidades de uma linha, o código a seguir pode ser escrito:  
  
```  
DrawLine( Point( 13, 22 ), Point( 87, 91 ) );  
```  
  
 Dois objetos do tipo `Point` são criados, passados para a função `DrawLine` e destruídos no final da expressão \(a chamada de função\).  
  
 Outro contexto no qual um construtor é chamado explicitamente está em uma inicialização:  
  
```  
Point pt = Point( 7, 11 );  
```  
  
 Um objeto do tipo `Point` é criado e inicializado usando o construtor que aceita dois argumentos do tipo `int`.  
  
 Os objetos que são criados chamando construtores explicitamente, como nos dois exemplos anteriores, não têm nome e têm um tempo de vida útil da expressão na qual são criados.  Isso é abordado em mais detalhes em [Objetos temporários](../cpp/temporary-objects.md).  
  
 Normalmente, é seguro chamar qualquer função membro dentro de um construtor pois o objeto foi configurado completamente \(as tabelas virtuais foram inicializadas e assim por diante\) antes da execução da primeira linha do código do usuário.  No entanto, é potencialmente inseguro que uma função membro chame uma função membro virtual para uma classe base abstrata durante a criação ou a destruição.  
  
 Os construtores podem chamar funções virtuais.  Quando as funções virtuais são chamadas, a função chamada é a função definida para própria classe do construtor \(ou herdada de suas bases\).  O exemplo a seguir mostra o que ocorre quando uma função virtual é chamada de dentro de um construtor:  
  
```  
// specl_calling_virtual_functions.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class Base  
{  
public:  
    Base();             // Default constructor.  
    virtual void f();   // Virtual member function.  
};  
  
Base::Base()  
{  
    cout << "Constructing Base sub-object\n";  
    f();                // Call virtual member function  
}                       //  from inside constructor.  
  
void Base::f()  
{  
    cout << "Called Base::f()\n";  
}  
  
class Derived : public Base  
{  
public:  
    Derived();          // Default constructor.  
    void f();           // Implementation of virtual  
};                      //  function f for this class.  
  
Derived::Derived()  
{  
    cout << "Constructing Derived object\n";  
}  
  
void Derived::f()  
{  
    cout << "Called Derived::f()\n";  
}  
  
int main()  
{  
    Derived d;  
}  
```  
  
 Quando o programa anterior é executado, a declaração `Derived d` causa a seguinte sequência de eventos:  
  
1.  O construtor para a classe `Derived` \(`Derived::Derived`\) é chamado.  
  
2.  Antes de entrar no corpo do construtor da classe `Derived`, o construtor da classe `Base` \(`Base::Base`\) é chamado.  
  
 `Base::Base` chama a função `f`, que é uma função virtual.  Normalmente, `Derived::f` será chamado porque o objeto `d` é do tipo `Derived`.  Como a função `Base::Base` é um construtor, o objeto ainda não é do tipo `Derived` e `Base::f` é chamado.  
  
## Consulte também  
 [Funções de membro especiais](../misc/special-member-functions-cpp.md)