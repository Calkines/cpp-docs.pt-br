---
title: /NXCOMPAT (compatível com Prevenção de Execução de Dados)
ms.date: 12/29/2017
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: 815719468e7dcf9325d19efe879b8f4ace040094
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490483"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (compatível com Prevenção de Execução de Dados)

Indica que um executável é compatível com o recurso Windows Data Execution Prevention.

## <a name="syntax"></a>Sintaxe

> **/NXCOMPAT**[**: NENHUMA**]

## <a name="remarks"></a>Comentários

Por padrão, **/NXCOMPAT** está em.

**/NXCOMPAT: no** pode ser usado para especificar explicitamente um executável como incompatível com Data Execution Prevention.

Para obter mais informações sobre a prevenção de execução de dados, consulte estes artigos:

- [Uma descrição detalhada do recurso prevenção de execução de dados (DEP)](https://support.microsoft.com/help/875352/a-detailed-description-of-the-data-execution-prevention-dep-feature-in)

- [Prevenção de execução de dados](/windows/desktop/Memory/data-execution-prevention)

- [Prevenção de execução de dados (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para definir essa opção do vinculador no Visual Studio

1. Abra o projeto **páginas de propriedade** caixa de diálogo. Para obter detalhes, confira [Trabalhando com propriedades do projeto](../../ide/working-with-project-properties.md).

1. Escolha o **propriedades de configuração** > **vinculador** > **linha de comando** página de propriedades.

1. Insira a opção na **opções adicionais** caixa. Escolher **Okey** ou **aplicar** para aplicar a alteração.

### <a name="to-set-this-linker-option-programmatically"></a>Para definir esta opção do vinculador por meio de programação

- Consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Consulte também

[Definindo opções de vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opções do vinculador](../../build/reference/linker-options.md)
