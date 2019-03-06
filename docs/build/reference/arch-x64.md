---
title: /arch (x64)
ms.date: 11/04/2016
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: ac34a18efbf31787889cc4fe31ebd3d8473df0eb
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421848"
---
# <a name="arch-x64"></a>/arch (x64)

Especifica a arquitetura da geração de código em x64. Consulte também [/arch (x86)](../../build/reference/arch-x86.md) e [/arch (ARM)](../../build/reference/arch-arm.md).

## <a name="syntax"></a>Sintaxe

```
/arch:[AVX|AVX2]
```

## <a name="arguments"></a>Arguments

**/arch:AVX**<br/>
Habilita o uso de instruções Intel Advanced Vector Extensions.

**/arch:AVX2**<br/>
Habilita o uso de instruções Intel Advanced Vector Extensions 2.

## <a name="remarks"></a>Comentários

**/arch** somente afeta geração de código para funções nativas. Quando você usa [/clr](../../build/reference/clr-common-language-runtime-compilation.md) para compilar, **/arch** não tem efeito sobre a geração de código para funções gerenciadas.

O `__AVX__` símbolo do pré-processador é definido quando o **/arch: avx** opção de compilador é especificada. O `__AVX2__` símbolo do pré-processador é definido quando o **/arch:avx2** opção de compilador é especificada. Para obter mais informações, consulte [Macros predefinidas](../../preprocessor/predefined-macros.md). O **/arch:avx2** opção foi introduzida no Visual Studio 2013 atualização 2, versão 12.0.34567.1.

### <a name="to-set-the-archavx-or-archavx2-compiler-option-in-visual-studio"></a>Para definir a opção do compilador /arch:AVX ou /arch:AVX2 no Visual Studio

1. Abra o **páginas de propriedade** caixa de diálogo para o projeto. Para obter mais informações, confira [Trabalhando com propriedades do projeto](../../ide/working-with-project-properties.md).

1. Selecione o **propriedades de configuração**, **C/C++** pasta.

1. Selecione o **geração de código** página de propriedades.

1. No **habilitar conjunto de instruções de aprimorada** lista suspensa, escolha **extensões de vetor avançadas (/ /arch: AVX)** ou **Advanced Vector Extensions 2 (/ arch:avx2)**.

### <a name="to-set-this-compiler-option-programmatically"></a>Para definir essa opção do compilador via programação

- Consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Consulte também

[/arch (arquitetura mínima de CPU)](../../build/reference/arch-minimum-cpu-architecture.md)<br/>
[Opções do Compilador](../../build/reference/compiler-options.md)<br/>
[Definindo opções do compilador](../../build/reference/setting-compiler-options.md)
