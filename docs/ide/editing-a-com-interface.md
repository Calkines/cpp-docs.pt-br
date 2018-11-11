---
title: Editando uma interface COM
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.com.editing.interfaces
helpviewer_keywords:
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 6c2909e0-af2d-4a37-bb39-ed372e6129cf
ms.openlocfilehash: 338782cbf7cc302c285e8e778389ae28e20f2b14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657360"
---
# <a name="editing-a-com-interface"></a>Editando uma interface COM

Usando comandos do menu de atalho de Modo de Exibição de Classe, você pode definir novos métodos e novas propriedades para as interfaces COM nos projetos do Visual C++. Além disso, na Caixa de Ferramentas, você pode definir eventos para controles ActiveX.

Para classes de objeto COM baseadas em ATL e MFC, você pode editar a implementação da classe ao mesmo tempo que edita a interface.

> [!NOTE]
>  Para as interfaces definidas fora da caixa de diálogo **Adicionar Classe**, o Visual C++ adiciona os métodos ou as propriedades ao arquivo .idl e adiciona stubs às classes que implementam métodos, mesmo quando as interfaces são adicionadas manualmente.

Os três assistentes a seguir ajudarão você a personalizar as interfaces existentes. Eles estão disponíveis em Modo de Exibição de Classe:

|Wizard|Tipo de projeto|
|------------|------------------|
|[Assistente de Adição de Propriedade](../ide/names-add-property-wizard.md)|Projetos ATL ou MFC que dão suporte à ATL. Clique com o botão direito do mouse na interface à qual deseja adicionar a propriedade.<br /><br />O Visual C++ detecta o tipo de projeto e modifica as opções do Assistente de Adição de Propriedade de acordo:<br /><br />- Para dispinterfaces em projetos criados usando o [Assistente de Aplicativo MFC](../mfc/reference/mfc-application-wizard.md), a invocação do Assistente de Adição de Propriedade fornece opções específicas ao MFC.<br />- Para interfaces de controle ActiveX do MFC, o Assistente de Adição de Propriedade fornece uma lista de métodos e propriedades de estoque que você pode usar, conforme fornecido, ou personalizar para o controle.<br />- Para todas as outras interfaces, os Assistentes de Adição de Propriedade fornecem opções úteis na maioria das situações.|
|[Assistente de Adição de Método](../ide/add-method-wizard.md)|Projetos ATL ou MFC que dão suporte à ATL. Clique com o botão direito do mouse na interface à qual deseja adicionar o método.<br /><br />O Visual C++ detecta o tipo de projeto e modifica as opções do Assistente de Adição de Método de acordo:<br /><br />- Para dispinterfaces em projetos criados usando o [Assistente de Aplicativo MFC](../mfc/reference/mfc-application-wizard.md), a invocação do Assistente de Adição de Método fornece opções específicas ao MFC.<br />- Para interfaces de controle ActiveX do MFC, o Assistente de Adição de Método fornece uma lista de métodos e propriedades de estoque que você pode usar, conforme fornecido, ou personalizar para o controle.<br />- Para todas as outras interfaces, os assistentes de **Adição de Método** fornecem opções úteis na maioria das situações.|

Além disso, você pode implementar novas interfaces no controle COM clicando com o botão direito do mouse na classe de controle do objeto em Modo de Exibição de Classe e clicando em [Implementar Interface](../ide/implement-interface-wizard.md).

## <a name="see-also"></a>Consulte também

[Trabalhando com arquivos de recurso](../windows/working-with-resource-files.md)<br>
[Adicionando funcionalidade com assistentes de código](../ide/adding-functionality-with-code-wizards-cpp.md)<br>
[Tipos de projeto do Visual C++](../ide/visual-cpp-project-types.md)