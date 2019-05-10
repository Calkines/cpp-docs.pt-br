---
title: LoadLibrary e AfxLoadLibrary
ms.date: 05/24/2018
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: 661d7742fb0fedae45bc063ba3821193d6c5438e
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220616"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary e AfxLoadLibrary

Processa a chamada [LoadLibraryExA](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa) ou [LoadLibraryExW](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexw)(ou [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) para vincular explicitamente para uma DLL. Se a função obtiver êxito, ele mapeará a DLL especificada no espaço de endereço do processo de chamada e retorna um identificador para a DLL que pode ser usada com outras funções em vinculação explícita — por exemplo, `GetProcAddress` e `FreeLibrary`.

`LoadLibrary` tenta localizar o DLL usando a mesma sequência de pesquisa que é usada para vínculo implícito. Se o sistema não é possível localizar a DLL ou se a função de ponto de entrada retornar FALSE, `LoadLibrary` retorna NULL. Se a chamada para `LoadLibrary` Especifica um módulo DLL que já está mapeado no espaço de endereço do processo de chamada, a função retornará uma alça de DLL e incrementará a contagem de referência do módulo.

Se a DLL tem uma função de ponto de entrada, o sistema operacional chama a função no contexto do thread que chamou `LoadLibrary`. A função de ponto de entrada não é chamada se a DLL já está anexada ao processo devido a uma chamada anterior a `LoadLibrary` que tem sem chamada correspondente para o `FreeLibrary` função.

Para aplicativos MFC que carregam DLLs de extensão do MFC, é recomendável que você use `AfxLoadLibrary` em vez de `LoadLibrary`. `AfxLoadLibrary` identificadores de sincronização de thread antes de chamar `LoadLibrary`. A interface (protótipo de função) para `AfxLoadLibrary` é o mesmo que `LoadLibrary`.

Se o Windows não é possível carregar a DLL, o processo pode tentar recuperar do erro. Por exemplo, o processo pode notificar o usuário sobre o erro e solicitar que o usuário especifique outro caminho para a DLL.

> [!IMPORTANT]
> Certifique-se de especificar o caminho completo de todas as DLLs. O diretório atual é pesquisado primeiro quando arquivos são carregados. Se você não qualificar o caminho do arquivo, talvez seja possível carregar um arquivo que não seja o pretendido. Outra maneira de evitar isso é usando o [/DEPENDENTLOADFLAG](reference/dependentloadflag.md) a opção de vinculador.

## <a name="what-do-you-want-to-do"></a>O que você deseja fazer?

- [Vincular um executável a uma DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Vincular um executável a uma DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Que mais você deseja saber?

- [Ordem de pesquisa de biblioteca de vínculo dinâmico](/windows/desktop/Dlls/dynamic-link-library-search-order)

- [FreeLibrary e AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Consulte também

- [Criar DLLs de C/C++ no Visual Studio](dlls-in-visual-cpp.md)
