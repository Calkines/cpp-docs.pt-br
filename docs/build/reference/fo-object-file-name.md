---
title: /Fo (Nome do arquivo de objeto)
ms.date: 11/04/2016
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
ms.openlocfilehash: a8f2c1a196f18e6d310fd41d4dbed751440a4c20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293037"
---
# <a name="fo-object-file-name"></a>/Fo (Nome do arquivo de objeto)

Especifica um nome de arquivo de objeto (.obj) ou diretório a ser usado no lugar do padrão.

## <a name="syntax"></a>Sintaxe

```
/Fopathname
```

## <a name="remarks"></a>Comentários

Se você não usar essa opção, o arquivo de objeto usa o nome base do arquivo de origem e a extensão. obj. Você pode usar qualquer nome e a extensão desejada, mas a convenção recomendada é usar. obj.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio

1. Abra a caixa de diálogo **Páginas de Propriedades** do projeto. Para obter detalhes, consulte [propriedades de compilador e de build definida C++ no Visual Studio](../working-with-project-properties.md).

1. Clique o **C/C++** pasta.

1. Clique o **arquivos de saída** página de propriedades.

1. Modificar a **nome do arquivo de objeto** propriedade.  No ambiente de desenvolvimento, o arquivo de objeto deve ter uma extensão de. obj.

### <a name="to-set-this-compiler-option-programmatically"></a>Para definir essa opção do compilador via programação

- Consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.

## <a name="example"></a>Exemplo

A linha de comando a seguir cria um arquivo de objeto chamado THIS.obj em um diretório existente, \OBJECT, na unidade B.

```
CL /FoB:\OBJECT\ THIS.C
```

## <a name="see-also"></a>Consulte também

[Opções do arquivo de saída (/F)](output-file-f-options.md)<br/>
[Opções do compilador MSVC](compiler-options.md)<br/>
[Sintaxe da linha de comando do compilador MSVC](compiler-command-line-syntax.md)<br/>
[Especificando o nome de caminho](specifying-the-pathname.md)
