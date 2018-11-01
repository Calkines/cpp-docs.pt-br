---
title: 'Como: copiar recursos (C++)'
ms.date: 11/04/2016
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
ms.openlocfilehash: 6baa53f8a047a8a7fc7540234dc0be2e08476d9f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545074"
---
# <a name="how-to-copy-resources-c"></a>Como: copiar recursos (C++)

Você pode copiar recursos de um arquivo para outro sem alterá-los ou pode [alterar o idioma ou a condição de um recurso ao copiá-lo](../windows/how-to-change-the-language-or-condition-of-a-resource-while-copying.md).

Você pode facilmente copiar recursos de um recurso existente ou arquivo executável para o arquivo de recurso atual. Para fazer isso, você abra ambos os arquivos que contêm recursos ao mesmo tempo e arrasta itens de um arquivo para outro ou copia e cola entre os dois arquivos. Esse método funciona para arquivos de script (. rc) do recurso e arquivos de modelo (. rct) de recursos, bem como arquivos executáveis (.exe).

> [!NOTE]
> O Visual C++ inclui arquivos de recurso de exemplo que você pode usar em seu próprio aplicativo. Para obter mais informações, consulte [clip-art: recursos comuns](https://github.com/Microsoft/VCSamples).

Você pode usar o método de arrastar e soltar entre arquivos. rc que estão abertos [fora do projeto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Copiar recursos entre os arquivos usando o método de arrastar e soltar

1. Abra ambos os arquivos de recurso autônomos (para obter mais informações, consulte [exibir recursos em um arquivo externa de um projeto de. rc](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Por exemplo, abra Source1.rc e Source2.rc.

2. Dentro do primeiro arquivo. RC, clique no recurso que você deseja copiar. Por exemplo, na `Source1.rc`, clique em **IDD_DIALOG1**.

3. Mantenha a tecla CTRL pressionada e arraste o recurso para o segundo arquivo. rc. Por exemplo, arrastar **IDD_DIALOG1** partir `Source1.rc` para `Source2.rc`.

   > [!NOTE]
   > Arrastando o recurso sem manter pressionado a **Ctrl** tecla move o recurso em vez de copiá-lo.

### <a name="to-copy-resources-using-copy-and-paste"></a>Para copiar recursos usando copiar e colar

1. Abra ambos os arquivos de recurso autônomos (para obter mais informações, consulte [exibir recursos em um arquivo externa de um projeto de. rc](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Por exemplo, Source1.rc e Source2.rc.

2. No arquivo de origem do qual você deseja copiar um recurso (por exemplo, `Source1.rc`), um recurso com o botão direito e escolha **cópia** no menu de atalho.

3. Clique no arquivo de recurso no qual você deseja colar o recurso (por exemplo, `Source2.rc`). Escolher **colar** no menu de atalho.

   > [!NOTE]
   > Não é possível arraste e solte, copiar, recortar ou colar entre os arquivos de recurso no projeto (**exibição de recurso**) e arquivos. rc autônomo (aquelas abertos em janelas de documento). Você pode fazer isso em versões anteriores do produto.

   > [!NOTE]
   > Para evitar conflitos com nomes de símbolos ou os valores no arquivo existente, Visual C++ pode alterar o valor de símbolo do recurso transferidos ou o nome do símbolo e o valor quando você os copia para o novo arquivo.

Para obter informações sobre como adicionar recursos a projetos gerenciados, consulte [recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index) na *guia do desenvolvedor do .NET Framework*. Para obter informações sobre como adicionar manualmente os arquivos de recursos a projetos gerenciados, acessar recursos, exibir recursos estáticos e atribuir cadeias de caracteres de recurso a propriedades, consulte [criando arquivos de recursos para aplicativos de área de trabalho](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obter informações sobre globalização e localização de recursos em aplicativos gerenciados, consulte [Globalizing e Localizando aplicativos do .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte também

[Como abrir um arquivo de script de recurso fora de um projeto (autônomo)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)<br/>
[Arquivos de recurso](../windows/resource-files-visual-studio.md)<br/>
[Editores de recursos](../windows/resource-editors.md)