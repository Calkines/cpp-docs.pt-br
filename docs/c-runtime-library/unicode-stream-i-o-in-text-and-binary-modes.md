---
title: E/S de fluxo Unicode em modos de texto e binários
ms.date: 11/04/2016
f1_keywords:
- c.io
helpviewer_keywords:
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
ms.openlocfilehash: c16d2f74856bb42dfd6ffc4e1af7306f6edd97fb
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745977"
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>E/S de fluxo Unicode em modos de texto e binários

Quando a rotina de E/S de fluxo Unicode (como **fwprintf**, **fwscanf**, **fgetwc**, **fputwc**, **fgetws** ou **fputws**) opera em um arquivo que está aberto no modo de texto (o padrão), dois tipos de conversões de caractere ocorrem:

- Conversão de Unicode em MBCS ou MBCS para Unicode. Quando uma função de E/S de fluxo Unicode opera no modo de texto, presume-se que o fluxo de origem ou destino é uma sequência de caracteres multibyte. Portanto, as funções de entrada de fluxo Unicode convertem caracteres multibyte em caracteres largos (como por uma chamada à função **mbtowc**). Pelo mesmo motivo, as funções de saída de fluxo Unicode convertem caracteres largos em caracteres multibyte (como por uma chamada à função **wctomb**).

- Retorno de carro – Conversão de linha (CR-LF). Essa conversão ocorre antes do MBCS – conversão Unicode (para funções de entrada de fluxo Unicode) e depois da conversão de Unicode – MBCS (para funções de saída de fluxo Unicode). Durante a entrada, cada combinação de retorno de carro – linha é convertida em um caractere de avanço de linha único. Durante a saída, cada caractere de avanço de linha é convertido em uma combinação de retorno de carro – avanço de linha.

No entanto, quando uma função de E/S de fluxo Unicode opera no modo binário, o arquivo é considerado como Unicode e nenhuma conversão de CR-LF ou conversão de caractere ocorre durante a entrada ou saída. Use _setmode( _fileno( stdin ), _O_BINARY ); instruções para usar corretamente o wcin em um arquivo de texto UNICODE.

## <a name="see-also"></a>Consulte também

[Rotinas de tempo de execução C universais por categoria](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Entrada e saída](../c-runtime-library/input-and-output.md)<br/>
