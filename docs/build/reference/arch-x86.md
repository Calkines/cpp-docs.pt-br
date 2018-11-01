---
title: /arch (x86)
ms.date: 11/04/2016
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
ms.openlocfilehash: fb115d564ca24ff29e120e0d8c25e0dbe28024cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549702"
---
# <a name="arch-x86"></a>/arch (x86)

Especifica a arquitetura para a geração de código no x86. Consulte também [/arch (x64)](../../build/reference/arch-x64.md) e [/arch (ARM)](../../build/reference/arch-arm.md).

## <a name="syntax"></a>Sintaxe

```
/arch:[IA32|SSE|SSE2|AVX|AVX2]
```

## <a name="arguments"></a>Arguments

**/ arch:IA32**<br/>
Não especifica instruções aprimoradas e especifica x87 para cálculos de ponto flutuante.

**/arch:SSE**<br/>
Habilita o uso de instruções SSE.

**/ arch:SSE2**<br/>
Habilita o uso de instruções SSE2. Essa é a instrução padrão em x86 plataformas se nenhum **/arch** opção for especificada.

**/arch: avx**<br/>
Habilita o uso de instruções Intel Advanced Vector Extensions.

**/ arch:avx2**<br/>
Habilita o uso de instruções Intel Advanced Vector Extensions 2.

## <a name="remarks"></a>Comentários

As instruções SSE e SSE2 existem em diversos processadores Intel e AMD. As instruções AVX existem nos processadores Intel Sandy Bridge e AMD Bulldozer. As instruções AVX2 são compatíveis com processadores Intel Haswell e Broadwell, e em processadores AMD baseados em Excavator.

O `_M_IX86_FP`, `__AVX__` e `__AVX2__` macros indicam que, se houver, **/arch** opção de compilador foi usada. Para obter mais informações, consulte [Macros predefinidas](../../preprocessor/predefined-macros.md). O **/arch:avx2** opção e `__AVX2__` macro foram introduzidos no Visual Studio 2013 atualização 2, versão 12.0.34567.1.

O otimizador escolhe quando e como usar as instruções SSE e SSE2 quando **/arch** for especificado. Ele usa as instruções SSE e SSE2 em alguns cálculos escalares de ponto flutuante quando determina que é mais rápido usar registros e instruções SSE/SSE2 em vez da pilha de registro de ponto flutuante do x87. Por isso, no momento, seu código pode combinar x87 e SSE/SSE2 nos cálculos de ponto flutuante. Além disso, com **/arch:SSE2**, as instruções SSE2 podem ser usadas para algumas operações de inteiro de 64 bits.

Além de usar as instruções SSE e SSE2, o compilador também usa outras instruções presentes nas revisões do processador, que são compatíveis com SSE e SSE2. Um exemplo disso é a instrução CMOV que apareceu pela primeira vez na revisão Pentium Pro dos processadores Intel.

Como o compilador do x86 gera códigos que usam as instruções SSE2 por padrão, você deve especificar **/arch:IA32** para desativar a geração de instruções SSE e SSE2 para x86 de processadores.

**/arch** somente afeta geração de código para funções nativas. Quando você usa [/clr](../../build/reference/clr-common-language-runtime-compilation.md) para compilar, **/arch** não tem efeito sobre a geração de código para funções gerenciadas.

**/arch** e [/QIfist](../../build/reference/qifist-suppress-ftol.md) não pode ser usado no mesmo compiland. Isso é importante principalmente se você não estiver usando a opção `_controlfp` para modificar a palavra de controle de FP, e o código de inicialização do tempo de execução definir o campo de controle de precisão da palavra de controle de FPU do x87 como 53 bits. Portanto, todas as operações duplicadas e de flutuação das expressões usam significandos de 53 bits e expoentes de 15 bits. No entanto, todas as operações SSE de precisão simples usam significandos de 24 bits e expoentes de 8 bits. Já as operações SSE2 de precisão dupla usam significandos de 53 bits e expoentes de 11 bits. Para obter mais informações, consulte [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md). Essas diferenças podem ser usadas em árvores de expressões, mas não quando há uma atribuição de usuário após cada subexpressão. Considere o seguinte:

```cpp
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.
```

Compare:

```cpp
t = f1 * f2;   // Do f1 * f2, round to the type of t.
r = t + d;     // This should produce the same overall result
               // whether x87 stack is used or SSE/SSE2 is used.
```

### <a name="to-set-this-compiler-option-for-avx-avx2-ia32-sse-or-sse2-in-visual-studio"></a>Para definir essa opção de compilador para AVX, AVX2, IA32, SSE ou SSE2 no Visual Studio

1. Abra o **páginas de propriedade** caixa de diálogo para o projeto. Para obter mais informações, confira [Trabalhando com propriedades do projeto](../../ide/working-with-project-properties.md).

1. Selecione o **propriedades de configuração**, **C/C++** pasta.

1. Selecione o **geração de código** página de propriedades.

1. Modificar a **habilitar o conjunto de instruções de avançado** propriedade.

### <a name="to-set-this-compiler-option-programmatically"></a>Para definir essa opção do compilador via programação

- Consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Consulte também

[/arch (arquitetura mínima de CPU)](../../build/reference/arch-minimum-cpu-architecture.md)<br/>
[Opções do Compilador](../../build/reference/compiler-options.md)<br/>
[Definindo opções do compilador](../../build/reference/setting-compiler-options.md)