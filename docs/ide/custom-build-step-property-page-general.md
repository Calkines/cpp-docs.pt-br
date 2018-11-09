---
title: 'Página de Propriedades de Etapa de Build Personalizado: geral'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCustomBuildStep.AdditionalInputs
- VC.Project.VCCustomBuildStep.CustomBuildAfterTargets
- VC.Project.VCCustomBuildStep.CustomBuildBeforeTargets
- VC.Project.VCCustomBuildStep.Outputs
- VC.Project.VCCustomBuildStep.Message
- VC.Project.VCCustomBuildStep.Command
helpviewer_keywords:
- project properties, custom build step
- custom build step (general)
ms.assetid: bd319741-0491-46c4-a428-7c61b4b46a02
ms.openlocfilehash: dc6765c9519c6cdb4245afa2f07079548a07e1fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621748"
---
# <a name="custom-build-step-property-page-general"></a>Página de Propriedades de Etapa de Build Personalizado: geral

Para cada combinação de configuração de projeto e plataforma de destino em seu projeto, você pode especificar uma etapa personalizada a ser executada quando o projeto é compilado.

Para obter a versão do Linux desta página, confira [Propriedades de Etapa de Build Personalizada (Linux C++)](../linux/prop-pages/custom-build-step-linux.md).

## <a name="uielement-list"></a>Lista UIElement

- **Linha de comando**

   O comando a ser executado pela etapa de compilação personalizada.

- **Descrição**

   Uma mensagem que será exibida quando a etapa de compilação personalizada for executada.

- **Saídas**

   O arquivo de saída gerado pela etapa de compilação personalizada. Essa configuração é necessária para que as compilações incrementais funcionem corretamente.

- **Dependências adicionais**

   Uma lista delimitada por ponto-e-vírgula de arquivos de entrada adicionais a ser usada para a etapa de compilação personalizada.

- **Executar depois e executar antes**

   Essas opções definem quando a etapa de compilação personalizada é executada no processo de compilação, em relação aos destinos listados. Os destinos mais comumente listados são BuildGenerateSources, BuildCompile e BuildLink, porque representam as etapas principais no processo de compilação. Outros destinos frequentemente listados são Midl, CLCompile e Link.

- **Tratar saída como conteúdo**

   Essa opção só é significativa para aplicativos da Plataforma Universal do Windows ou do Windows Phone, que incluem todos os arquivos de conteúdo no pacote .appx.

### <a name="to-specify-a-custom-build-step"></a>Para especificar uma etapa de compilação personalizada

1. Na barra de menus, escolha **Projeto**, **Propriedades**. Para obter mais informações, confira [Trabalhando com propriedades do projeto](../ide/working-with-project-properties.md).

1. Na caixa de diálogo **Páginas de Propriedades**, navegue para a página **Propriedades de Configuração**, **Etapa de Build Personalizada**, **Geral**.

1. Modifique as configurações.

## <a name="see-also"></a>Consulte também

[Páginas de propriedade](../ide/property-pages-visual-cpp.md)