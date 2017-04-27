---
title: "Operador reinterpret_cast | Microsoft Docs"
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
  - "reinterpret_cast"
  - "reinterpret_cast_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Palavra-chave reinterpret_cast [C++]"
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operador reinterpret_cast
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Permite que qualquer ponteiro seja convertido em outro tipo de ponteiro.  Também permite que qualquer tipo integral seja convertido em qualquer tipo de ponteiro e vice\-versa.  
  
## Sintaxe  
  
```  
reinterpret_cast < type-id > ( expression )  
```  
  
## Comentários  
 O uso incorreto do operador `reinterpret_cast` pode ser facilmente inseguros.  A menos que a conversão desejada seja inerentemente de nível baixo, você deve usar um dos outros operadores de conversão.  
  
 O operador `reinterpret_cast` pode ser usado para conversões como `char*` a `int*`, ou `One_class*` a `Unrelated_class*`, que é inerentemente inseguro.  
  
 O resultado de `reinterpret_cast` não pode ser usado com segurança para algo diferente de ser convertido de volta ao seu tipo original.  Outros usos são, na melhor das hipóteses, não portáteis.  
  
 O operador `reinterpret_cast` não pode eliminar os atributos **const**, `volatile` ou **\_\_unaligned**.  Consulte [Operador const\_cast](../Topic/const_cast%20Operator.md) para obter informações sobre como remover esses atributos.  
  
 O operador `reinterpret_cast` converte um valor de ponteiro nulo em valor de ponteiro nulo do tipo de destino.  
  
 Um uso prático de `reinterpret_cast` está em uma função de hash, que mapeia um valor a um índice de forma que dois valores distintos raramente terminam acima com o mesmo índice.  
  
```  
#include <iostream>  
using namespace std;  
  
// Returns a hash code based on an address  
unsigned short Hash( void *p ) {  
   unsigned int val = reinterpret_cast<unsigned int>( p );  
   return ( unsigned short )( val ^ (val >> 16));  
}  
  
using namespace std;  
int main() {  
   int a[20];  
   for ( int i = 0; i < 20; i++ )  
      cout << Hash( a + i ) << endl;  
}  
  
Output:   
64641  
64645  
64889  
64893  
64881  
64885  
64873  
64877  
64865  
64869  
64857  
64861  
64849  
64853  
64841  
64845  
64833  
64837  
64825  
64829  
```  
  
 `reinterpret_cast` permite que o ponteiro é tratado como um tipo integral.  O resultado de bit é deslocado e recebe XOR para gerar um índice exclusivo \(exclusivo para um alto nível de probabilidade\).  O índice é truncado em seguida por uma conversão padrão do estilo C para o tipo de retorno de função.  
  
## Consulte também  
 [Operadores de conversão](../cpp/casting-operators.md)   
 [Palavras\-chave C\+\+](../cpp/keywords-cpp.md)