---
title: Desenvolvimento da UWP com C++
ms.date: 03/13/2019
ms.openlocfilehash: c6b92a3b85c08bc2d43ad297c410445ea974822b
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58783931"
---
# <a name="uwp-development-with-c"></a>Desenvolvimento da UWP com C++

A Universal Windows Platform (UWP) é a interface de programação modernos para Windows. Com UWP, você escreve um aplicativo ou componente once e implantá-lo em qualquer dispositivo Windows 10. Você pode escrever um componente em C++ e os aplicativos escritos em qualquer outra linguagem compatível com a UWP podem usá-lo.

A maioria da documentação do UWP está na árvore de conteúdo do Windows no [documentação da plataforma Universal do Windows](/windows/uwp/). Lá você encontrará tutoriais de início, bem como documentação de referência. 

Para novos aplicativos UWP e componentes, é recomendável que você use [C + + c++ /CLI WinRT](/windows/uwp/cpp-and-winrt-apis/), uma novo padrão C + + 17 projeção de linguagem para APIs do Windows Runtime. C + + c++ /CLI WinRT está disponível no SDK do Windows 10, versão 1803 em diante. C + + c++ /CLI WinRT é implementado inteiramente em arquivos de cabeçalho e foi projetado para fornecer acesso de primeira classe à moderna API do Windows.

O conteúdo nesse local aborda duas tecnologias mais antigas do UWP do C++:

- o [C + + / extensão da linguagem c++ /CX](visual-c-language-reference-c-cx.md)
- o [biblioteca de modelos C++ do Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

Essas tecnologias continuarão a ter suporte, mas geralmente não são recomendados para novo desenvolvimento.

## <a name="related-articles"></a>Artigos relacionados
[Introdução aos aplicativos do Windows 10](/windows/uwp/get-started/)
[começar com C + + c++ /CLI WinRT](/windows/uwp/cpp-and-winrt-apis/get-started)