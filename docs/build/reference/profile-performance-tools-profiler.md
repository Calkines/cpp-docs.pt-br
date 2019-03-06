---
title: /PROFILE (criador de perfil das ferramentas de desempenho)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Profile
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
ms.openlocfilehash: a0fda47497ffc247dd9678ece7aac76291aed1ff
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57419147"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (criador de perfil das ferramentas de desempenho)

Produz um arquivo de saída que pode ser usado com o criador de perfil de Ferramentas de desempenho.

## <a name="syntax"></a>Sintaxe

```
/PROFILE
```

## <a name="remarks"></a>Comentários

/ PERFIL implica que as seguintes opções do vinculador:

- [/OPT:REF](../../build/reference/opt-optimizations.md)

- /OPT:NOICF

- [/INCREMENTAL:NO](../../build/reference/incremental-link-incrementally.md)

- [/FIXED:NO](../../build/reference/fixed-fixed-base-address.md)

/ PERFIL faz com que o vinculador gerar uma seção de realocação na imagem do programa.  Uma seção de realocação permite que o criador de perfil transformar a imagem de programa para obter dados de perfil.

**/ PERFIL** só está disponível apenas nas versões Enterprise (desenvolvimento de equipe).  Para obter mais informações sobre o PREfast, consulte [análise de código para visão geral do C/C++](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do vinculador no ambiente de desenvolvimento do Visual Studio

1. Abra a caixa de diálogo **Páginas de Propriedades** do projeto. Para obter detalhes, confira [Trabalhando com propriedades do projeto](../../ide/working-with-project-properties.md).

1. Expanda o nó **Propriedades de Configuração**.

1. Expanda o **vinculador** nó.

1. Selecione o **avançado** página de propriedades.

1. Modificar a **perfil** propriedade.

### <a name="to-set-this-linker-option-programmatically"></a>Para definir esta opção do vinculador por meio de programação

1. Consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.

## <a name="see-also"></a>Consulte também

[Definindo opções de vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opções do vinculador](../../build/reference/linker-options.md)
