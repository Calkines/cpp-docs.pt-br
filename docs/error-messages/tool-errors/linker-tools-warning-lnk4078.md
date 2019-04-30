---
title: Aviso LNK4078 (Ferramentas de Vinculador)
ms.date: 11/04/2016
f1_keywords:
- LNK4078
helpviewer_keywords:
- LNK4078
ms.assetid: 5a16796d-6caf-42d9-8f65-b042843eafb8
ms.openlocfilehash: d20eb0523ffebe9229d05b6316772259661f6020
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399923"
---
# <a name="linker-tools-warning-lnk4078"></a>Aviso LNK4078 (Ferramentas de Vinculador)

várias seções de 'nome da seção' encontradas com diferentes atributos

O LINK localizado dois ou mais seções que têm o mesmo nome, mas diferentes atributos.

Esse aviso pode ser causado por um arquivo de biblioteca ou exportações de importação que foi criado por uma versão anterior do LINK ou LIB.

Recrie o arquivo e vincular novamente.

## <a name="example"></a>Exemplo

LNK4078 também pode ser causado por uma alteração significativa: a seção nomeada pelo [init_seg](../../preprocessor/init-seg.md) em x86 foi de leitura/gravação, agora é somente leitura.

O exemplo a seguir gera LNK4078.

```
// LNK4078.cpp
// compile with: /W1
// LNK4078 expected
#include <stdio.h>
#pragma warning(disable : 4075)
typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors to call
PF pfx[200];   // pointers to destructors.

struct A { A() {} };

int myexit (PF pf) { return 0; }

#pragma section(".mine$a", read, write)
// try the following line instead
// #pragma section(".mine$a", read)
__declspec(allocate(".mine$a")) int ii = 1;

#pragma section(".mine$z", read, write)
// try the following line instead
// #pragma section(".mine$z", read)
__declspec(allocate(".mine$z")) int i = 1;

#pragma data_seg()
#pragma init_seg(".mine$m", myexit)
A bbbb;
A cccc;
int main() {}
```