---
title: /GF (eliminar cadeias de caracteres duplicadas)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.StringPooling
- VC.Project.VCCLWCECompilerTool.StringPooling
- /gf
helpviewer_keywords:
- duplicate strings
- Eliminate Duplicate Strings compiler option [C++]
- pooling strings compiler option [C++]
- -GF compiler option [C++]
- /GF compiler option [C++]
- GF compiler option [C++]
- strings [C++], pooling
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
ms.openlocfilehash: 90d3fb5c601d9534215a46594884be5d168fe0aa
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449549"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (eliminar cadeias de caracteres duplicadas)

Permite que o compilador criar uma cópia única de cadeias de caracteres idênticas na imagem do programa e na memória durante a execução. Essa é uma otimização chamada *pooling de cadeia de caracteres* que pode criar programas menores.

## <a name="syntax"></a>Sintaxe

```
/GF
```

## <a name="remarks"></a>Comentários

Se você usar **/GF**, o sistema operacional não Troque a parte da cadeia de caracteres da memória e pode ler as cadeias de caracteres de volta do arquivo de imagem.

**/GF** de pools de cadeias de caracteres como somente leitura. Se você tentar modificar cadeias de caracteres em **/GF**, ocorrerá um erro de aplicativo.

Pool de cadeia de caracteres permite que o que pretendiam como vários ponteiros para buffers de várias ser vários ponteiros para um único buffer. No código a seguir `s` e `t` são inicializados com a mesma cadeia de caracteres. Pooling de cadeia de caracteres faz com que eles apontam para a mesma memória:

```
char *s = "This is a character buffer";
char *t = "This is a character buffer";
```

> [!NOTE]
>  O [/ZI](z7-zi-zi-debug-information-format.md) opcional usada para editar e continuar, define automaticamente a **/GF** opção.

> [!NOTE]
>  O **/GF** opção de compilador cria uma seção endereçável para cada cadeia de caracteres exclusiva. E, por padrão, um arquivo de objeto pode conter até 65.536 seções endereçáveis. Se seu programa contiver mais de 65.536 cadeias de caracteres, use o [/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md) opção de compilador para criar mais seções.

**/GF** está em vigor quando [/O1](o1-o2-minimize-size-maximize-speed.md) ou [/O2](o1-o2-minimize-size-maximize-speed.md) é usado.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio

1. Abra a caixa de diálogo **Páginas de Propriedades** do projeto. Para obter detalhes, confira [Definir as propriedades de build e do compilador do C++ no Visual Studio](../working-with-project-properties.md).

1. Clique o **C/C++** pasta.

1. Clique o **geração de código** página de propriedades.

1. Modificar a **habilitar o Pooling de cadeia de caracteres** propriedade.

### <a name="to-set-this-compiler-option-programmatically"></a>Para definir essa opção do compilador via programação

- Consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>.

## <a name="see-also"></a>Consulte também

[Opções do compilador MSVC](compiler-options.md)<br/>
[Sintaxe da linha de comando do compilador MSVC](compiler-command-line-syntax.md)
