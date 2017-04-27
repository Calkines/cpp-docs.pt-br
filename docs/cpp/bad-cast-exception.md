---
title: "Exce&#231;&#227;o bad_cast | Microsoft Docs"
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
  - "bad_cast"
  - "bad_cast_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Palavra-chave bad_cast [C++]"
  - "exceções, bad_cast"
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exce&#231;&#227;o bad_cast
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A exceção `bad_cast` é lançada pelo operador `dynamic_cast` como resultado de uma conversão em um tipo de referência que falhou.  
  
## Sintaxe  
  
```  
catch (bad_cast)  
   statement  
```  
  
## Comentários  
 A interface de `bad_cast` é:  
  
```  
class bad_cast : public exception {  
public:  
   bad_cast(const char * _Message = "bad cast");  
   bad_cast(const bad_cast &);  
   virtual ~bad_cast();  
};  
```  
  
 O código a seguir contém um exemplo de `dynamic_cast` com falha que lança a exceção `bad_cast`.  
  
```  
// expre_bad_cast_Exception.cpp  
// compile with: /EHsc /GR  
#include <typeinfo.h>  
#include <iostream>  
  
class Shape {  
public:  
   virtual void virtualfunc() const {}  
};  
  
class Circle: public Shape {  
public:  
   virtual void virtualfunc() const {}  
};  
  
using namespace std;  
int main() {  
   Shape shape_instance;  
   Shape& ref_shape = shape_instance;  
   try {  
      Circle& ref_circle = dynamic_cast<Circle&>(ref_shape);   
   }  
   catch (bad_cast b) {  
      cout << "Caught: " << b.what();  
   }  
}  
```  
  
 A exceção é lançada porque o objeto que está sendo convertido \(uma forma\) não é derivado do tipo convertido especificado \(círculo\).  Para evitar a exceção, adicione estas declarações a `main`:  
  
```  
Circle circle_instance;  
Circle& ref_circle = circle_instance;  
```  
  
 Depois, inverta o sentido da conversão no bloco `try` como segue:  
  
```  
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);  
```  
  
## Consulte também  
 [Operador dynamic\_cast](../cpp/dynamic-cast-operator.md)   
 [Palavras\-chave C\+\+](../cpp/keywords-cpp.md)   
 [Tratamento de exceções C\+\+](../cpp/cpp-exception-handling.md)