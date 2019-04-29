---
title: Macros (C/C++)
ms.date: 11/04/2016
helpviewer_keywords:
- preprocessor
- preprocessor, macros
- Visual C++, preprocessor macros
ms.assetid: a7bfc5d4-2537-4fe0-bef0-70cec0b43388
ms.openlocfilehash: 281aaf686c07894b5cb1fab187ba903179c51de8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62371770"
---
# <a name="macros-cc"></a>Macros (C/C++)
Pré-processamento expande macros em todas as linhas que não são diretivas de pré-processador (linhas que não têm uma **#** como o primeiro caractere diferente de espaço em branco) e em partes de algumas políticas que não são ignoradas como parte de um compilação condicional. As políticas de “compilação condicional” permitem que você suprima a compilação de partes de um arquivo de origem testando uma expressão constante ou um identificador para determinar quais blocos de texto passam no compilador e que são removidos do arquivo de origem durante o pré-processamento.

A política `#define` normalmente é usada para associar identificadores significativos a constantes, palavras-chave e instruções ou expressões de uso geral. Os identificadores que representam constantes às vezes são chamados de “constantes simbólicas” ou “constantes de manifesto”. Os identificadores que representam instruções ou expressões são chamados de “macros”. Nesta documentação de pré-processador, somente o termo “macro” é usado.

Quando o nome da macro é reconhecido no texto de origem do programa ou nos argumentos de alguns outros comandos de pré-processador, ele é tratado como uma chamada para aquela macro. O nome da macro é substituído por uma cópia do corpo da macro. Se a macro aceitar argumentos, os argumentos reais após o nome da macro serão substituídos por parâmetros formais no corpo da macro. O processo de substituição de uma chamada de macro pela cópia processada do corpo é chamado de “expansão” da chamada de macro.

Em termos práticos, há dois tipos de macros. Macros "do tipo objeto" não aceitam argumentos, enquanto macros "do tipo função" pode ser definidas para aceitarem argumentos para que pareçam e ajam como chamadas de função. Como as macros não gerenciam chamadas de função reais, às vezes você pode fazer com que os programas sejam executados mais rapidamente substituindo chamadas de função por macros. (Em C++, as funções embutidas frequentemente são o método preferencial.) No entanto, as macros podem criar problemas se você não defini-las e usá-las com cuidado. Você pode precisar usar parênteses em definições de macro com argumentos para preservar a precedência apropriada em uma expressão. Além disso, as macros podem não manipular corretamente expressões com efeitos colaterais. Consulte a `getrandom` exemplo na [o #define diretiva](../preprocessor/hash-define-directive-c-cpp.md) para obter mais informações.

Depois que você tiver definido uma macro, não poderá redefini-la como um valor diferente sem descartar primeiro a definição original. No entanto, você pode redefinir a macro com exatamente a mesma definição. Assim, a mesma definição pode aparecer mais de uma vez em um programa.

O `#undef` diretiva remove a definição de uma macro. Depois que você tiver removido a definição, poderá redefinir a macro com um valor diferente. [O # diretiva define](../preprocessor/hash-define-directive-c-cpp.md) e [#undef](../preprocessor/hash-undef-directive-c-cpp.md) Discuta o `#define` e `#undef` diretivas, respectivamente.

Para obter mais informações, consulte

- [Macros e C++](../preprocessor/macros-and-cpp.md)

- [Macros variadic](../preprocessor/variadic-macros.md)

- [Macros predefinidas](../preprocessor/predefined-macros.md)

## <a name="see-also"></a>Consulte também

[Referência de pré-processador do C/C++](../preprocessor/c-cpp-preprocessor-reference.md)