---
title: 'Símbolos: Identificadores de recursos (C++)'
ms.date: 11/04/2016
f1_keywords:
- vc.editors.symbol.identifiers
helpviewer_keywords:
- symbols [C++], resource identifiers
- symbols [C++], creating
- resource symbols
- symbols [C++], editing
- resource editors [C++], resource symbols
ms.assetid: 8fccc09a-0237-4a65-b9c4-57d60c59e324
ms.openlocfilehash: abe6297d74df4941328d3e606fb3b0f646d36265
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50529994"
---
# <a name="symbols-resource-identifiers-c"></a>Símbolos: Identificadores de recursos (C++)

Um símbolo é um identificador de recurso (ID) que consiste em duas partes: uma cadeia de texto (nome de símbolo) mapeada para um valor inteiro (valor de símbolo). Por exemplo:

```
IDC_EDITNAME = 5100
```

Nomes de símbolos são geralmente denominados identificadores.

Símbolos fornecem uma maneira descritiva de fazer referência a recursos e objetos de interface do usuário, no seu código-fonte e enquanto estiver trabalhando com eles nos editores de recursos. Você pode exibir e manipular símbolos em um local conveniente usando o [caixa de diálogo símbolos de recurso](../windows/viewing-resource-symbols.md).

Quando você cria um novo recurso ou objeto de recurso, o [editores de recursos](../windows/resource-editors.md) forneça um nome padrão para o recurso, por exemplo, `IDC_RADIO1`e atribuir um valor a ela. A definição de mais valor name é armazenada no arquivo Resource. h.

> [!NOTE]
> Quando você estiver copiando recursos ou objetos de recurso de um arquivo. RC para outro, o Visual C++ pode alterar o recurso transferido símbolo valor, ou o nome do símbolo e, para evitar conflitos com nomes de símbolos ou os valores no arquivo existente.

À medida que seu aplicativo crescer em tamanho e a sofisticação e aumenta seu número de recursos e símbolos. Grande número de símbolos espalhados em vários arquivos de rastreamento pode ser difícil. O [caixa de diálogo símbolos de recurso](../windows/resource-symbols-dialog-box.md) simplifica o gerenciamento de símbolo, oferecendo uma ferramenta central por meio do qual você pode:

- [Símbolos de recurso do modo de exibição](../windows/viewing-resource-symbols.md)

- [Criar novos símbolos](../windows/creating-new-symbols.md)

- [Alterar os símbolos não atribuídos](../windows/changing-unassigned-symbols.md)

- [Excluir símbolos não atribuídos](../windows/deleting-unassigned-symbols.md)

- [Abra o Editor de recurso para um determinado símbolo](../windows/opening-the-resource-editor-for-a-given-symbol.md)

- [Alterar um símbolo ou um nome de símbolo (ID)](../windows/changing-a-symbol-or-symbol-name-id.md)

- [Alterar um valor numérico de símbolo](../windows/changing-a-symbol-s-numeric-value.md)

- [Alterar os nomes dos arquivos de cabeçalho de símbolo](../windows/changing-the-names-of-symbol-header-files.md)

- [Incluir compartilhados (somente leitura) ou calculados símbolos](../windows/including-shared-read-only-or-calculated-symbols.md)

- [Exibir IDs de símbolos predefinidos](../windows/predefined-symbol-ids.md)

Para obter informações sobre como adicionar recursos a projetos gerenciados, consulte [recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index) na *guia do desenvolvedor do .NET Framework*. Para obter informações sobre como adicionar manualmente os arquivos de recursos a projetos gerenciados, acessar recursos, exibir recursos estáticos e atribuir cadeias de caracteres de recurso a propriedades, consulte [criando arquivos de recursos para aplicativos de área de trabalho](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obter informações sobre globalização e localização de recursos em aplicativos gerenciados, consulte [Globalizing e Localizando aplicativos do .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte também

[Como pesquisar símbolos em recursos](../windows/how-to-search-for-symbols-in-resources.md)<br/>
[Editores de recursos](../windows/resource-editors.md)<br/>
[Arquivos de recurso](../windows/resource-files-visual-studio.md)