---
title: Vincular um executável a uma DLL
ms.date: 11/04/2016
helpviewer_keywords:
- run time [C++], linking
- dynamic load linking [C++]
- linking [C++], DLLs
- DLLs [C++], linking
- implicit linking [C++]
- explicit linking [C++]
- executable files [C++], linking to DLLs
- loading DLLs [C++]
ms.assetid: 7592e276-dd6e-4a74-90c8-e1ee35598ea3
ms.openlocfilehash: fc7a676059af17e7a42189c7c15ca157a081e08a
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "57818356"
---
# <a name="link-an-executable-to-a-dll"></a>Vincular um executável a uma DLL

Um arquivo executável vincula (ou carrega) uma DLL em uma das duas maneiras:

- *Vinculação implícita*, em que o sistema operacional carrega a DLL quando o executável usando ele é carregado. O executável do cliente chama as funções exportadas da DLL, como se as funções foram estaticamente vinculadas e contidas no executável. Vinculação implícita às vezes chamamos *carregamento estático* ou *vinculação dinâmica em tempo de carregamento*.

- *A vinculação explícita*, em que o sistema operacional carrega a DLL sob demanda no tempo de execução. Um executável que usa uma DLL por meio da vinculação explícita deve fazer chamadas de função para carregar e descarregar a DLL explicitamente e acessar as funções exportadas pela DLL. Ao contrário das chamadas para funções em uma biblioteca vinculada estaticamente, o executável do cliente deve chamar as funções exportadas em uma DLL por meio de um ponteiro de função. A vinculação explícita é, às vezes, conhecida como *dinâmico de carga* ou *vinculação dinâmica em tempo de execução*.

Um executável pode usar qualquer método de vinculação para vincular a mesma DLL. Além disso, esses métodos não são mutuamente excludentes; um executável pode implicitamente vincular a uma DLL e outro pode anexar a ele explicitamente.

<a name="determining-which-linking-method-to-use"></a>

## <a name="link-an-executable-to-a-dll"></a>Vincular um executável a uma DLL

Se deseja usar a vinculação implícita ou explícita de vinculação é uma decisão de arquitetura que você deve fazer para seu aplicativo. Há vantagens e desvantagens em cada método.

### <a name="implicit-linking"></a>Vinculação implícita

Vinculação implícita ocorre quando o código de um aplicativo chama uma função DLL exportada. Quando o código-fonte para o executável de chamada é compilado ou montado, a chamada de função DLL gera uma referência de função externa no código do objeto. Para resolver esta referência externa, o aplicativo deve vincular com a biblioteca de importação (arquivo. lib) fornecida pelo fabricante da DLL.

A biblioteca de importação contém apenas o código para carregar a DLL e para implementar chamadas para funções na DLL. Localizando uma função externa em uma biblioteca de importação informa o vinculador que o código da função está em uma DLL. Para resolver referências externas para DLLs, o vinculador simplesmente adiciona informações para o arquivo executável que informa ao sistema onde encontrar o código da DLL, quando o processo é iniciado.

Quando o sistema inicia um programa que contém referências vinculadas dinamicamente, ele usa as informações no arquivo executável do programa para localizar as DLLs necessárias. Se ele não é possível localizar a DLL, o sistema encerra o processo e exibe uma caixa de diálogo que relata o erro. Caso contrário, o sistema mapeia os módulos da DLL no espaço de endereço do processo.

Se qualquer uma das DLLs tem uma função de ponto de entrada para o código de inicialização e término, como `DllMain`, o sistema operacional chama a função. Um dos parâmetros passados para a função de ponto de entrada especifica um código que indica a DLL está relacionada a anexar ao processo. Se a função de ponto de entrada não retornar TRUE, o sistema encerra o processo e relata o erro.

Por fim, o sistema modifica o código executável do processo para fornecer endereços iniciais para as funções de DLL.

Como o restante do código de um programa, o código da DLL é mapeado no espaço de endereço do processo de quando o processo é iniciado e ele é carregado na memória apenas quando necessário. Como resultado, o `PRELOAD` e `LOADONCALL` atributos de código usados por arquivos. def para controle de carregamento nas versões anteriores do Windows não têm significado.

### <a name="explicit-linking"></a>A vinculação explícita

A maioria dos aplicativos usa a vinculação implícita, porque ele é o método de vinculação mais fácil usar. No entanto, há ocasiões em que a vinculação explícita é necessária. Aqui estão algumas razões comuns para usar a vinculação explícita:

- O aplicativo não sabe o nome de uma DLL que ele carrega até o tempo de execução. Por exemplo, o aplicativo pode obter o nome da DLL e as funções exportadas de um arquivo de configuração na inicialização.

- Um processo que usa a vinculação implícita é encerrado pelo sistema operacional, se a DLL não for encontrada na inicialização do processo. Um processo que usa a vinculação explícita não é encerrado nessa situação e pode tentar se recuperar do erro. Por exemplo, o processo pode notificar o usuário sobre o erro e peça que o usuário especifique outro caminho para a DLL.

- Um processo que usa a vinculação implícita também será finalizado se qualquer uma das DLLs é vinculada para ter um `DllMain` função falhará. Um processo que usa a vinculação explícita não é encerrado nessa situação.

- Um aplicativo que implicitamente contém links para várias DLLs pode ser lento para ser iniciado porque o Windows carrega todas as DLLs quando o carregamento do aplicativo. Para melhorar o desempenho de inicialização, um aplicativo pode implicitamente vincular somente para as DLLs necessárias imediatamente após o carregamento e aguarde até que outras DLLs são necessárias para vinculá-las explicitamente.

- A vinculação explícita elimina a necessidade para vincular o aplicativo usando uma biblioteca de importação. Se as alterações na DLL fazer com que os ordinais de exportação alterar, aplicativos que usam a vinculação explícita não é necessário vincular novamente se eles chamam `GetProcAddress` usando o nome de uma função e não é um valor ordinal, enquanto os aplicativos que usam a vinculação implícita necessário vincular novamente para o nova biblioteca de importação.

Aqui estão dois riscos da vinculação explícita para estar atento:

- Se a DLL tem uma `DllMain` função de ponto de entrada, o sistema operacional chama a função no contexto do thread que chamou `LoadLibrary`. A função de ponto de entrada não é chamada se a DLL já está anexada ao processo devido a uma chamada anterior a `LoadLibrary` que não teve nenhuma chamada correspondente para o `FreeLibrary` função. A vinculação explícita pode causar problemas se a DLL usa um `DllMain` função para executar a inicialização para cada thread de um processo porque threads que já existem quando `LoadLibrary` (ou `AfxLoadLibrary`) é chamado não são inicializados.

- Se uma DLL declara os dados de extensão estático como `__declspec(thread)`, ele pode causar uma falha de proteção se explicitamente vinculado. Depois que a DLL é carregada por uma chamada para `LoadLibrary`, ele faz com que uma falha de proteção sempre que o código faz referência a esses dados. (Incluem itens estáticos globais e locais de dados de extensão estático.) Portanto, quando você cria uma DLL, você deve evitar o uso de armazenamento local de thread ou informar os usuários DLL sobre as possíveis armadilhas de carregamento dinâmico de sua DLL. Para obter mais informações, consulte [usando o armazenamento local de thread em uma biblioteca de vínculo dinâmico (Windows SDK)](/windows/desktop/Dlls/using-thread-local-storage-in-a-dynamic-link-library).

<a name="linking-implicitly"></a>

## <a name="link-an-executable-to-a-dll"></a>Vincular um executável a uma DLL

Para usar uma DLL por meio da vinculação implícita, executáveis de cliente devem obter esses arquivos com o provedor da DLL:

- Um ou mais arquivos de cabeçalho (arquivos. h) que contêm as declarações dos dados exportados, funções e/ou classes do C++ na DLL. As classes, funções e dados exportados pela DLL devem ser marcados `__declspec(dllimport)` no arquivo de cabeçalho. Para obter mais informações, consulte [dllexport, dllimport](../cpp/dllexport-dllimport.md).

- Uma biblioteca de importação para vincular no executável. O vinculador cria a biblioteca de importação quando a DLL é compilada. Para obter mais informações, consulte [. Os arquivos LIB](reference/dot-lib-files-as-linker-input.md).

- O arquivo DLL real.

Para usar uma DLL por meio da vinculação implícita, um executável deve incluir os arquivos de cabeçalho que declaram os dados, funções ou classes exportadas pela DLL em cada arquivo de origem que contém as chamadas para os dados exportados, funções e classes do C++. De uma perspectiva de codificação, chamadas para as funções exportadas são como qualquer outra chamada de função.

Para criar o arquivo executável de chamada, você deve vincular com a biblioteca de importação. Se você usa um makefile externo ou sistema de compilação, especifique o nome do arquivo de biblioteca de importação onde você lista outros arquivos de objeto (. obj) ou bibliotecas que pode ser vinculada.

O sistema operacional deve ser capaz de localizar o arquivo DLL quando ele carrega o executável de chamada. Isso significa que seu aplicativo deve implantar ou verificar a existência da DLL quando seu aplicativo está instalado.

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>Como vincular explicitamente para uma DLL

Para usar uma DLL por meio da vinculação explícita, aplicativos devem fazer uma chamada de função para carregar explicitamente a DLL em tempo de execução. Para vincular explicitamente para uma DLL, um aplicativo deve:

- Chame [LoadLibrary](loadlibrary-and-afxloadlibrary.md), `LoadLibraryEx`, ou uma função semelhante para carregar a DLL e obter um identificador de módulo.

- Chame [GetProcAddress](getprocaddress.md) obter um ponteiro de função para cada função que o aplicativo chama exportada. Porque os aplicativos chamam as funções de DLL por meio de um ponteiro, o compilador não gera as referências externas, portanto, não é necessário para vincular com uma biblioteca de importação. No entanto, você deve ter uma `typedef` ou `using` instrução que define a assinatura de chamada das funções exportadas que você chamar.

- Chame [FreeLibrary](freelibrary-and-afxfreelibrary.md) quando terminar com a DLL.

Por exemplo, essa função de exemplo chama `LoadLibrary` para carregar uma DLL denominada "MyDLL", chamadas `GetProcAddress` para obter um ponteiro para uma função chamada "DLLFunc1", chama a função e salva o resultado e, em seguida, chama `FreeLibrary` descarregar a DLL.

```C
#include "windows.h"

typedef HRESULT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT*);

HRESULT LoadAndCallSomeFunction(DWORD dwParam1, UINT * puParam2)
{
    HINSTANCE hDLL;               // Handle to DLL
    LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer
    HRESULT hrReturnVal;

    hDLL = LoadLibrary("MyDLL");
    if (NULL != hDLL)
    {
        lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL, "DLLFunc1");
        if (NULL != lpfnDllFunc1)
        {
            // call the function
            hrReturnVal = lpfnDllFunc1(dwParam1, puParam2);
        }
        else
        {
            // report the error
            hrReturnVal = ERROR_DELAY_LOAD_FAILED;
        }
        FreeLibrary(hDLL);
    }
    else
    {
        hrReturnVal = ERROR_DELAY_LOAD_FAILED;
    }
    return hrReturnVal;
}
```

Ao contrário de neste exemplo, na maioria dos casos você deve chamar `LoadLibrary` e `FreeLibrary` apenas uma vez no seu aplicativo para uma DLL de determinado, especialmente se você pretende chamar várias funções na DLL ou DLL de chamar funções repetidamente.

## <a name="what-do-you-want-to-know-more-about"></a>Que mais você deseja saber?

- [Trabalhando com bibliotecas de importação e arquivos de exportação](reference/working-with-import-libraries-and-export-files.md)

- [Ordem de pesquisa de biblioteca de vínculo dinâmico](/windows/desktop/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>Consulte também

[DLLs no Visual C++](dlls-in-visual-cpp.md)
