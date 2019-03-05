---
title: Opções, Assistente de controle ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.control.options
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
ms.openlocfilehash: 1dd136739162c72d8064deb9b1498794f1985e1b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282975"
---
# <a name="options-atl-control-wizard"></a>Opções, Assistente de controle ATL

Use esta página do Assistente para definir o tipo de controle que você está criando e o nível de suporte de interface que ele contém.

## <a name="uielement-list"></a>Lista UIElement

### <a name="control-type"></a>Tipo de controle

O tipo de controle que você deseja criar.

- **Controle padrão**: Um controle ActiveX.

- **Controle de composição**: Um controle ActiveX que pode conter (semelhante a uma caixa de diálogo) outros controles ActiveX ou controles do Windows. Um controle composto inclui o seguinte:

  - Um modelo para a caixa de diálogo que implementa o controle de composição.

  - Um recurso personalizado, registro, que registra automaticamente o controle composto quando invocado.

  - Uma classe C++ que implementa o controle de composição.

  - Uma interface COM, exposta pelo controle de composição.

  - Uma página de teste HTML que contém o controle de composição.

    Por padrão, esse controle define [CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) como true, para indicar que este é um controle da janela. Ele implementa um mapa coletor. Para obter mais informações, consulte [suporte para controle DHTML](../../atl/atl-support-for-dhtml-controls.md).

- **Controle DHTML**: Um controle DHTML ATL Especifica a interface do usuário, usando HTML. A classe de UI DHTML contém um mapa COM. Por padrão, esse controle define [CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) como true, para indicar que este é um controle da janela.

   Para obter mais informações, consulte [identificando os elementos do projeto de controle DHTML](../../atl/identifying-the-elements-of-the-dhtml-control-project.md).

### <a name="minimal-control"></a>Controle mínimo

Dá suporte a apenas as interfaces que são absolutamente necessários para a maioria dos contêineres. Você pode definir **controle mínimo** para qualquer um dos tipos de controle: você pode criar um controle padrão mínimo, um controle de composição mínimo ou um controle DHTML mínimo.

### <a name="aggregation"></a>Agregação

Adiciona o suporte de agregação para o controle que você está criando. Para obter mais informações, consulte [agregação](../../atl/aggregation.md).

- **Sim**: Crie um controle que pode ser agregado.

- **Não**: Crie um controle que não pode ser agregado.

- **Somente**: Crie um controle que pode ser instanciado apenas por meio de agregação.

### <a name="threading-model"></a>Modelo de Threading

Especifica que o modelo de threading usado pelo controle.

- **Único**: O controle será executado somente no thread COM primário.

- **Apartment**: O controle pode ser criado em qualquer apartment de thread único. O padrão.

### <a name="interface"></a>Interface

O tipo de interface que para o contêiner expõe a esse controle.

- **Dupla**: Cria uma interface que expõe propriedades e métodos por meio de `IDispatch` e diretamente por meio de VTBL.

- **Personalizado**: Cria uma interface que expõe métodos diretamente por meio de um VTBL.

   Se você selecionar **personalizado**, em seguida, você pode especificar que o controle está **compatível com a automação**. Se você selecionar **compatível com a automação**, em seguida, o assistente adiciona as [oleautomation](../../windows/oleautomation.md) de atributo na interface em IDL, e a interface pode ser empacotada pelo empacotador universal em oleaut32.dll. Ver [Marshaling detalhes](/windows/desktop/com/marshaling-details) no SDK do Windows para obter mais informações.

   Além disso, se você selecionar **compatível com a automação**, em seguida, todos os parâmetros para todos os métodos no controle devem ser VARIANT compatível.

### <a name="support"></a>Suporte

Define o suporte a diverso adicional para o controle.

- **Pontos de Conexão**: Permite que os pontos de conexão para seu objeto, fazendo a classe do seu objeto derivam [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) e permitindo que ele expõe uma interface de origem.

- **Licenciado**: Adiciona suporte para o controle para o [licenciamento](/windows/desktop/com/licensing). Controles licenciados só podem ser hospedados, se o computador cliente tem a licença correta.

## <a name="see-also"></a>Consulte também

[Assistente de Controle da ATL](../../atl/reference/atl-control-wizard.md)
