---
title: /Wp64 (detectar problemas de portabilidade de 64 bits)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems
- VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems
- /wp64
helpviewer_keywords:
- 64-bit compiler [C++], detecting portability problems
- /Wp64 compiler option [C++]
- -Wp64 compiler option [C++]
- Wp64 compiler option [C++]
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
ms.openlocfilehash: 5a3cdaf85fa4dc05ece54fc630cb69fc93650e6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316542"
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64 (detectar problemas de portabilidade de 64 bits)

Essa opção do compilador é obsoleta. Nas versões do Visual Studio anteriores ao Visual Studio 2013, isso detecta problemas de portabilidade de 64 bits nos tipos que também são marcados com o [__w64](../../cpp/w64.md) palavra-chave.

## <a name="syntax"></a>Sintaxe

```
/Wp64
```

## <a name="remarks"></a>Comentários

Por padrão, nas versões do Visual Studio anteriores ao Visual Studio 2013, o **/Wp64** opção de compilador está desativada no compilador MSVC que compilações x86 de 32 bits código, e no compilador MSVC que compilações de 64 bits, x64 código.

> [!IMPORTANT]
>  O [/Wp64](wp64-detect-64-bit-portability-issues.md) opção de compilador e [__w64](../../cpp/w64.md) palavra-chave foram preteridas no Visual Studio 2010 e o Visual Studio 2012 e não tem suporte a partir do Visual Studio 2013. Se você converter um projeto que usa essa opção, o comutador não será migrado durante a conversão. Para usar essa opção no Visual Studio 2010 ou Visual Studio 2012, você deve digitar o comutador de compilador sob **opções adicionais** na **linha de comando** seção das propriedades do projeto. Se você usar o **/Wp64** opção de compilador na linha de comando, o compilador emite D9002 de aviso de linha de comando. Em vez de usar essa opção e palavra-chave para detectar problemas de portabilidade de 64 bits, use um compilador MSVC que tem como alvo uma plataforma de 64 bits e especifique o [/W4](compiler-option-warning-level.md) opção. Para obter mais informações, consulte [C++ configurar projetos para 64 bits, x64 destinos](../configuring-programs-for-64-bit-visual-cpp.md).

Variáveis dos tipos a seguir são testadas em um sistema operacional de 32 bits, como se eles estavam sendo usados em um sistema operacional de 64 bits:

- int

- long

- pointer

Se você compilar regularmente seu aplicativo usando um compilador que builds de 64 bits, x64 código, você pode simplesmente desabilitar **/Wp64** em suas compilações de 32 bits porque o compilador de 64 bits detectará todos os problemas. Para obter mais informações sobre como sistema operacional de destino de Windows 64 bits, consulte [C++ configurar projetos para 64 bits, x64 destinos](../configuring-programs-for-64-bit-visual-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio

1. Abra o projeto **páginas de propriedade** caixa de diálogo.

   Para obter mais informações, consulte [propriedades de compilador e de build definida C++ no Visual Studio](../working-with-project-properties.md).

1. Clique o **C/C++** pasta.

1. Clique o **linha de comando** página de propriedades.

1. Modificar a **opções adicionais** caixa para incluir **/Wp64**.

### <a name="to-set-this-compiler-option-programmatically"></a>Para definir essa opção do compilador via programação

- Consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>.

## <a name="see-also"></a>Consulte também

[Opções do compilador MSVC](compiler-options.md)<br/>
[Sintaxe da linha de comando do compilador MSVC](compiler-command-line-syntax.md)<br/>
[Configurar projetos do C++ para x64 de 64 bits, destinos](../configuring-programs-for-64-bit-visual-cpp.md)
