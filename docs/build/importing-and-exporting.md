---
title: Importando e exportando
ms.date: 05/06/2019
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
ms.openlocfilehash: 03931f7f128ab0666890bb8e76677db67dda8fc7
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220635"
---
# <a name="importing-and-exporting"></a>Importando e exportando

Você pode importar os símbolos públicos para um aplicativo ou exportar funções de uma DLL usando dois métodos:

- Usar um arquivo de definição (. def) do módulo ao criar a DLL

- Use as palavras-chave **__declspec(dllimport)** ou **dllexport** em uma definição de função no aplicativo principal

## <a name="using-a-def-file"></a>Usando um arquivo. def

Um arquivo de definição de módulo (. def) é um arquivo de texto que contém uma ou mais declarações de módulo que descrevem vários atributos de uma DLL. Se você não usar **__declspec(dllimport)** ou **dllexport** para exportar funções de uma DLL, a DLL exige um arquivo. def.

Você pode usar arquivos. def [importar para um aplicativo](importing-using-def-files.md) ou a [exportar de uma DLL](exporting-from-a-dll-using-def-files.md).

## <a name="using-declspec"></a>Usando declspec

Não é necessário usar **__declspec(dllimport)** para seu código seja compilado corretamente, mas fazer isso permite que o compilador gere um código melhor. O compilador é capaz de gerar um código melhor, porque ele pode determinar se existe uma função em uma DLL ou não, que permite que o compilador a produzir um código que ignora um nível de indireção que normalmente estaria presente em uma chamada de função que cruzaram um limite de DLL. No entanto, você deve usar **__declspec(dllimport)** para importar as variáveis usadas em uma DLL.

Na seção de exportações do arquivo. def adequada, **dllexport** não é necessária. **dllexport** foi adicionada para fornecer uma maneira fácil de exportar funções de um arquivo. dll ou. .exe sem usar um arquivo. def.

O formato de executável portátil do Win32 é projetado para minimizar o número de páginas que devem ser tocados para corrigir as importações. Para fazer isso, ele coloca todos os endereços de importação para qualquer programa em um só lugar, chamado tabela de endereço de importação. Isso permite que o carregador modificar somente uma ou duas páginas ao acessar essas importações.

## <a name="what-do-you-want-to-do"></a>O que você deseja fazer?

- [Importar para um aplicativo](importing-into-an-application-using-declspec-dllimport.md)

- [Exportação de uma DLL](exporting-from-a-dll.md)

## <a name="see-also"></a>Consulte também

[Criar DLLs de C/C++ no Visual Studio](dlls-in-visual-cpp.md)
