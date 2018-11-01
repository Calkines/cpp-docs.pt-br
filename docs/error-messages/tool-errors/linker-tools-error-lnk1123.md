---
title: Erro das Ferramentas de Vinculador LNK1123
ms.date: 12/29/2017
f1_keywords:
- LNK1123
helpviewer_keywords:
- LNK1123
ms.openlocfilehash: b67a2a4ddad13988967b7cc7d827862a2a6fe933
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456414"
---
# <a name="linker-tools-error-lnk1123"></a>Erro das Ferramentas de Vinculador LNK1123

> falha durante a conversão para COFF: arquivo inválido ou corrompido

Os arquivos de entrada devem ter o formato COFF (Common Object File Format). Se um arquivo de entrada não for COFF, o vinculador tenta converter automaticamente objetos OMF de 32 bits para COFF ou executa CVTRES.EXE para converter arquivos de recurso. Essa mensagem indica que o vinculador não pode converter o arquivo. Isso também ocorre ao usar uma versão incompatível do CVTRES.EXE de outra instalação do Visual Studio, do Windows Development Kit ou do .NET Framework.

> [!NOTE]
> Se você estiver executando uma versão anterior do Visual Studio, pode não haver suporte para a conversão automática.

## <a name="to-fix-the-problem"></a>Para corrigir o problema

- Aplica todos os service packs e atualizações para sua versão do Visual Studio. Isso é especialmente importante para o Visual Studio 2010.

- Tente compilar com a vinculação incremental desabilitada. Na barra de menus, escolha **Projeto**, **Propriedades**. No **páginas de propriedades** diálogo caixa, expanda **propriedades de configuração**, **vinculador**. Altere o valor de **habilitar vinculação Incremental** à **não**.

- Verifique se a versão do CVTRES.EXE encontrada primeiro na variável de ambiente PATH combina com a versão das ferramentas de compilação ou com a versão do Conjunto de Ferramentas de Plataforma, usado no projeto.

- Tente desativar a opção de inserção de manifesto. Na barra de menus, escolha **Projeto**, **Propriedades**. No **páginas de propriedades** diálogo caixa, expanda **propriedades de configuração**, **ferramenta de manifesto**, **de entrada e saída**. Altere o valor de **Inserir manifesto** à **não**.

- Verifique se o tipo de arquivo é válido. Por exemplo, verifique se um objeto OMF é de 32 bits e não de 16 bits. Para obter mais informações, consulte [. Arquivos obj como entrada de vinculador](../../build/reference/dot-obj-files-as-linker-input.md) e [formato PE](/windows/desktop/Debug/pe-format).

- Verifique se o arquivo não está corrompido. Recompile-o, se necessário.

## <a name="see-also"></a>Consulte também

[Arquivos .obj como entrada do vinculador](../../build/reference/dot-obj-files-as-linker-input.md)<br/>
[Referência de EDITBIN](../../build/reference/editbin-reference.md)<br/>
[Referência de DUMPBIN](../../build/reference/dumpbin-reference.md)
