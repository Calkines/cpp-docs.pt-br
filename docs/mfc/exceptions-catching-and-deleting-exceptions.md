---
title: 'Exceções: Obtendo e excluindo exceções'
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
ms.openlocfilehash: 511850c3c17a4eb70529202f4b0c2b36132fc8ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173259"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Exceções: Obtendo e excluindo exceções

As instruções e os exemplos a seguir mostram como detectar e eliminar as exceções. Para obter mais informações sobre o **tente**, **catch**, e **lançar** palavras-chave, consulte [tratamento de exceções de C++](../cpp/cpp-exception-handling.md).

Seus manipuladores de exceção devem excluir os objetos de exceção tratam, pois a falha ao excluir a exceção faz com que um vazamento de memória sempre que esse código captura uma exceção.

Sua **catch** bloco deve excluir uma exceção quando:

- O **catch** bloco lançar uma nova exceção.

   Obviamente, você não pode excluir a exceção se você lançar a mesma exceção novamente:

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- Execução retorna de dentro de **catch** bloco.

> [!NOTE]
>  Ao excluir uma `CException`, use o `Delete` a função de membro para excluir a exceção. Não use o **excluir** palavra-chave, pois ele pode falhar se a exceção não está no heap.

#### <a name="to-catch-and-delete-exceptions"></a>Para capturar e excluir exceções

1. Use o **tente** palavra-chave para configurar um **tente** bloco. Executar quaisquer instruções de programa que podem gerar uma exceção dentro de um **tente** bloco.

   Use o **catch** palavra-chave para configurar um **catch** bloco. Coloque o código de tratamento de exceção em um **catch** bloco. O código na **catch** bloco é executado somente se o código dentro a **tente** bloco lançar uma exceção do tipo especificado no **catch** instrução.

   A seguir mostra de esqueleto como **tente** e **catch** blocos normalmente são organizados:

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Quando uma exceção é lançada, o controle passa para a primeira **catch** bloco cuja declaração de exceção corresponde ao tipo da exceção. Seletivamente pode lidar com diferentes tipos de exceções com sequencial **catch** bloqueia conforme listado abaixo:

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Para obter mais informações, consulte [exceções: Convertendo de Macros de exceção MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Consulte também

[Tratamento de Exceção](../mfc/exception-handling-in-mfc.md)
