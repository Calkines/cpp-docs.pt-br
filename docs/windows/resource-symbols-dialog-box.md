---
title: Caixa de diálogo símbolos do recurso (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resourcesymbols
helpviewer_keywords:
- New Symbol dialog box [C++]
- Resource Symbols dialog box [C++]
- Change Symbol dialog box [C++]
ms.assetid: 9706cde3-1f48-4fcd-bedb-2b03b455e3c1
ms.openlocfilehash: 156b531bfcedca70c930d77773d3a308735735f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483506"
---
# <a name="resource-symbols-dialog-box-c"></a>Caixa de diálogo símbolos do recurso (C++)

O **símbolos de recurso** caixa de diálogo C++ permite que você adicione novos símbolos de recurso, altere os símbolos que são exibidos, ou pular para o local no código-fonte em que um símbolo está em uso.

- **Nome**

   Exibe o nome do símbolo. Para obter mais informações, consulte [restrições de nome de símbolo](../windows/symbol-name-restrictions.md).

- **Valor**

   Exibe o valor numérico do símbolo. Para obter mais informações, consulte [restrições de valor de símbolo](../windows/symbol-value-restrictions.md).

- **Em uso**

   Quando selecionado, especifica que o símbolo está sendo usado por um ou mais recursos. Um ou mais recursos são listados na usado pela caixa.

- **Mostrar símbolos somente leitura**

   Quando selecionado, exibe recursos somente leitura. Por padrão, o **símbolo de recurso** caixa de diálogo exibe somente os recursos pode ser modificados no arquivo de script de recurso, mas com essa opção selecionada, os recursos modificáveis aparecem em negrito e os recursos de somente leitura são exibidos em texto sem formatação.

- **Usado por**

   Exibe um ou mais recursos usando o símbolo selecionado na lista de símbolos. Para mover para o editor para um determinado recurso, selecione o recurso nas **usado por** caixa e clique em **Exibir uso**. Para obter mais informações, consulte [abrindo o Editor de recursos para um símbolo dado](../windows/opening-the-resource-editor-for-a-given-symbol.md).

- **Novo**

   Abre o **novo símbolo** caixa de diálogo que permite que você defina o nome e, se necessário, um valor para um novo identificador simbólico do recurso. Para obter mais informações, consulte [criando novos símbolos](../windows/creating-new-symbols.md).

- **Alteração**

   Abre o **alterar símbolo** caixa de diálogo que permite que você altere o nome ou o valor de um símbolo. Se o símbolo for para um controle ou recurso em uso, o símbolo pode ser alterado somente de editor de recursos correspondente. Para obter mais informações, consulte [alterando símbolos não atribuídos](../windows/changing-unassigned-symbols.md).

- **Exibir uso**

   Abre o recurso que contém o símbolo no editor de recurso correspondente. Para obter mais informações, consulte [abrindo o Editor de recursos para um símbolo dado](../windows/opening-the-resource-editor-for-a-given-symbol.md).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte também

[Exibindo símbolos de recurso](../windows/viewing-resource-symbols.md)