---
title: Compilador aviso (nível 3) C4359
ms.date: 11/04/2016
f1_keywords:
- C4359
helpviewer_keywords:
- C4359
ms.assetid: d8fe993c-ef82-45a0-a43d-c29f9d1bacdb
ms.openlocfilehash: 3856c50aabce497f28a179b30346b30371986e51
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402002"
---
# <a name="compiler-warning-level-3-c4359"></a>Compilador aviso (nível 3) C4359

'type': alinhamento real (8) é maior que o valor especificado em __declspec(align())

O alinhamento especificado para um tipo é menor que o alinhamento do tipo de um de seus membros de dados.  Para obter mais informações, consulte [alinhar](../../cpp/align-cpp.md).

## <a name="example"></a>Exemplo

O exemplo a seguir gera C4359.

```
// C4359.cpp
// compile with: /W3 /c
struct __declspec(align(8)) C8 { __int64 i; };
struct __declspec(align(4)) C4  { C8 m8; };   // C4359
struct __declspec(align(8)) C8_b  { C8 m8; };   // OK
struct __declspec(align(16)) C16  { C8 m8; };   // OK
```