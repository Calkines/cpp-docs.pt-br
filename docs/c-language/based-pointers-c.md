---
title: Ponteiros baseados (C)
ms.date: 11/04/2016
helpviewer_keywords:
- __based keyword [C]
- based pointers
- pointers, based
- based addressing
ms.assetid: b5446920-89e0-4e2f-91f3-1f2a769a08e8
ms.openlocfilehash: e5d8c529adfb92c9db1fdcc5a38f688853606d5d
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150773"
---
# <a name="based-pointers-c"></a>Ponteiros baseados (C)

**Seção específica da Microsoft**

[__based (referência do C++)](../cpp/based-pointers-cpp.md)

Para os compiladores C de 32 bits e de 64 bits da Microsoft, um ponteiro baseado é um deslocamento de 32 bits ou de 64 bits a partir de um base de ponteiro de 32 bits ou de 64 bits. O endereçamento baseado é útil para controlar as seções nas quais os objetos são alocados, diminuindo assim o tamanho do arquivo executável e aumentando a velocidade de execução. Em geral, o formato para especificar um ponteiro baseado é

> *type* **__based(** *base* **)** *declarator*

A variante "ponteiro de base" do endereçamento baseado permite especifica um ponteiro como base. O ponteiro baseado, portanto, é um deslocamento para a seção de memória que começa no início do ponteiro no qual ele é baseado. Os ponteiros com base em endereços de ponteiro são o único formato da palavra-chave `__based` válido em compilações de 32 bits e de 64 bits. Nessas compilações, ele são deslocamentos de 32 bits ou de 64 bits a partir de uma base de 32 bits ou de 64 bits.

Um uso para ponteiros baseados em ponteiros é para identificadores persistentes que contêm ponteiros. Uma lista vinculada que consiste em ponteiros baseados em um ponteiro pode ser salva em disco e depois ser recarregada em outro local na memória, com os ponteiros permanecendo válidos.

O exemplo a seguir mostra um ponteiro com base em um ponteiro.

```C
void *vpBuffer;

struct llist_t
{
    void __based( vpBuffer ) *vpData;
    struct llist_t __based( vpBuffer ) *llNext;
};
```

O ponteiro `vpBuffer` é atribuído ao endereço da memória alocada em algum momento posterior no programa. A lista vinculada é realocada em relação ao valor de `vpBuffer`.

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[Declaradores e declarações de variável](../c-language/declarators-and-variable-declarations.md)
