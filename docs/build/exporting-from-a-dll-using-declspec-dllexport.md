---
title: Exportando a partir de uma DLL usando __declspec(dllexport)
ms.date: 05/06/2019
f1_keywords:
- dllexport
- __declspec
helpviewer_keywords:
- __declspec(dllexport) keyword [C++]
- names [C++], DLL exports by
- export directives [C++]
- exporting DLLs [C++], __declspec(dllexport) keyword
ms.assetid: a35e25e8-7263-4a04-bad4-00b284458679
ms.openlocfilehash: 167060d0270004b8648d32af206865bfe66c3b4b
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220797"
---
# <a name="exporting-from-a-dll-using-declspecdllexport"></a>Exportando a partir de uma DLL usando __declspec(dllexport)

Você pode exportar dados, funções, classes ou funções de membro de classe de uma DLL usando o **dllexport** palavra-chave. **dllexport** adiciona a diretiva de exportação para o arquivo de objeto, você não precisa usar um arquivo. def.

Esta conveniência é mais aparente quando tentar exportar nomes de função de C++ decorados. Como não há nenhuma especificação padrão para a decoração de nome, o nome de uma função exportada pode alterar entre versões do compilador. Se você usar **dllexport**, recompilação da DLL e arquivos dependentes .exe é necessário apenas para conta quaisquer alterações de convenção de nomenclatura.

Muitas diretivas de exportação, como ordinais, NONAME e PRIVATE, podem ser feitas somente em um arquivo. def, e não é possível especificar esses atributos sem um arquivo. def. No entanto, usando **dllexport** além de usar um. def arquivo não causa erros de compilação.

Para exportar funções, o **dllexport** palavra-chave deve aparecer à esquerda da palavra-chave a convenção de chamada, se uma palavra-chave for especificada. Por exemplo:

```
__declspec(dllexport) void __cdecl Function1(void);
```

Para exportar todos os membros de dados públicos e funções de membro em uma classe, a palavra-chave deve aparecer à esquerda do nome da classe, da seguinte maneira:

```
class __declspec(dllexport) CExampleExport : public CObject
{ ... class definition ... };
```

> [!NOTE]
>  `__declspec(dllexport)` não pode ser aplicado a uma função com o `__clrcall` convenção de chamada.

Ao criar sua DLL, você normalmente cria um arquivo de cabeçalho que contém os protótipos de função e/ou classes que você está exportando e adiciona **dllexport** às declarações no arquivo de cabeçalho. Para tornar seu código mais legível, defina uma macro para **dllexport** e usar a macro com cada símbolo que você estiver exportando:

```
#define DllExport   __declspec( dllexport )
```

**dllexport** armazena nomes na tabela de exportação da DLL de função. Se você deseja otimizar o tamanho da tabela, consulte [exportar funções de uma DLL por Ordinal em vez de por nome](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

## <a name="what-do-you-want-to-do"></a>O que você deseja fazer?

- [Exportar de uma DLL usando arquivos. def](exporting-from-a-dll-using-def-files.md)

- [Exportar e importar usando AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportar funções de C++ para uso em executáveis da linguagem C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportar funções de C para uso em executáveis C ou da linguagem C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Determinar qual método de exportação usar](determining-which-exporting-method-to-use.md)

- [Importação para um aplicativo usando __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicialize um DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Que mais você deseja saber?

- [A palavra-chave declspec](../cpp/declspec.md)

- [Importação e exportação de funções embutidas](importing-and-exporting-inline-functions.md)

- [Importações mútuas](mutual-imports.md)

## <a name="see-also"></a>Consulte também

[Exportando de uma DLL](exporting-from-a-dll.md)
