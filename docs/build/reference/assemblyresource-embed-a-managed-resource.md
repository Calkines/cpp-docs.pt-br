---
title: /ASSEMBLYRESOURCE (inserir um recurso gerenciado)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.EmbedManagedResourceFile
- /ASSEMBLYRESOURCE
helpviewer_keywords:
- ASSEMBLYRESOURCE linker option
- assemblies [C++]
- -ASSEMBLYRESOURCE linker option
- assemblies [C++], linking resource files
- /ASSEMBLYRESOURCE linker option
ms.assetid: 0ce6e1fb-921b-4b1b-a59c-d35388d789f2
ms.openlocfilehash: c18a014ca645cceb3196fb7efefd227e96f8e1fa
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416210"
---
# <a name="assemblyresource-embed-a-managed-resource"></a>/ASSEMBLYRESOURCE (inserir um recurso gerenciado)

```
/ASSEMBLYRESOURCE:filename[,[name][,PRIVATE]]
```

## <a name="parameters"></a>Parâmetros

*filename*<br/>
O recurso gerenciado que você deseja inserir neste assembly.

*name*<br/>
Opcional. O nome lógico do recurso; o nome usado para carregar o recurso. O padrão é o nome do arquivo.

Opcionalmente, você pode especificar se o arquivo deve ser privado no manifesto do assembly. Por padrão, *nome* é público no assembly.

## <a name="remarks"></a>Comentários

Use a opção de /ASSEMBLYRESOURCE. para inserir um recurso em um assembly.

Os recursos são públicos no assembly quando criado com a opção de vinculador. O vinculador não permite que você renomeie o recurso no assembly.

Se *filename* é um arquivo de recurso (. resources) do .NET Framework criado, por exemplo, pelo [gerador de arquivos de recurso (Resgen.exe)](/dotnet/framework/tools/resgen-exe-resource-file-generator) ou no ambiente de desenvolvimento, ele pode ser acessado com membros no **System. Resources** namespace (consulte [System.Resources.ResourceManager](/dotnet/api/system.resources.resourcemanager) para obter mais informações). Para todos os outros recursos, use o **GetManifestResource** \* métodos **Reflection** classe para acessar o recurso em tempo de execução.

Outras opções de vinculador que afetam a geração de assembly são:

- [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)

- [/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

- [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do vinculador no ambiente de desenvolvimento do Visual Studio

1. Abra a caixa de diálogo **Páginas de Propriedades** do projeto. Para obter detalhes, consulte [configuração de propriedades do projeto Visual C++](../../ide/working-with-project-properties.md).

1. Clique o **vinculador** pasta.

1. Clique o **entrada** página de propriedades.

1. Modificar a **Inserir arquivo de recurso gerenciado** propriedade.

### <a name="to-set-this-linker-option-programmatically"></a>Para definir esta opção do vinculador por meio de programação

1. Consulte <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EmbedManagedResourceFile%2A>.

## <a name="see-also"></a>Consulte também

[Definindo opções de vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opções do vinculador](../../build/reference/linker-options.md)
