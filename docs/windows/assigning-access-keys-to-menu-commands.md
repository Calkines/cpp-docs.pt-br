---
title: Atribuindo teclas de acesso a comandos de Menu (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- access keys [C++], checking
- menus [C++], shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics [C++], adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics [C++], uniqueness checking
- Check Mnemonics command
ms.assetid: fbcf1a00-af6a-4171-805a-0ac01d4e8b0d
ms.openlocfilehash: 7a3302f7744bf5c3a0cbaac96de04d9f649fac10
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587324"
---
# <a name="assigning-access-keys-to-menu-commands-c"></a>Atribuindo teclas de acesso a comandos de Menu (C++)

Em um projeto do C++, você pode atribuir uma chave de acesso (um mnemônico que permite ao usuário selecionar o menu com o teclado) para seus menus e comandos de menu.

### <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>Para atribuir uma chave de acesso (atalho) a um comando de menu

1. Digite um e comercial (`&`) na frente de uma letra no nome do menu ou nome do comando para especificar essa letra como a chave de acesso correspondente. Por exemplo "& do arquivo" conjuntos **Alt**+**F** como a tecla de atalho para o **arquivo** menu em aplicativos escritos para Microsoft Windows.

   O item de menu fornecerá uma indicação visível de que uma das letras tenha uma tecla de atalho atribuída a ele. A seguinte letra que o e comercial será exibido sublinhado (contingente no sistema operacional).

   > [!NOTE]
   > Verifique se todas as chaves de acesso em um menu são exclusivas, menu do botão direito do mouse e escolhendo **Verificar mnemônicos** no menu de atalho.

Para obter informações sobre como adicionar recursos a projetos gerenciados, consulte [recursos em aplicativos de área de trabalho](/dotnet/framework/resources/index) na *guia do desenvolvedor do .NET Framework*. Para obter informações sobre como adicionar manualmente os arquivos de recursos a projetos gerenciados, acessar recursos, exibir recursos estáticos e atribuir cadeias de caracteres de recurso a propriedades, consulte [criando arquivos de recursos para aplicativos de área de trabalho](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obter informações sobre globalização e localização de recursos em aplicativos gerenciados, consulte [Globalizing e Localizando aplicativos do .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Consulte também

[Editor de Menu](../windows/menu-editor.md)