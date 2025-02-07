---
title: Construção de objetos em um e dois estágios
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: 871db7abd2682d557bf2e80e9cb97624f0dc53a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160153"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Construção de objetos em um e dois estágios

Você pode escolher entre duas técnicas para criar objetos gráficos, como canetas e pincéis:

- *Construção de um estágio*: Criar e inicializar o objeto em um estágio, tudo com o construtor.

- *Construção de dois estágios*: Criar e inicializar o objeto em duas fases separadas. O construtor cria o objeto e inicializa-o uma função de inicialização.

Construção de dois estágios sempre é mais segura. Na construção de um estágio, o construtor pode lançar uma exceção se você fornecer argumentos incorretos ou falha de alocação de memória. Esse problema é evitado com a construção de dois estágios, embora seja necessário que verificar se há falha. Em ambos os casos, destruir o objeto é o mesmo processo.

> [!NOTE]
>  Essas técnicas se aplicam à criação de quaisquer objetos, os objetos gráficos não apenas.

## <a name="example-of-both-construction-techniques"></a>Exemplo de ambas as técnicas de construção

O exemplo a seguir breve mostra ambos os métodos de construção de um objeto pen:

[!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>O que você deseja saber mais sobre

- [Objetos gráficos](../mfc/graphic-objects.md)

- [Selecionando um objeto gráfico em um contexto de dispositivo](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Contextos de dispositivo](../mfc/device-contexts.md)

- [Desenhando em uma exibição](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>Consulte também

[Objetos gráficos](../mfc/graphic-objects.md)
