---
title: /I (diretórios de inclusão adicionais)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.AdditionalIncludeDirectories
- VC.Project.VCCLCompilerTool.AdditionalIncludeDirectories
- /I
- VC.Project.VCNMakeTool.IncludeSearchPath
helpviewer_keywords:
- /I compiler option [C++]
- Additional Include Directories compiler option
- I compiler option [C++]
- -I compiler option [C++]
- set include directories
- include directories, compiler option [C++]
ms.assetid: 3e9add2a-5ed8-4d15-ad79-5b411e313a49
ms.openlocfilehash: b922a4472246bb13bfed4022f2f85061c5d1217b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563859"
---
# <a name="i-additional-include-directories"></a>/I (diretórios de inclusão adicionais)

Adiciona um diretório à lista de diretórios procurados para os arquivos de inclusão.

## <a name="syntax"></a>Sintaxe

```
/I[ ]directory
```

## <a name="arguments"></a>Arguments

*Diretório*<br/>
O diretório a ser adicionado à lista de diretórios pesquisados pelos arquivos de inclusão.

## <a name="remarks"></a>Comentários

Para adicionar mais de um diretório, use esta opção mais de uma vez. Diretórios são pesquisados até que o arquivo de inclusão especificado for encontrado.

Você pode usar essa opção com a ignorar demarcadores de inclusão padrão ([/X (ignorar demarcadores de inclusão padrão)](../../build/reference/x-ignore-standard-include-paths.md)) opção.

O compilador pesquisa de diretórios na seguinte ordem:

1. Diretórios que contém o arquivo de origem.

1. Diretórios especificados com o **/I** opção, na ordem em que o CL encontrá-las.

1. Diretórios especificados na **INCLUDE** variável de ambiente.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio

1. Abra a caixa de diálogo **Páginas de Propriedades** do projeto. Para obter detalhes, confira [Trabalhando com propriedades do projeto](../../ide/working-with-project-properties.md).

1. Clique o **C/C++** pasta.

1. Clique o **geral** página de propriedades.

1. Modificar a **diretórios de inclusão adicionais** propriedade.

### <a name="to-set-this-compiler-option-programmatically"></a>Para definir essa opção do compilador via programação

- Consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalIncludeDirectories%2A>.

## <a name="example"></a>Exemplo

O comando a seguir procura os arquivos de inclusão solicitados pelo Main. c na seguinte ordem: primeiro no diretório que contém Main. c, em seguida, no diretório \include., em seguida, no diretório \MY\INCLUDE e, finalmente, nos diretórios atribuído a de inclusão variável de ambiente.

```
CL /I \INCLUDE /I\MY\INCLUDE MAIN.C
```

## <a name="see-also"></a>Consulte também

[Opções do Compilador](../../build/reference/compiler-options.md)<br/>
[Definindo opções do compilador](../../build/reference/setting-compiler-options.md)