---
title: Implementar Virtuais Puros
ms.date: 11/16/2016
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
ms.openlocfilehash: e693fdc17057d3800053bf5a7bad64ec441bcc3e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614897"
---
# <a name="implement-pure-virtuals"></a>Implementar Virtuais Puros
**O quê:** permite gerar imediatamente o código necessário para implementar todos os métodos virtuais puros em uma classe.

**Quando:** você deseja herdar de uma classe com funções virtuais puras.

**Por quê:** você pode implementar todas as funções virtuais puras manualmente uma por uma; no entanto, esse recurso gerará todas as assinaturas de método automaticamente.

**Como:**

1. Coloque o cursor de texto ou do mouse sobre a classe na qual deseja implementar as funções virtuais puras da classe base.

   ![Código realçado](images/virtuals_highlight.png)

1. Depois, siga um destes procedimentos:
   * **Teclado**
     * Pressione **Ctrl +.** para disparar o menu **Ações Rápidas e Refatorações** e selecione **Implementar todos os Virtuais Puros para a classe '*ClassName*'** no menu de contexto, em que *ClassName* é o nome da classe selecionada.
   * **Mouse**
     * Clique com o botão direito do mouse, selecione o menu **Ações Rápidas e Refatorações** e selecione **Implementar todos os Virtuais Puros para a classe '*ClassName*'** no menu de contexto, em que *ClassName* é o nome da classe selecionada.

1. As assinaturas de método virtuais puras serão criadas automaticamente, prontas para serem implementadas.

   ![Resultado de Implementar Virtuais Puros](images/virtuals_result.png)
