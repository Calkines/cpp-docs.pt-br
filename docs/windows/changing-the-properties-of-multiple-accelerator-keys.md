---
title: Alterando as propriedades de várias teclas de aceleração (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: b55c9bd6-b430-48bb-b942-0e6f21d7abf9
ms.openlocfilehash: 00c2bed34d70fa13161cbaa8968d967664c8bb0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668995"
---
# <a name="changing-the-properties-of-multiple-accelerator-keys-c"></a>Alterando as propriedades de várias teclas de aceleração (C++)

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Para alterar as propriedades de várias teclas de aceleração

1. Abra a tabela de aceleradores clicando duas vezes em seu ícone no [exibição de recurso](../windows/resource-view-window.md).

   > [!NOTE]
   > Se seu projeto já não contiver um arquivo. RC, consulte [criando um novo arquivo de Script de recurso](../windows/how-to-create-a-resource-script-file.md).

2. Selecione as teclas de aceleração que você deseja alterar, mantendo pressionada a **Ctrl** da chave que você clicar em cada um deles.

3. Vá para o [janela de propriedades](/visualstudio/ide/reference/properties-window) e digite os valores que você deseja que todos os aceleradores selecionados para compartilhar.

   > [!NOTE]
   > Cada valor de modificador aparece como uma propriedade booleana na **propriedades** janela. Se você alterar uma [modificador](../windows/accelerator-modifier-property.md) o valor de **propriedades** janela, a tabela de aceleradores trata o novo modificador como uma adição a qualquer modificador que anteriormente estavam lá. Por isso, se você definir quaisquer valores do modificador, você precisará definir todas elas para garantir que cada Acelerador compartilha os mesmos **modificador** configurações.

Para obter informações sobre como adicionar recursos a projetos gerenciados, consulte [recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index) na *guia do desenvolvedor do .NET Framework*. Para obter informações sobre como adicionar manualmente os arquivos de recursos a projetos gerenciados, acessar recursos, exibir recursos estáticos e atribuir cadeias de caracteres de recurso a propriedades, consulte [criando arquivos de recursos para aplicativos de área de trabalho](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obter informações sobre globalização e localização de recursos em aplicativos gerenciados, consulte [Globalizing e Localizando aplicativos do .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte também

[Editando tabelas de aceleradores](../windows/editing-accelerator-tables.md)<br/>
[Editor de aceleradores](../windows/accelerator-editor.md)