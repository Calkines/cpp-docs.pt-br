---
title: "Operador static_cast | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "static_cast"
  - "static_cast_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Palavra-chave static_cast [C++]"
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operador static_cast
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Converte *expression* no tipo de *type\-id,* com base somente nos tipos que estiverem presentes na expressão.  
  
## Sintaxe  
  
```  
static_cast <type-id> ( expression )   
```  
  
## Comentários  
 No padrão C\+\+, nenhuma verificação de tipo de tempo de execução é feita para ajudar a garantir a segurança da conversão.  No C\+\+\/CX, uma verificação de tempo de compilação e de tempo de execução é executada.  Para obter mais informações, consulte [Conversão](../Topic/Casting%20\(C++-CX\).md).  
  
 O operador `static_cast` pode ser usado para operações como converter um ponteiro em uma classe base, em um ponteiro e em uma classe derivada.  Essas conversões não são sempre seguras.  
  
 Em geral, você usa `static_cast` quando quer converter tipos de dados numéricos, como enums, em ints ou ints em floats, e tem certeza dos tipos de dados envolvidos na conversão.  As conversões `static_cast` não são tão seguranças quanto as conversões `dynamic_cast`, pois `static_cast` não verifica o tipo de tempo de execução, enquanto `dynamic_cast` verifica.  `dynamic_cast` em um ponteiro ambíguo falhará, enquanto `static_cast` é retornado como se nada estivesse errado; isso pode ser perigoso.  Embora as conversões `dynamic_cast` sejam seguras, `dynamic_cast` só funciona em ponteiros ou referências, e a verificação de tipo de tempo de execução é uma sobrecarga.  Para obter mais informações, consulte [Operador dynamic\_cast](../cpp/dynamic-cast-operator.md).  
  
 No exemplo a seguir, a linha `D* pd2 = static_cast<D*>(pb);` não é segura porque `D` pode ter campos e métodos que não estão em `B`.  No entanto, a linha `B* pb2 = static_cast<B*>(pd);` é uma conversão segura porque `D` sempre contém tudo de `B`.  
  
```  
// static_cast_Operator.cpp  
// compile with: /LD  
class B {};  
  
class D : public B {};  
  
void f(B* pb, D* pd) {  
   D* pd2 = static_cast<D*>(pb);   // Not safe, D can have fields  
                                   // and methods that are not in B.  
  
   B* pb2 = static_cast<B*>(pd);   // Safe conversion, D always  
                                   // contains all of B.  
}  
```  
  
 Em contraste com [dynamic\_cast](../cpp/dynamic-cast-operator.md), nenhuma verificação de tempo de execução é feita na conversão `static_cast` de `pb`.  O objeto apontado por `pb` não pode ser um objeto do tipo `D`, pois, nesse caso, o uso de `*pd2` seria desastroso.  Por exemplo, chamar uma função que é membro da classe `D`, mas não da classe `B`, poderá resultar em uma violação de acesso.  
  
 Os operadores `dynamic_cast` e `static_cast` movem um ponteiro em toda uma hierarquia de classe.  No entanto, `static_cast` confia exclusivamente nas informações fornecidas na instrução de conversão e, portanto, pode ser não seguro.  Por exemplo:  
  
```  
// static_cast_Operator_2.cpp  
// compile with: /LD /GR  
class B {  
public:  
   virtual void Test(){}  
};  
class D : public B {};  
  
void f(B* pb) {  
   D* pd1 = dynamic_cast<D*>(pb);  
   D* pd2 = static_cast<D*>(pb);  
}  
```  
  
 Se `pb` apontar para um objeto do tipo `D`, `pd1` e `pd2` obterão o mesmo valor.  Eles também obterão o mesmo valor se `pb == 0`.  
  
 Se `pb` apontar para um objeto do tipo `B` e não para a classe `D` completa, `dynamic_cast` terá conhecimento suficiente para retornar zero.  No entanto, `static_cast` depende da asserção do programador de que `pb` aponta para um objeto do tipo `D` e simplesmente retorna um ponteiro ao suposto objeto `D`.  
  
 Portanto, `static_cast` pode fazer o inverso de conversões implícitas; nesse caso, os resultados são indefinidos.  O programador deve verificar se os resultados de uma conversão `static_cast` são seguros.  
  
 Esse comportamento também se aplica a tipos diferentes dos tipos de classe.  Por exemplo, `static_cast` pode ser usado para converter um int em `char`.  No entanto, o `char` resultante pode não ter bits suficientes para armazenar o valor inteiro de `int`.  Além disso, o programador deve verificar se os resultados de uma conversão`static_cast` são seguros.  
  
 O operador `static_cast` também pode ser usado para executar qualquer conversão implícita, incluindo conversões padrão e conversões definidas pelo usuário.  Por exemplo:  
  
```  
// static_cast_Operator_3.cpp  
// compile with: /LD /GR  
typedef unsigned char BYTE;  
  
void f() {  
   char ch;  
   int i = 65;  
   float f = 2.5;  
   double dbl;  
  
   ch = static_cast<char>(i);   // int to char  
   dbl = static_cast<double>(f);   // float to double  
   i = static_cast<BYTE>(ch);  
}  
```  
  
 O operador `static_cast` pode converter explicitamente um valor integral em um tipo de enumeração.  Se o valor do tipo integral não estiver dentro do intervalo de valores de enumeração, o valor de enumeração resultante será indefinido.  
  
 O operador `static_cast` converte um valor de ponteiro nulo em valor de ponteiro nulo do tipo de destino.  
  
 Qualquer expressão pode ser explicitamente convertida no tipo void pelo operador `static_cast`.  O tipo void de destino pode, opcionalmente, incluir o atributo `const`, `volatile` ou `__unaligned`.  
  
 O operador `static_cast` não pode eliminar os atributos `const`, `volatile` ou `__unaligned`.  Consulte [Operador const\_cast](../Topic/const_cast%20Operator.md) para obter informações sobre como remover esses atributos.  
  
 Devido ao perigo de realizar conversões não verificadas sobre um coletor de lixo de realocação, o uso de `static_cast` só deve estar no código crítico de desempenho quando você tiver certeza de que funcionará corretamente.  Se você precisar usar `static_cast` no modo de liberação, substitua\-o por [safe\_cast](../windows/safe-cast-cpp-component-extensions.md) em suas compilações de depuração para garantir o êxito.  
  
## Consulte também  
 [Operadores de conversão](../cpp/casting-operators.md)   
 [Palavras\-chave C\+\+](../cpp/keywords-cpp.md)