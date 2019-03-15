---
title: /vmb, - vmg (método de representação)
ms.date: 11/04/2016
f1_keywords:
- /vmb
- /vmg
helpviewer_keywords:
- vmb compiler option [C++]
- -vmg compiler option [C++]
- vmg compiler option [C++]
- -vmb compiler option [C++]
- /vmb compiler option [C++]
- representation method compiler options [C++]
- /vmg compiler option [C++]
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
ms.openlocfilehash: eac41de04ec883e7b5acf26596647f912b0b1d20
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808476"
---
# <a name="vmb-vmg-representation-method"></a>/vmb, /vmg (método de representação)

Selecione o método que o compilador usa para representar os ponteiros para membros de classe.

Use **/vmb** se você sempre define uma classe antes de declarar um ponteiro para um membro da classe.

Use **/vmg** para declarar um ponteiro para um membro de uma classe antes da definição da classe. Essa necessidade pode surgir se você definir os membros de duas classes diferentes que fazem referência entre si. Para essas classes mutuamente referência, uma classe deve ser referenciada antes de ser definida.

## <a name="syntax"></a>Sintaxe

```
/vmb
/vmg
```

## <a name="remarks"></a>Comentários

Você também pode usar [pointers_to_members](../../preprocessor/pointers-to-members.md) ou [palavras-chave de herança](../../cpp/inheritance-keywords.md) em seu código para especificar uma representação de ponteiro.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio

1. Abra a caixa de diálogo **Páginas de Propriedades** do projeto. Para obter detalhes, consulte [propriedades de compilador e de build definida C++ no Visual Studio](../working-with-project-properties.md).

1. Clique o **C/C++** pasta.

1. Clique o **linha de comando** página de propriedades.

1. Digite a opção de compilador na **opções adicionais** caixa.

### <a name="to-set-this-compiler-option-programmatically"></a>Para definir essa opção do compilador via programação

- Consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Consulte também

[Opções do compilador MSVC](compiler-options.md)<br/>
[Sintaxe de linha de comando do compilador MSVC](compiler-command-line-syntax.md)
