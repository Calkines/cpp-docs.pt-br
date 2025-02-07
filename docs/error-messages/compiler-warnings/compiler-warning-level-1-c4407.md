---
title: Compilador aviso (nível 1) C4407
ms.date: 11/04/2016
f1_keywords:
- C4407
helpviewer_keywords:
- C4407
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
ms.openlocfilehash: 2e47e293b650f64d2a6be91a837cc4195e073e8f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447750"
---
# <a name="compiler-warning-level-1-c4407"></a>Compilador aviso (nível 1) C4407

conversão entre diferente ponteiro para representações de membro, compilador pode gerar código incorreto

Foi detectada uma conversão incorreta.

C4407 pode ser gerado devido ao trabalho de conformidade do compilador que foi feito no Visual Studio 2005. Ponteiro para membro agora requer um nome qualificado e o operador address-of (&).

C4407 pode ocorrer se você converter entre vários herança ponteiro-para-membro a um herança única ponteiro para membro. Às vezes, isso pode funcionar, mas, às vezes, ele não é possível porque a representação de ponteiro para membro de herança única não conter informações suficientes. Compilar com o **/vmm** podem ajudar a (para obter mais informações, consulte [/vmm, /vms, /vmv (representação de finalidade geral)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)). Você também pode tentar reorganizar suas classes base; o compilador está detectando uma perda de informações na conversão porque uma classe base está em um deslocamento diferente de zero de derivada.

O exemplo a seguir gera C4407:

```
// C4407.cpp
// compile with: /W1 /c
struct C1 {};
struct C2 {};
struct C3 : C1, C2 {};

typedef void(C3::*PMF_C3)();
typedef void(C2::*PMF_C2)();

PMF_C2 f1(PMF_C3 pmf) {
   return (PMF_C2)pmf;   // C4407, change type of cast,
   // or reverse base class inheritance of C3 (i.e. : C2, C1)
}
```