---
title: 'Como: Usar eventos de compilação em projetos do MSBuild'
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
ms.openlocfilehash: 3fe205223b6cf381bbf3e2872b1a84f9d81a3cb7
ms.sourcegitcommit: 2da5c42928739ca8cd683a9002598f28d8ec5f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70060062"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>Como: Usar eventos de compilação em projetos do MSBuild

Um evento de compilação é um comando que o MSBuild executa em um estágio específico no processo de compilação. O evento de *pré-compilação* ocorre antes do início da compilação; o evento de *pré-vínculo* ocorre antes do início da etapa de link; e o evento de *pós-compilação* ocorre depois que a compilação é encerrada com êxito. Um evento de compilação ocorrerá somente se a etapa de compilação associada ocorrer. Por exemplo, o evento de pré-vínculo não ocorrerá se a etapa de vínculo não for executada.

Cada um dos três eventos de compilação é representado em um grupo de definição de item por um`<Command>`elemento Command () que é executado e um`<Message>`elemento Message () que é exibido quando o **MSBuild** executa o evento de compilação. Cada elemento é opcional e, se você especificar o mesmo elemento várias vezes, a última ocorrência terá precedência.

Um elemento *Use-in-Build* opcional (`<`*compilação-evento*`UseInBuild>`) pode ser especificado em um grupo de propriedades para indicar se o evento de compilação é executado. O valor do conteúdo de um elemento *Use-in-Build* é **true** ou **false**. Por padrão, um evento de compilação é executado, a menos que seu elemento *de uso no Build* correspondente `false`esteja definido como.

A tabela a seguir lista cada elemento XML do evento de compilação:

|Elemento XML|Descrição|
|-----------------|-----------------|
|`PreBuildEvent`|Esse evento é executado antes do início da compilação.|
|`PreLinkEvent`|Esse evento é executado antes do início da etapa de link.|
|`PostBuildEvent`|Esse evento é executado após a conclusão da compilação.|

A tabela a seguir lista cada elemento de *uso-in-Build* :

|Elemento XML|Descrição|
|-----------------|-----------------|
|`PreBuildEventUseInBuild`|Especifica se o evento de *pré-compilação* deve ser executado.|
|`PreLinkEventUseInBuild`|Especifica se o evento de *pré-vínculo* deve ser executado.|
|`PostBuildEventUseInBuild`|Especifica se o evento de *pós-compilação* deve ser executado.|

## <a name="example"></a>Exemplo

O exemplo a seguir pode ser adicionado dentro do elemento de projeto do arquivo myproject. vcxproj criado no [Walkthrough: Usando o MSBuild para criar C++ um](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)projeto. Um evento de *pré-compilação* faz uma cópia do Main. cpp; um evento de *pré-vínculo* faz uma cópia do Main. obj; e um evento de *pós-compilação* faz uma cópia de MyProject. exe. Se o projeto for criado usando uma configuração de versão, os eventos de compilação serão executados. Se o projeto for criado usando uma configuração de depuração, os eventos de compilação não serão executados.

``` xml
<ItemDefinitionGroup>
  <PreBuildEvent>
    <Command>copy $(ProjectDir)main.cpp $(ProjectDir)copyOfMain.cpp</Command>
    <Message>Making a copy of main.cpp </Message>
  </PreBuildEvent>
  <PreLinkEvent>
    <Command>copy $(ProjectDir)$(Configuration)\main.obj $(ProjectDir)$(Configuration)\copyOfMain.obj</Command>
    <Message>Making a copy of main.obj</Message>
  </PreLinkEvent>
  <PostBuildEvent>
    <Command>copy $(ProjectDir)$(Configuration)\$(TargetFileName) $(ProjectDir)$(Configuration)\copyOfMyproject.exe</Command>
    <Message>Making a copy of myproject.exe</Message>
  </PostBuildEvent>
</ItemDefinitionGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
  <PreBuildEventUseInBuild>true</PreBuildEventUseInBuild>
  <PreLinkEventUseInBuild>true</PreLinkEventUseInBuild>
  <PostBuildEventUseInBuild>true</PostBuildEventUseInBuild>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
  <PreBuildEventUseInBuild>false</PreBuildEventUseInBuild>
  <PreLinkEventUseInBuild>false</PreLinkEventUseInBuild>
  <PostBuildEventUseInBuild>false</PostBuildEventUseInBuild>
</PropertyGroup>
```

## <a name="see-also"></a>Consulte também

[MSBuild na linha de comando – C++](msbuild-visual-cpp.md)<br/>
[Passo a passo: usar o MSBuild para a criação de um projeto C++](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)
