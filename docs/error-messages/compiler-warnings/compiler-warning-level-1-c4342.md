---
title: "Compilador (nível 1) de aviso C4342 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4342
dev_langs:
- C++
helpviewer_keywords:
- C4342
ms.assetid: 47d4d5ab-069f-4cdc-98c3-10d649577a37
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: c4a2afbc3ced186b0db63b22b3cc5c2b27204c71
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4342"></a>Compilador C4342 de aviso (nível 1)
alteração de comportamento: '*função*' chamado, mas um operador membro foi chamado em versões anteriores  
  
 Nas versões do Visual C++ antes do Visual Studio 2002, um membro foi chamado, mas esse comportamento foi alterado e o compilador agora localiza a melhor correspondência no escopo de namespace.  
  
 Se um operador de membro for encontrado, o compilador anteriormente não consideram qualquer namespace operadores de escopo. Se houver uma correspondência melhor no escopo do namespace, o compilador atual corretamente chamá-lo, enquanto que os compiladores anteriores não considerá-la.  
  
 Esse aviso deve ser desabilitado depois que a porta com êxito seu código para a versão atual.  O compilador pode resultar em falsos positivos, gerar esse aviso de código onde não há nenhuma alteração de comportamento.  
  
 Esse aviso é desativada por padrão. Para obter mais informações, consulte [compilador avisos que está desativado por padrão](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 O exemplo a seguir gera C4342:  
  
```cpp  
// C4342.cpp  
// compile with: /EHsc /W1  
#include <fstream>  
#pragma warning(default: 4342)  
using namespace std;  
struct X : public ofstream {  
   X();  
};  
  
X::X() {  
   open( "ofs_bug_ev.txt." );  
   if ( is_open() ) {  
      *this << "Text" << "<-should be text" << endl;   // C4342  
      *this << ' ' << "<-should be space symbol" << endl;   // C4342  
   }  
}  
  
int main() {  
   X b;  
   b << "Text" << "<-should be text" << endl;  
   b << ' ' << "<-should be space symbol" << endl;  
}  
```