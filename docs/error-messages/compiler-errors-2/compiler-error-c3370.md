---
title: Erro do compilador C3370
ms.date: 11/04/2016
f1_keywords:
- C3370
helpviewer_keywords:
- C3370
ms.assetid: ee6d4c85-78fc-42b2-836e-5cc491a3b2ba
ms.openlocfilehash: 0dbc95fcb26354b0f963d1844ddd6a43783c532a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300603"
---
# <a name="compiler-error-c3370"></a>Erro do compilador C3370

'idl_module name': idl_module ainda não foi definido

Antes de usar [idl_module](../../windows/idl-module.md) para especificar um ponto de entrada em uma DLL, primeiro você deve usar `idl_module` para especificar o nome da DLL.

O exemplo a seguir gera C3370:

```
// C3370.cpp
[module(name=MyLibrary)];
// uncomment the following line to resolve the error
// [idl_module(name="name1", dllname=x.dll)];
[idl_module(name="name1"), entry(100)] // C3370
int f1();

int main()
{
}
```