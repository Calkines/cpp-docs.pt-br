---
title: Exceções de hardware
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [C++], hardware
- errors [C++], low-level
- errors [C++], hardware
- hardware exceptions [C++]
- low level errors
ms.assetid: 06ac6f01-a8cf-4426-bb12-1688315ae1cd
ms.openlocfilehash: 17775f3b2ee6dfa235c93d0bf0e3335b464aaa69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153665"
---
# <a name="hardware-exceptions"></a>Exceções de hardware

A maioria das exceções padrão reconhecidas pelo sistema operacional são exceções definidas por hardware. O Windows reconhece algumas exceções de software de nível baixo, mas elas geralmente são mais bem tratadas pelo sistema operacional.

O Windows mapeia os erros de hardware de processadores diferentes para os códigos de exceção nesta seção. Em alguns casos, um processador pode gerar somente um subconjunto dessas exceções. O Windows pré-processa informações sobre a exceção e emite o código de exceção apropriado.

As exceções de hardware reconhecidas pelo windows são resumidas na seguinte tabela:

|Código da exceção|Causa da exceção|
|--------------------|------------------------|
|STATUS_ACCESS_VIOLATION|Leitura ou gravação em um local de memória inacessível.|
|STATUS_BREAKPOINT|Encontro de um ponto de interrupção definido por hardware; usado somente por depuradores.|
|STATUS_DATATYPE_MISALIGNMENT|Leitura ou gravação de dados em um endereço que não está alinhado corretamente; por exemplo, as entidades de 16 bits devem ser alinhadas em limites de 2 bytes. (Não aplicável para Intel 80*x*x86 processadores.)|
|STATUS_FLOAT_DIVIDE_BY_ZERO|Divisão do tipo de ponto flutuante por 0,0.|
|STATUS_FLOAT_OVERFLOW|Expoente positivo máximo do tipo de ponto flutuante excedido.|
|STATUS_FLOAT_UNDERFLOW|Magnitude excedida do expoente negativo mais baixo do tipo de ponto flutuante.|
|STATUS_FLOATING_RESEVERED_OPERAND|Usando um formato de ponto flutuante reservado (uso inválido de formato).|
|STATUS_ILLEGAL_INSTRUCTION|Tentativa de executar um código de instrução não definido pelo processador.|
|STATUS_PRIVILEGED_INSTRUCTION|Execução de uma instrução não permitida no modo atual do computador.|
|STATUS_INTEGER_DIVIDE_BY_ZERO|Divisão de um tipo de inteiro por 0.|
|STATUS_INTEGER_OVERFLOW|Tentativa de uma operação que excede o intervalo do inteiro.|
|STATUS_SINGLE_STEP|Execução de uma instrução no modo de etapa única; usado somente por depuradores.|

Muitas das exceções listadas na tabela anterior devem ser tratadas por depuradores, pelo sistema operacional, ou outro código de nível baixo. Com a exceção de erros de inteiro e de ponto flutuante, seu código não deve tratar esses erros. Assim, geralmente você deve usar o filtro de tratamento de exceções para ignorar exceções (avaliado como 0). Caso contrário, você poderá impedir que os mecanismos de nível inferior respondam adequadamente. Você pode, no entanto, tomar precauções apropriadas contra o efeito potencial desses erros de baixo nível [escrever manipuladores de terminação](../cpp/writing-a-termination-handler.md).

## <a name="see-also"></a>Consulte também

[Escrevendo um manipulador de exceção](../cpp/writing-an-exception-handler.md)<br/>
[Tratamento de exceções estruturado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)