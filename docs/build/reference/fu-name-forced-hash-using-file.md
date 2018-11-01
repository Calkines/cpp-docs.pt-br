---
title: '/FU (nome forçado #usando arquivo)'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.ForcedUsingFiles
- /FU
- VC.Project.VCNMakeTool.ForcedUsingAssemblies
helpviewer_keywords:
- -FU compiler option [C++]
- FU compiler option [C++]
- /FU compiler option [C++]
ms.assetid: 698f8603-457f-435a-baff-5ac9243d6ca1
ms.openlocfilehash: ecd9290336cfd6efd183bdd701f1d447b7ddaf2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492079"
---
# <a name="fu-name-forced-using-file"></a>/FU (nome forçado #usando arquivo)

Uma opção de compilador que você pode usar como uma alternativa ao passar um nome de arquivo para [# diretiva using](../../preprocessor/hash-using-directive-cpp.md) no código-fonte.

## <a name="syntax"></a>Sintaxe

> **/Fu** *arquivo*

## <a name="arguments"></a>Arguments

*file*<br/>
Especifica o arquivo de metadados para fazer referência a esta compilação.

## <a name="remarks"></a>Comentários

O comutador /FU leva apenas um nome de arquivo. Para especificar vários arquivos, use /FU com cada um deles.

Se você estiver usando o C + + c++ CLI e fazem referência a metadados para usar o [Assemblies amigáveis](../../dotnet/friend-assemblies-cpp.md) recurso, não é possível usar **/FU**. Você deve referenciar os metadados no código usando `#using`— junto com o `[as friend]` atributo. Assemblies amigáveis não têm suporte em extensões de componentes do Visual C++ C + + c++ /CLI CX.

Para obter informações sobre como criar um assembly ou módulo para o common language runtime (CLR), consulte [/clr (compilação de tempo de execução de linguagem comum)](../../build/reference/clr-common-language-runtime-compilation.md). Para obter informações sobre como compilar no C + + c++ /CX, consulte [compilando aplicativos e bibliotecas](../../cppcx/building-apps-and-libraries-c-cx.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio

1. Abra a caixa de diálogo **Páginas de Propriedades** do projeto. Para obter detalhes, confira [Trabalhando com propriedades do projeto](../../ide/working-with-project-properties.md).

1. Selecione o **propriedades de configuração** > **C/C++** > **avançado** página de propriedades.

1. Modificar a **forçar #using** propriedade.

### <a name="to-set-this-compiler-option-programmatically"></a>Para definir essa opção do compilador via programação

- Consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedUsingFiles%2A>.

## <a name="see-also"></a>Consulte também

[Opções do arquivo de saída (/F)](../../build/reference/output-file-f-options.md)<br/>
[Opções do Compilador](../../build/reference/compiler-options.md)<br/>
[Definindo opções do compilador](../../build/reference/setting-compiler-options.md)