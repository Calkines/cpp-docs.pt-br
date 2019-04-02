---
title: Configurar as sessões de depuração do CMake no Visual Studio
ms.date: 03/21/2019
helpviewer_keywords:
- CMake debugging
ms.openlocfilehash: 712728247c439c38d5e640118fc153cf89647c80
ms.sourcegitcommit: 42e65c171aaa17a15c20b155d22e3378e27b4642
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356160"
---
# <a name="configure-cmake-debugging-sessions"></a>Configurar sessões de depuração do CMake

Todos os destinos executáveis do CMake são mostrados na lista suspensa **Item de Inicialização** na barra de ferramentas **Geral**. Para iniciar uma sessão de depuração, basta selecionar um e iniciar o depurador.

![Lista suspensa de item de inicialização do CMake](media/cmake-startup-item-dropdown.png "CMake startup item dropdown")

Inicie também uma sessão de depuração por meio dos menus do CMake.

## <a name="customize-debugger-settings"></a>Personalizar configurações do depurador

Para personalizar as configurações do depurador para qualquer destino executável do CMake no projeto, clique com o botão direito do mouse no arquivo CMakeLists.txt específico e selecione **Configurações de Depuração e de Inicialização**. (Ou selecione um destino no **exibição de destinos** na **Gerenciador de soluções**.) Quando você seleciona um destino do CMake no submenu, um arquivo chamado **Launch** é criado. Esse arquivo é pré-populado com informações sobre o destino do CMake selecionado e permite que você especifique parâmetros adicionais, como argumentos de programa ou o tipo de depurador. Para referenciar qualquer chave em um **Cmakesettings** do arquivo, preceda-o com `cmake.` na **Launch**. O exemplo a seguir mostra um simples **Launch** arquivo que recebe o valor da `remoteCopySources` chave no **Cmakesettings** arquivo para a configuração selecionada no momento:

```json
{
  "version": "0.2.1",
  "defaults": {},
  "configurations": [
    {
      "type": "default",
      "project": "CMakeLists.txt",
      "projectTarget": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "name": "CMakeHelloWorld.exe (Debug\\CMakeHelloWorld.exe)",
      "args": ["${cmake.remoteCopySources}"]
    }
  ]
}
```

Assim que você salva o **Launch** arquivo, em que uma entrada é criada a **Item de inicialização** lista suspensa com o novo nome. Editando a **Launch** arquivo, você pode criar quantas configurações de depuração que desejar para qualquer número de destinos do CMake.

## <a name="support-for-cmakesettings-variables"></a>Suporte para variáveis de CMakeSettings

 **Launch** dá suporte a variáveis que são declaradas no **Cmakesettings** (veja abaixo) e que são aplicáveis à configuração selecionada no momento. Também contém uma chave chamada `currentDir`, que define o diretório atual do aplicativo a ser iniciado:

```json
{
  "type": "default",
  "project": "CMakeLists.txt",
  "projectTarget": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "name": "CMakeHelloWorld1.exe (C:\\Users\\satyan\\CMakeBuilds\\Test\\Debug\\CMakeHelloWorld1.exe)",
  "currentDir": "${env.USERPROFILE}\\CMakeBuilds\\${workspaceHash}"
}
```

Quando você executa o aplicativo, o valor de `currentDir` é algo semelhante a

```cmd
C:\Users\satyan\7f14809a-2626-873e-952e-cdf038211175\
```
## <a name="see-also"></a>Consulte também

[Projetos do CMake no Visual Studio](cmake-projects-in-visual-studio.md)<br/>
[Configurar um projeto do Linux CMake](../linux/cmake-linux-project.md)<br/>
[Conectar-se ao computador Linux remoto](../linux/connect-to-your-remote-linux-computer.md)<br/>
[Personalizar as configurações de compilação do CMake](customize-cmake-settings.md)<br/>
[Configurar sessões de depuração do CMake](configure-cmake-debugging-sessions.md)<br/>
[Implantar, executar e depurar o projeto do Linux](../linux/deploy-run-and-debug-your-linux-project.md)<br/>
[Referência de configuração predefinida do CMake](cmake-predefined-configuration-reference.md)<br/>