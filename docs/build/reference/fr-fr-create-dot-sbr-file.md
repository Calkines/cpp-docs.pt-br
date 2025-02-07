---
title: /FR, /Fr (criar arquivo .Sbr)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BrowseInformation
- VC.Project.VCCLCompilerTool.BrowseInformation
- /fr
- VC.Project.VCCLCompilerTool.BrowseInformationFile
- VC.Project.VCCLWCECompilerTool.BrowseInformationFile
helpviewer_keywords:
- /FR compiler option [C++]
- -FR compiler option [C++]
- FR compiler option [C++]
- symbolic browser information
ms.assetid: 3fd8f88b-3924-4feb-9393-287036a28896
ms.openlocfilehash: 73642baba77a62cac531ae7b2842ec9953b338ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292790"
---
# <a name="fr-fr-create-sbr-file"></a>/FR, /Fr (criar arquivo .Sbr)

Cria arquivos. SBR.

## <a name="syntax"></a>Sintaxe

```
/FR[pathname[\filename]]
/Fr[pathname[\filename]]
```

## <a name="remarks"></a>Comentários

> [!WARNING]
> Embora BSCMAKE ainda está instalado com o Visual Studio, ele não é mais usado pelo IDE. Desde o Visual Studio 2008, as informações de símbolo e procura são armazenadas automaticamente em um arquivo. sdf de SQL Server na pasta da solução.

Durante o processo de compilação, a Microsoft procurar informações de arquivo manutenção Utility (BSCMAKE) usa esses arquivos para criar um. Arquivo BSC, que é usado para exibir informações de procura.

**/FR** cria um arquivo. SBR com informações simbólicas completas.

**/FR** cria um arquivo. SBR sem informações em variáveis locais.

Se você não especificar `filename`, o arquivo. SBR obtém o mesmo nome base que o arquivo de origem.

**/FR** foi preterida; use **/FR** em vez disso. Para obter mais informações, consulte preterido e opções do compilador removido no [opções de compilador listadas por categoria](compiler-options-listed-by-category.md).

> [!NOTE]
>  Não altere a extensão. SBR. BSCMAKE requer os arquivos intermediários para ter essa extensão.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio

1. Abra a caixa de diálogo **Páginas de Propriedades** do projeto. Para obter detalhes, consulte [propriedades de compilador e de build definida C++ no Visual Studio](../working-with-project-properties.md).

1. No painel de navegação, escolha o **C/C++**, **procurar informações** página de propriedades.

1. Modificar a **procure o arquivo de informações** ou **permitem procurar informações** propriedade.

### <a name="to-set-this-compiler-option-programmatically"></a>Para definir essa opção do compilador via programação

- Consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> e <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>.

## <a name="see-also"></a>Consulte também

[Opções do arquivo de saída (/F)](output-file-f-options.md)<br/>
[Opções do compilador MSVC](compiler-options.md)<br/>
[Sintaxe da linha de comando do compilador MSVC](compiler-command-line-syntax.md)<br/>
[Especificando o nome de caminho](specifying-the-pathname.md)
