---
title: Compilador aviso (nível 1) C4930
ms.date: 11/04/2016
f1_keywords:
- C4930
helpviewer_keywords:
- C4930
ms.assetid: 89a206c9-c536-4186-8e81-1cde3e7f4f5b
ms.openlocfilehash: 15cd1ed61c747e2c9168b9fc0fee03dca8403a24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242780"
---
# <a name="compiler-warning-level-1-c4930"></a>Compilador aviso (nível 1) C4930

'protótipo': função prototipada não chamada (era uma definição de variável se destina?)

O compilador detectou um protótipo de função não utilizada. Se o protótipo foi pretendido como uma declaração de variável, remova os parênteses de abertura/fechamento.

O exemplo a seguir gera C4930:

```
// C4930.cpp
// compile with: /W1
class Lock {
public:
   int i;
};

void f() {
   Lock theLock();   // C4930
   // try the following line instead
   // Lock theLock;
}

int main() {
}
```

C4930 também pode ocorrer quando o compilador não pode distinguir entre uma declaração de protótipo de função e uma chamada de função.

O exemplo a seguir gera C4930:

```
// C4930b.cpp
// compile with: /EHsc /W1

class BooleanException
{
   bool _result;

public:
   BooleanException(bool result)
      : _result(result)
   {
   }

   bool GetResult() const
   {
      return _result;
   }
};

template<class T = BooleanException>
class IfFailedThrow
{
public:
   IfFailedThrow(bool result)
   {
      if (!result)
      {
         throw T(result);
      }
   }
};

class MyClass
{
public:
   bool MyFunc()
   {
      try
      {
         IfFailedThrow<>(MyMethod()); // C4930

         // try one of the following lines instead
         // IfFailedThrow<> ift(MyMethod());
         // IfFailedThrow<>(this->MyMethod());
         // IfFailedThrow<>((*this).MyMethod());

         return true;
      }
      catch (BooleanException e)
      {
         return e.GetResult();
      }
   }

private:
   bool MyMethod()
   {
      return true;
   }
};

int main()
{
   MyClass myClass;
   myClass.MyFunc();
}
```

No exemplo acima, o resultado de um método que assuma zero argumentos é passado como um argumento para o construtor de uma variável de classe local sem nome. A chamada pode ser sem ambiguidade graças nomear a variável local ou prefixando a chamada de método com uma instância do objeto juntamente com o operador de ponteiro para membro apropriado.