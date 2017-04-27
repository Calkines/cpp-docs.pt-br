---
title: "Especializa&#231;&#227;o parcial de modelos de classe (C++) | Microsoft Docs"
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
  - "especialização parcial de modelos de classe"
ms.assetid: f3c67c0b-3875-434a-b8d8-bb47e99cf4f0
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Especializa&#231;&#227;o parcial de modelos de classe (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Os modelos da classe podem estar parcialmente especializados e a classe resultante ainda é um modelo.  A especialização parcial permite que o código do modelo seja personalizado parcialmente para tipos específicos em situações, como:  
  
-   Um modelo tem vários tipos e apenas alguns deles precisam ser especializados.  O resultado é um modelo com parâmetros nos tipos restantes.  
  
-   Um modelo tem apenas um tipo, mas uma especialização é necessária para os tipos ponteiro, referência, ponteiro para o membro ou o ponteiro de função.  A própria especialização ainda é um modelo no tipo apontado ou referenciado.  
  
## Exemplo  
  
```  
// partial_specialization_of_class_templates.cpp  
template <class T> struct PTS {  
   enum {  
      IsPointer = 0,  
      IsPointerToDataMember = 0  
   };  
};  
  
template <class T> struct PTS<T*> {  
   enum {  
      IsPointer = 1,  
      IsPointerToDataMember = 0  
   };  
};  
  
template <class T, class U> struct PTS<T U::*> {  
   enum {  
      IsPointer = 0,  
      IsPointerToDataMember = 1  
   };  
};  
  
struct S{};  
  
extern "C" int printf_s(const char*,...);  
  
int main() {  
   S s, *pS;  
   int S::*ptm;  
   printf_s("PTS<S>::IsPointer == %d PTS<S>::IsPointerToDataMember == %d\n",   
           PTS<S>::IsPointer, PTS<S>:: IsPointerToDataMember);  
   printf_s("PTS<S*>::IsPointer == %d PTS<S*>::IsPointerToDataMember ==%d\n"  
           , PTS<S*>::IsPointer, PTS<S*>:: IsPointerToDataMember);  
   printf_s("PTS<int S::*>::IsPointer == %d PTS"  
           "<int S::*>::IsPointerToDataMember == %d\n",   
           PTS<int S::*>::IsPointer, PTS<int S::*>::   
           IsPointerToDataMember);  
}  
```  
  
  **PTS\<S\>::IsPointer \=\= 0 PTS\<S\>::IsPointerToDataMember \=\= 0**  
**PTS\<S\*\>::IsPointer \=\= 1 PTS\<S\*\>::IsPointerToDataMember \=\=0**  
**PTS\<int S::\*\>::IsPointer \=\= 0 PTS\<int S::\*\>::IsPointerToDataMember \=\= 1**   
## Exemplo  
 Se você tiver uma classe de coleção de modelo que use qualquer tipo **T**, pode criar uma especialização parcial que usa qualquer tipo de ponteiro **T\***.  O código a seguir demonstra um modelo de classe de coleção `Bag` e uma especialização parcial para os tipos de ponteiro nos quais a coleção diferencia os tipos de ponteiro antes de copiá\-los na matriz.  Então, a coleção armazena os valores que forem apontados.  Com o modelo original, somente os próprios ponteiros seriam armazenados na coleção, deixando os dados vulneráveis a exclusão ou a alteração.  Nesta versão especial do ponteiro da coleção, o código para verificar se há um ponteiro nulo no método `add` é adicionado.  
  
```  
// partial_specialization_of_class_templates2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
// Original template collection class.  
template <class T> class Bag {  
   T* elem;  
   int size;  
   int max_size;  
  
public:  
   Bag() : elem(0), size(0), max_size(1) {}  
   void add(T t) {  
      T* tmp;  
      if (size + 1 >= max_size) {  
         max_size *= 2;  
         tmp = new T [max_size];  
         for (int i = 0; i < size; i++)  
            tmp[i] = elem[i];  
         tmp[size++] = t;  
         delete[] elem;  
         elem = tmp;  
      }  
      else  
         elem[size++] = t;  
   }  
  
   void print() {  
      for (int i = 0; i < size; i++)  
         cout << elem[i] << " ";  
      cout << endl;  
   }  
};  
  
// Template partial specialization for pointer types.  
// The collection has been modified to check for NULL   
// and store types pointed to.  
template <class T> class Bag<T*> {  
   T* elem;  
   int size;  
   int max_size;  
  
public:  
   Bag() : elem(0), size(0), max_size(1) {}  
   void add(T* t) {  
      T* tmp;  
      if (t == NULL) {   // Check for NULL  
         cout << "Null pointer!" << endl;  
         return;  
      }  
  
      if (size + 1 >= max_size) {  
         max_size *= 2;  
         tmp = new T [max_size];  
         for (int i = 0; i < size; i++)  
            tmp[i] = elem[i];  
         tmp[size++] = *t;  // Dereference  
         delete[] elem;  
         elem = tmp;  
      }  
      else  
         elem[size++] = *t; // Dereference  
   }  
  
   void print() {  
      for (int i = 0; i < size; i++)  
         cout << elem[i] << " ";  
      cout << endl;  
   }  
};  
  
int main() {  
   Bag<int> xi;  
   Bag<char> xc;  
   Bag<int*> xp; // Uses partial specialization for pointer types.  
  
   xi.add(10);  
   xi.add(9);  
   xi.add(8);  
   xi.print();  
  
   xc.add('a');  
   xc.add('b');  
   xc.add('c');  
   xc.print();  
  
   int i = 3, j = 87, *p = new int[2];  
   *p = 8;  
   *(p + 1) = 100;  
   xp.add(&i);  
   xp.add(&j);  
   xp.add(p);  
   xp.add(p + 1);  
   p = NULL;  
   xp.add(p);  
   xp.print();  
}  
```  
  
  **10 9 8**   
**a b c**   
**Null pointer\!**  
**3 87 8 100**    
## Exemplo  
 O exemplo a seguir define uma classe do modelo que usa pares de quaisquer dois tipos e depois define uma especialização parcial da classe do modelo especializada para que um dos tipos seja `int`.  A especialização define um método de classificação adicionais que implementa um tipo simples da bolha com base em inteiro.  
  
```  
// partial_specialization_of_class_templates3.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
template <class Key, class Value> class Dictionary {  
   Key* keys;  
   Value* values;  
   int size;  
   int max_size;  
public:  
   Dictionary(int initial_size) :  size(0) {  
      max_size = 1;  
      while (initial_size >= max_size)  
         max_size *= 2;  
      keys = new Key[max_size];  
      values = new Value[max_size];  
   }  
   void add(Key key, Value value) {  
      Key* tmpKey;  
      Value* tmpVal;  
      if (size + 1 >= max_size) {  
         max_size *= 2;  
         tmpKey = new Key [max_size];  
         tmpVal = new Value [max_size];  
         for (int i = 0; i < size; i++) {  
            tmpKey[i] = keys[i];  
            tmpVal[i] = values[i];  
         }  
         tmpKey[size] = key;  
         tmpVal[size] = value;  
         delete[] keys;  
         delete[] values;  
         keys = tmpKey;  
         values = tmpVal;  
      }  
      else {  
         keys[size] = key;  
         values[size] = value;  
      }  
      size++;  
   }  
  
   void print() {  
      for (int i = 0; i < size; i++)  
         cout << "{" << keys[i] << ", " << values[i] << "}" << endl;  
   }  
};  
  
// Template partial specialization: Key is specified to be int.  
template <class Value> class Dictionary<int, Value> {  
   int* keys;  
   Value* values;  
   int size;  
   int max_size;  
public:  
   Dictionary(int initial_size) :  size(0) {  
      max_size = 1;  
      while (initial_size >= max_size)  
         max_size *= 2;  
      keys = new int[max_size];  
      values = new Value[max_size];  
   }  
   void add(int key, Value value) {  
      int* tmpKey;  
      Value* tmpVal;  
      if (size + 1 >= max_size) {  
         max_size *= 2;  
         tmpKey = new int [max_size];  
         tmpVal = new Value [max_size];  
         for (int i = 0; i < size; i++) {  
            tmpKey[i] = keys[i];  
            tmpVal[i] = values[i];  
         }  
         tmpKey[size] = key;  
         tmpVal[size] = value;  
         delete[] keys;  
         delete[] values;  
         keys = tmpKey;  
         values = tmpVal;  
      }  
      else {  
         keys[size] = key;  
         values[size] = value;  
      }  
      size++;  
   }  
  
   void sort() {  
      // Sort method is defined.  
      int smallest = 0;  
      for (int i = 0; i < size - 1; i++) {  
         for (int j = i; j < size; j++) {  
            if (keys[j] < keys[smallest])  
               smallest = j;  
         }  
         swap(keys[i], keys[smallest]);  
         swap(values[i], values[smallest]);  
      }  
   }  
  
   void print() {  
      for (int i = 0; i < size; i++)  
         cout << "{" << keys[i] << ", " << values[i] << "}" << endl;  
   }  
};  
  
int main() {  
   Dictionary<char*, char*>* dict = new Dictionary<char*, char*>(10);  
   dict->print();  
   dict->add("apple", "fruit");  
   dict->add("banana", "fruit");  
   dict->add("dog", "animal");  
   dict->print();  
  
   Dictionary<int, char*>* dict_specialized = new Dictionary<int, char*>(10);  
   dict_specialized->print();  
   dict_specialized->add(100, "apple");  
   dict_specialized->add(101, "banana");  
   dict_specialized->add(103, "dog");  
   dict_specialized->add(89, "cat");  
   dict_specialized->print();  
   dict_specialized->sort();  
   cout << endl << "Sorted list:" << endl;  
   dict_specialized->print();  
}  
```  
  
  **{apple, fruit}**  
**{banana, fruit}**  
**{dog, animal}**  
**{100, apple}**  
**{101, banana}**  
**{103, dog}**  
**{89, cat}**  
**Lista classificada:**  
**{89, cat}**  
**{100, apple}**  
**{101, banana}**  
**{103, dog}**   
## Consulte também  
 [Especialização explícita de modelos de classe](../Topic/Explicit%20Specialization%20of%20Class%20Templates.md)