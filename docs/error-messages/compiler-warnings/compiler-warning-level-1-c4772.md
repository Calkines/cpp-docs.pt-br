---
title: Compilador aviso (nível 1) C4772
ms.date: 11/04/2016
f1_keywords:
- C4772
helpviewer_keywords:
- C4772
ms.assetid: dafe6fd8-9faf-41f5-9d66-a55838742c14
ms.openlocfilehash: 95243ab66d5d0296e1c316ff8dde7add75a030cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385453"
---
# <a name="compiler-warning-level-1-c4772"></a>Compilador aviso (nível 1) C4772

> \#import referenciou um tipo de uma biblioteca de tipos faltando; '*tipo ausente*' usado como um espaço reservado

Uma biblioteca de tipos foi referenciada com o [#import](../../preprocessor/hash-import-directive-cpp.md) diretiva. No entanto, a biblioteca de tipos continha uma referência a outra biblioteca de tipos que não foi referenciada com `#import`. Esse outro arquivo. tlb não foi encontrado pelo compilador.

Observe que o compilador não encontrará as bibliotecas de tipos em diretórios diferentes se você usar o [/I (diretórios de inclusão adicionais)](../../build/reference/i-additional-include-directories.md) opção de compilador para especificar os diretórios. Se você deseja que o compilador para encontrar as bibliotecas de tipos em diretórios diferentes, adicione esses diretórios para a variável de ambiente PATH.

Por padrão, esse aviso é emitido como um erro. Não podem ser suprimidos C4772 com /W0.

## <a name="example"></a>Exemplo

Essa é a primeira biblioteca de tipo necessária para reproduzir C4772.

```IDL
// c4772a.idl
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12b")]
library C4772aLib
{
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c100")]
   enum E_C4772a
   {
      one, two, three
   };
};
```

Esta é a segunda biblioteca de tipo necessária para reproduzir C4772.

```IDL
// c4772b.idl
// post-build command: del /f C4772a.tlb
// C4772a.tlb is available when c4772b.tlb is built
[uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12d")]
library C4772bLib
{
   importlib ("c4772a.tlb");
   [uuid("f87070ba-c6d9-405c-a8e4-8cd9ca25c12e")]
   struct S_C4772b
   {
      enum E_C4772a e;
   };
};
```

O exemplo a seguir gera C4772:

```cpp
// C4772.cpp
// assumes that C4772a.tlb is not available to the compiler
// #import "C4772a.tlb"
#import "C4772b.tlb"   // C4772 uncomment previous line to resolve
                       // and make sure c4772a.tlb is on disk
```