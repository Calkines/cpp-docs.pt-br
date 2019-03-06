---
title: 'Como: Usar eventos de Build em projetos do MSBuild'
ms.date: 11/04/2016
f1_keywords:
- msbuild.cpp.howto.usebuildevents
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
ms.openlocfilehash: ea9ff51066c09e1e4a783b622248d9774a023172
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417564"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>Como: Usar eventos de Build em projetos do MSBuild

Um evento de compilação é um comando que o MSBuild executa em um estágio específico no processo de compilação. O *pré-build* evento ocorre antes do início do build; a *pré-vínculo* evento ocorre antes do início da etapa de link; e o *pós-compilação* evento ocorre após a compilação termina com êxito. Um evento de compilação ocorre apenas se a etapa de compilação associado ocorre. Por exemplo, o evento de pré-vínculo não ocorrer se a etapa de link não é executado.

Cada um dos eventos de três build é representada por um elemento de comando em um grupo de definição de item (`<Command>`) que é executado e um elemento de mensagem (`<Message>`) que é exibido quando **MSBuild** executa o evento de compilação. Cada elemento é opcional e, se você especificar o mesmo elemento várias vezes, a última ocorrência terá precedência.

Um recurso opcional *uso no build* elemento (`<`*evento de build*`UseInBuild>`) pode ser especificado em um grupo de propriedade para indicar se o evento de build é executado. O valor do conteúdo de um *uso no build* elemento seja **verdadeiro** ou **false**. Por padrão, um evento de compilação é executado, a menos que seu correspondente *uso no build* é definido como `false`.

A tabela a seguir lista cada elemento XML do evento de compilação:

|Elemento XML|Descrição|
|-----------------|-----------------|
|`PreBuildEvent`|Esse evento é executado antes do início da compilação.|
|`PreLinkEvent`|Esse evento é executado antes de começa a etapa de link.|
|`PostBuildEvent`|Esse evento é executado após a conclusão da compilação.|

A tabela a seguir lista cada *uso no build* elemento:

|Elemento XML|Descrição|
|-----------------|-----------------|
|`PreBuildEventUseInBuild`|Especifica se deve executar o *pré-compilação* eventos.|
|`PreLinkEventUseInBuild`|Especifica se deve executar o *pré-vínculo* eventos.|
|`PostBuildEventUseInBuild`|Especifica se deve executar o *pós-compilação* eventos.|

## <a name="example"></a>Exemplo

O exemplo a seguir pode ser adicionado dentro do elemento de projeto do myproject. vcxproj arquivo criado no [passo a passo: Usando MSBuild para criar um projeto do Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md). Um *pré-Build* evento faz uma cópia de cpp; um *pré-vínculo* evento faz uma cópia de Main; e um *pós-compilação* evento faz uma cópia do myproject.exe. Se o projeto é compilado usando uma configuração de versão, os eventos de build serão executados. Se o projeto é compilado usando uma configuração de depuração, os eventos de build não são executados.

```
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

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)<br/>
[Passo a passo: Usando o MSBuild para criar um projeto em Visual C++](../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)
