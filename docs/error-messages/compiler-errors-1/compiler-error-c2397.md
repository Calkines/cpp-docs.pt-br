---
title: C2397 de erro do compilador | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2397
dev_langs:
- C++
ms.assetid: b418cf5a-d50d-4a6c-98a7-994ae35046d1
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 31f2b548fd13bc7702d44ef4a6d5dc5c34a5eb3c
ms.lasthandoff: 02/25/2017

---
# <a name="compiler-error-c2397"></a>C2397 de erro do compilador
conversão de 'type_1' em 'type_2' requer uma conversão de restrição  
  
 Uma conversão implícita de restrição foi encontrada ao usar inicialização uniforme.  
  
 A linguagem C permite conversões de estreitamento implícitas na inicialização e atribuições e C++ segue o naipe, embora narrowing inesperada é uma causa de muitos erros de código. Para tornar o código mais seguro, o C++ padrão exige que uma mensagem de diagnóstico quando ocorre uma conversão de restrição em uma lista de inicialização. No Visual C++, o diagnóstico é C2397 de erro do compilador ao usar o início de sintaxe com suporte de inicialização uniforme no Visual Studio 2015. O compilador gera [C4838 de aviso do compilador (nível 1)](../../error-messages/compiler-warnings/compiler-warning-level-1-c4838.md) ao usar a sintaxe de inicialização de agregação com suporte pelo Visual Studio 2013 ou lista.  
  
 Uma conversão de restrição pode ser okey quando você conhece que o possível intervalo de valores convertidos pode se ajustar no destino. Nesse caso, você sabe mais do que o compilador faz. Se você fizer uma conversão de restrição intencionalmente, fazer suas intenções explícita usando uma conversão estática. Caso contrário, essa mensagem de erro indica quase sempre que tem um bug no código. Você pode corrigi-lo, assegurando-se de que os objetos que você inicializar têm tipos que são grandes o suficiente para lidar com as entradas.  
  
 O exemplo a seguir gera C2397 e mostra uma maneira de corrigir:  
  
```  
// C2397.cpp -- C++ narrowing conversion diagnostics  
// Compile by using: cl /EHsc C2397.cpp  
#include <vector>   
  
struct S1 {  
    int m1;  
    double m2, m3;  
};  
  
void function_C2397(double d1) {  
    char c1 { 127 };          // OK  
    char c2 { 513 };          // error C2397  
  
    std::vector<S1> vS1;  
    vS1.push_back({ d1, 2, 3 }); // error C2397  
  
    // Possible fix if you know d1 always fits in an int  
    vS1.push_back({ static_cast<int>(d1), 2, 3 });   
}  
```