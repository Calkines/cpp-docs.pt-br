---
title: /Gm (habilitar recompilação manual)
ms.date: 11/12/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.MinimalRebuild
- /Gm
- /FD
- VC.Project.VCCLWCECompilerTool.MinimalRebuild
helpviewer_keywords:
- /Gm compiler option [C++]
- minimal rebuild
- enable minimal rebuild compiler option [C++]
- Gm compiler option [C++]
- -Gm compiler option [C++]
ms.assetid: d8869ce0-d2ea-40eb-8dae-6d2cdb61dd59
ms.openlocfilehash: 4a66dda37b84119a4b8bc23f7fc719d50e8786f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292051"
---
# <a name="gm-enable-minimal-rebuild"></a>/Gm (habilitar recompilação manual)

Preterido. Habilita recompilação mínima, que determina se os arquivos de origem C++ que incluem definições de classe C++ alteradas (armazenadas nos arquivos de cabeçalho (.h)) precisam ser recompilados.

## <a name="syntax"></a>Sintaxe

```
/Gm
```

## <a name="remarks"></a>Comentários

**/GM** foi preterido. Ele poderá não disparar uma compilação para determinados tipos de alterações do arquivo de cabeçalho. Você pode remover com segurança essa opção de seus projetos. Para melhorar o tempo de compilação, é recomendável usar cabeçalhos pré-compilados e paralelos e incrementais opções de build em vez disso. Para obter uma lista de opções do compilador preterido, consulte o **preteridos e removidos opções do compilador** seção [opções de compilador listadas por categoria](compiler-options-listed-by-category.md).

O compilador armazena as informações de dependência entre arquivos de origem e definições de classe no arquivo .idb do projeto durante a primeira compilação. (Informações sobre dependência dizem que arquivo de origem depende da definição de classe, e qual arquivo. h a definição está localizado em.) As compilações subsequentes usam as informações armazenadas no arquivo. IDB para determinar se um arquivo de origem precisa ser compilado, mesmo se ele inclui um arquivo. h modificado.

> [!NOTE]
> A recompilação mínima conta com definições de classe que não mudem entre os arquivos incluídos. As definições de classe devem ser globais para um projeto (deve haver apenas uma definição de uma determinada classe), pois as informações de dependência no arquivo .idb são criadas para todo o projeto. Se você tiver mais de uma definição para uma classe no seu projeto, desabilite a recompilação mínima.

Como o vinculador incremental não oferece suporte a metadados do Windows incluídos em arquivos. obj usando a [/ZW (compilação de tempo de execução do Windows)](zw-windows-runtime-compilation.md) opção, o **/Gm** opção é incompatível com  **/ZW**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio

1. Abra a caixa de diálogo **Páginas de Propriedades** do projeto. Para obter detalhes, consulte [propriedades de compilador e de build definida C++ no Visual Studio](../working-with-project-properties.md).

1. Selecione o **propriedades de configuração** > **C/C++** > **geração de código** página de propriedades.

1. Modificar a **habilitar recompilação mínima** propriedade.

### <a name="to-set-this-compiler-option-programmatically"></a>Para definir essa opção do compilador via programação

- Consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>.

## <a name="see-also"></a>Consulte também

[Opções do compilador MSVC](compiler-options.md)<br/>
[Sintaxe da linha de comando do compilador MSVC](compiler-command-line-syntax.md)
