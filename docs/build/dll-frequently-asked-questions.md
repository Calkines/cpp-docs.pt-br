---
title: Perguntas frequentes sobre DLL do MFC
ms.date: 05/06/2019
helpviewer_keywords:
- troubleshooting [C++], DLLs
- DLLs [C++], frequently asked questions
- FAQs [C++], DLLs
ms.assetid: 09dd068e-fc33-414e-82f7-289c70680256
ms.openlocfilehash: 9108aaf3fcface847b0391455a2aecd4d45658c4
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220941"
---
# <a name="dll-frequently-asked-questions"></a>Perguntas frequentes sobre DLL

A seguir está algumas perguntas frequentes (FAQ) sobre DLLs.

- [Uma DLL MFC pode criar vários threads?](#mfc_multithreaded_1)

- [Um aplicativo multithread pode acessar uma DLL MFC em threads diferentes?](#mfc_multithreaded_2)

- [Existem classes do MFC ou funções que não podem ser usadas em uma DLL MFC?](#mfc_prohibited_classes)

- [Quais técnicas de otimização devo usar para melhorar o desempenho do aplicativo cliente durante o carregamento?](#mfc_optimization)

- [Há um vazamento de memória na minha DLL MFC regular, mas meu código parece funcionar normalmente. Como encontrar o vazamento de memória?](#memory_leak)

## <a name="mfc_multithreaded_1"></a> Uma DLL MFC pode criar vários threads?

Exceto durante a inicialização, uma DLL MFC pode crie com segurança vários threads desde que ele usa o armazenamento local (TLS) funções, como o thread de Win32 **TlsAlloc** para alocar o armazenamento local de thread. No entanto, se usar uma DLL MFC **__declspec(thread)** para alocar o armazenamento local de thread, o aplicativo cliente deve ser vinculado implicitamente para a DLL. Se o aplicativo cliente explicitamente links para a DLL, a chamada para **LoadLibrary** não serão carregados com êxito a DLL. Para obter mais informações sobre variáveis de thread local em DLLs, consulte [thread](../cpp/thread.md).

Uma DLL do MFC que cria um novo thread MFC durante a inicialização irá parar de responder quando ele é carregado por um aplicativo. Isso inclui o sempre que um thread é criado chamando `AfxBeginThread` ou `CWinThread::CreateThread` dentro de:

- O `InitInstance` de um `CWinApp`-objeto em uma DLL MFC regular derivado.

- Um fornecido `DllMain` ou **RawDllMain** função em uma DLL MFC regular.

- Um fornecido `DllMain` ou **RawDllMain** função em uma DLL de extensão do MFC.

## <a name="mfc_multithreaded_2"></a> Um aplicativo multithread pode acessar uma DLL MFC em threads diferentes?

Aplicativos de vários threads podem acessar DLLs MFC regulares vinculadas dinamicamente ao MFC e DLLs de extensão do MFC de threads diferentes. Um aplicativo pode acessar as DLLs MFC regulares que se vinculam estaticamente ao MFC de vários threads criados no aplicativo.

## <a name="mfc_prohibited_classes"></a> Existem classes do MFC ou funções que não podem ser usadas em uma DLL MFC?

Uso de DLLs de extensão o `CWinApp`-derivado da classe do aplicativo cliente. Eles não devem ter suas próprias `CWinApp`-classe derivada.

DLLs MFC regulares deve ter um `CWinApp`-derivado de classe e um único objeto dessa classe de aplicativo, assim como um aplicativo do MFC. Ao contrário do `CWinApp` objeto de um aplicativo, o `CWinApp` objeto da DLL não tem uma bomba de mensagem principal.

Observe que, como o `CWinApp::Run` mecanismo não se aplica a uma DLL, o aplicativo que detém a bomba de mensagem principal. Se a DLL abre caixas de diálogo sem janela restrita ou tem uma janela de quadro principal de seu próprio, bomba de mensagem principal do aplicativo deve chamar uma rotina exportada pela DLL, que por sua vez chama o `CWinApp::PreTranslateMessage` a função de membro de objeto de aplicativo da DLL.

## <a name="mfc_optimization"></a> Quais técnicas de otimização devo usar para aprimorar o aplicativo cliente&#39;no desempenho ao carregar s?

Se sua DLL for uma DLL MFC regular que está vinculado estaticamente ao MFC, alterá-lo como um regular vinculada dinamicamente ao MFC DLL do MFC reduz o tamanho do arquivo.

Se a DLL tem um grande número de funções exportadas, use um arquivo. def para exportar as funções (em vez de usar **dllexport**) e usar o arquivo. def [atributo NONAME](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) em cada função exportada. O atributo NONAME faz com que apenas o valor ordinal e não o nome da função a ser armazenado na tabela de exportação da DLL, que reduz o tamanho do arquivo.

DLLs vinculadas implicitamente a um aplicativo são carregadas quando o carregamento do aplicativo. Para melhorar o desempenho durante o carregamento, tente dividir a DLL em DLLs diferentes. Coloque todas as funções que o aplicativo de chamada precisa imediatamente após o carregamento em uma DLL e ter o aplicativo de chamada implicitamente vincular a essa DLL. Coloque as outras funções que o aplicativo de chamada não precisa imediatamente em outra DLL e ter o aplicativo vincule explicitamente para essa DLL. Para obter mais informações, consulte [vincular um executável a uma DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use).

## <a name="memory_leak"></a> Há&#39;s um vazamento de memória na minha DLL MFC regular, mas meu código parece funcionar normalmente. Como encontrar o vazamento de memória?

Uma possível causa da perda de memória é que o MFC cria objetos temporários que são usados dentro de funções de manipulador de mensagem. Em aplicativos MFC, esses objetos temporários são automaticamente limpos no `CWinApp::OnIdle()` função que é chamada entre o processamento de mensagens. No entanto, em bibliotecas de vínculo dinâmico (DLLs), do MFC a `OnIdle()` função não é chamada automaticamente. Como resultado, objetos temporários não são automaticamente limpos. Para limpar os objetos temporários, a DLL deve chamar explicitamente `OnIdle(1)` periodicamente.

## <a name="see-also"></a>Consulte também

[Criar DLLs de C/C++ no Visual Studio](dlls-in-visual-cpp.md)
