---
title: Definições e declarações (C++)
ms.date: 11/04/2016
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
ms.openlocfilehash: 987e27bdf35eba7d9380fc546c15b93b3179333b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628937"
---
# <a name="definitions-and-declarations-c"></a>Definições e declarações (C++)

**Seção específica da Microsoft**

A interface da DLL refere-se a todos os itens (funções e dados) que são conhecidos a serem exportados por algum programa no sistema; ou seja, todos os itens que são declarados como **dllimport** ou **dllexport**. Todas as declarações incluídas na interface da DLL devem especificar o **dllimport** ou **dllexport** atributo. No entanto, a definição deve especificar somente o **dllexport** atributo. Por exemplo, a definição de função a seguir gera um erro de compilador:

```
__declspec( dllimport ) int func() {   // Error; dllimport
                                       // prohibited on definition.
   return 1;
}
```

Este código também gera um erro:

```
__declspec( dllimport ) int i = 10;  // Error; this is a definition.
```

No entanto, esta é uma sintaxe correta:

```
__declspec( dllexport ) int i = 10;  // Okay--export definition
```

O uso de **dllexport** implica uma definição, enquanto **dllimport** implica uma declaração. Você deve usar o **extern** palavra-chave with **dllexport** para forçar uma declaração; caso contrário, uma definição é implícita. Assim, os seguintes exemplos estão corretos:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllExport int k; // These are both correct and imply a
DllImport int j;        // declaration.
```

Os exemplos a seguir esclarecem o que foi dito acima:

```
static __declspec( dllimport ) int l; // Error; not declared extern.

void func() {
    static __declspec( dllimport ) int s;  // Error; not declared
                                           // extern.
    __declspec( dllimport ) int m;         // Okay; this is a
                                           // declaration.
    __declspec( dllexport ) int n;         // Error; implies external
                                           // definition in local scope.
    extern __declspec( dllimport ) int i;  // Okay; this is a
                                           // declaration.
    extern __declspec( dllexport ) int k;  // Okay; extern implies
                                           // declaration.
    __declspec( dllexport ) int x = 5;     // Error; implies external
                                           // definition in local scope.
}
```

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[dllexport, dllimport](../cpp/dllexport-dllimport.md)