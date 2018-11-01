---
title: Assemblies mistos (nativos e gerenciados)
ms.date: 09/18/2018
helpviewer_keywords:
- interop [C++], mixed assemblies
- /clr compiler option [C++], mixed assemblies
- managed code [C++], interoperability
- interoperability [C++], mixed assemblies
- mixed DLL loading [C++]
- mixed assemblies [C++], about mixed assemblies
- assemblies [C++], mixed
- mixed assemblies [C++]
- native code [C++], .NET interoperatibility
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
ms.openlocfilehash: 78e95177282804369bac2065582a06b8acbc975b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428661"
---
# <a name="mixed-native-and-managed-assemblies"></a>Assemblies mistos de (nativos e gerenciados)

Assemblies mistos são capazes de conter instruções de máquina não gerenciada e instruções MSIL. Isso lhes permite chamar e ser chamado por componentes do .NET, enquanto mantém a compatibilidade com bibliotecas de C++ nativas. Usando assemblies mistos, os desenvolvedores poderão criar aplicativos que usam uma mistura de .NET e o código C++ nativo.

Por exemplo, uma biblioteca existente que consistam inteiramente de código C++ nativo pode ser colocada na plataforma .NET por meio da recompilação apenas um módulo com o **/clr** comutador de compilador. Esse módulo, em seguida, é possível usar os recursos do .NET, mas permanece compatível com o restante do aplicativo. Também é possível decidir entre a compilação gerenciada e nativa em uma base de função por função dentro do mesmo arquivo (consulte [gerenciado, não gerenciado](../preprocessor/managed-unmanaged.md)).

Visual C++ suporta somente a geração de assemblies gerenciados mistos, usando o **/clr** opção de compilador. O **/clr: pure** e **/CLR: safe** opções do compilador são preteridas no Visual Studio 2015 e sem suporte no Visual Studio 2017. Se você precisar de assemblies gerenciados puros ou verificáveis, é recomendável que criá-las usando c#.

A geração dos três tipos distintos de assemblies gerenciados com suporte de versões anteriores do conjunto de ferramentas de compilador do Visual C++: mistas, puras e verificáveis. O último dois são discutidos [código puro e verificável (C + + c++ CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md).

## <a name="in-this-section"></a>Nesta seção

[Como: migrar para /clr](../dotnet/how-to-migrate-to-clr.md)<br/>
Descreve as etapas recomendadas para introdução ou atualizando a funcionalidade do .NET em seu aplicativo.

[Como: compilar MFC e ATL código, usando /clr](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
Discute como compilar programas existentes do MFC e ATL para direcionar o Common Language Runtime.

[Inicialização de assemblies mistos](../dotnet/initialization-of-mixed-assemblies.md)<br/>
Descreve o problema de "bloqueio do carregador" e soluções.

[Suporte de biblioteca para assemblies mistos](../dotnet/library-support-for-mixed-assemblies.md)<br/>
Discute como usar bibliotecas nativas em **/clr** compilações.

[Considerações sobre desempenho](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
Descreve as implicações de desempenho de assemblies mistos e marshaling de dados.

[Domínios de aplicativo e Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
Discute o suporte do Visual C++ para domínios do aplicativo.

[Conversão dupla](../dotnet/double-thunking-cpp.md)<br/>
Discute as implicações de desempenho de um ponto de entrada nativo para uma função gerenciada.

[Evitando exceções no CLR desligamento ao consumo dos objetos COM criados com /clr](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
Discute como obter um desligamento correto de um aplicativo gerenciado que consome um objeto COM compilados com **/clr**.

[Como criar um aplicativo parcialmente confiável removendo a dependência da DLL da biblioteca CRT](../dotnet/create-a-partially-trusted-application.md)<br/>
Discute como criar um aplicativo parcialmente confiável do Common Language Runtime usando o Visual C++, removendo a dependência no msvcm90.dll.

Para obter mais informações sobre diretrizes de codificação para assemblies mistos, consulte o artigo do MSDN [uma visão geral de gerenciado/não gerenciado interoperabilidade entre código](https://msdn.microsoft.com/library/ms973872.aspx).

## <a name="see-also"></a>Consulte também

- [Interoperabilidade entre .NET e nativo](../dotnet/native-and-dotnet-interoperability.md)
