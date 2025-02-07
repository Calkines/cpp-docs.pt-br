---
title: /GX (habilitar tratamento de exceções)
ms.date: 11/04/2016
f1_keywords:
- /gx
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
ms.openlocfilehash: 43be8f6d0f080f0d85568ce5b089751fc68f0e8e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291997"
---
# <a name="gx-enable-exception-handling"></a>/GX (habilitar tratamento de exceções)

Preterido. Habilita o tratamento de exceções síncronas usando a suposição de que funções declarado usando `extern "C"` nunca geram uma exceção.

## <a name="syntax"></a>Sintaxe

```
/GX
```

## <a name="remarks"></a>Comentários

**/GX** foi preterido. Use o equivalente [/EHsc](eh-exception-handling-model.md) opção em vez disso. Para obter uma lista de opções do compilador preterido, consulte o **preteridos e removidos opções do compilador** seção [opções de compilador listadas por categoria](compiler-options-listed-by-category.md).

Por padrão, **/EHsc**, o equivalente **/GX**, está em vigor quando você compila usando o ambiente de desenvolvimento do Visual Studio. Ao usar as ferramentas de linha de comando, sem tratamento de exceções é especificado. Este é o equivalente de **/GX-**.

Para obter mais informações, consulte [tratamento de exceções de C++](../../cpp/cpp-exception-handling.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio

1. Abra a caixa de diálogo **Páginas de Propriedades** do projeto. Para obter detalhes, consulte [propriedades de compilador e de build definida C++ no Visual Studio](../working-with-project-properties.md).

1. No painel de navegação, escolha **propriedades de configuração**, **C/C++**, **linha de comando**.

1. Digite a opção de compilador na **opções adicionais** caixa.

### <a name="to-set-this-compiler-option-programmatically"></a>Para definir essa opção do compilador via programação

- Consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Consulte também

[Opções do compilador MSVC](compiler-options.md)<br/>
[Sintaxe da linha de comando do compilador MSVC](compiler-command-line-syntax.md)<br/>
[/EH (modelo de tratamento de exceções)](eh-exception-handling-model.md)
