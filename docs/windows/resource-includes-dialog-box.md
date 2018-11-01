---
title: Recurso inclui a caixa de diálogo (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.resourceincludes
helpviewer_keywords:
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
ms.assetid: 659a54e6-e416-4045-8411-798730ff4ce3
ms.openlocfilehash: b0e7125e07deb965055da54126eb0933e64c0429
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625041"
---
# <a name="resource-includes-dialog-box-c"></a>Recurso inclui a caixa de diálogo (C++)

Você pode usar o **recurso inclui** caixa de diálogo em um projeto do C++ para modificar a disposição de trabalho normal do ambiente de armazenar todos os recursos no arquivo. rc de projeto e todas as [símbolos](../windows/symbols-resource-identifiers.md) em Resource. h.

Para abrir o **recurso inclui** do arquivo na caixa de diálogo, clique com botão direito um. rc [exibição de recurso](../windows/resource-view-window.md), em seguida, escolha **recurso inclui** no menu de atalho.

- **Arquivo de cabeçalho de símbolo**

   Permite que você altere o nome do arquivo de cabeçalho em que as definições de símbolo para o arquivo de recurso são armazenadas. Para obter mais informações, consulte [alterando os nomes dos arquivos de cabeçalho do símbolo](../windows/changing-the-names-of-symbol-header-files.md).

- **Diretivas de símbolo somente leitura**

   Permite que você inclua arquivos de cabeçalho que contêm símbolos que não devem ser modificados durante uma sessão de edição. Por exemplo, você pode incluir um arquivo de símbolo que é compartilhado entre vários projetos. Você também pode incluir arquivos. h do MFC. Para obter mais informações, consulte [incluindo compartilhados (somente leitura) ou símbolos calculados](../windows/including-shared-read-only-or-calculated-symbols.md).

- **Diretivas de tempo de compilação**

   Permite que você inclua arquivos de recursos que são criados e editados separadamente dos recursos em seu arquivo de recurso principal, contêm diretivas de tempo de compilação (como aquelas que incluem condicionalmente recursos) ou contêm recursos em um formato personalizado. Você também pode usar o **caixa de diretivas de tempo de compilação** para incluir arquivos de recursos padrão do MFC. Para obter mais informações, consulte [incluindo recursos em tempo de compilação](../windows/how-to-include-resources-at-compile-time.md).

> [!NOTE]
> Entradas nessas caixas de texto aparecem no arquivo. rc marcado pelo `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, e `TEXTINCLUDE 3` , respectivamente. Para obter mais informações, consulte [TN035: usando vários arquivos de recurso e arquivos de cabeçalho com o Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Depois de fazer alterações em seu arquivo de recurso usando o **inclui recursos** caixa de diálogo, você precisa fechar o arquivo. RC e, em seguida, reabri-lo para que as alterações entrem em vigor. Para obter mais informações, consulte [incluindo recursos em tempo de compilação](../windows/how-to-include-resources-at-compile-time.md).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte também

[Como especificar diretórios de inclusão para recursos](../windows/how-to-specify-include-directories-for-resources.md)<br/>
[Símbolos: identificadores de recursos](../windows/symbols-resource-identifiers.md)<br/>
[Arquivos de recurso](../windows/resource-files-visual-studio.md)<br/>
[Editores de recursos](../windows/resource-editors.md)