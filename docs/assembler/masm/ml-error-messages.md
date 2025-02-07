---
title: Mensagens de erro ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
ms.openlocfilehash: adf2c509c3d8d9110ddb757f809a4bca9199df7a
ms.sourcegitcommit: af580f3a11b19d22288424eac7ceae1bc24ab312
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66355323"
---
# <a name="ml-error-messages"></a>Mensagens de erro ML

As mensagens de erro geradas por componentes MASM se enquadram em três categorias:

- **Erros fatais.** Elas indicam um problema grave que impede que o utilitário conclua seu processo normal.

- **Erros não fatais.** O utilitário pode concluir seu processo. Se isso acontecer, seu resultado não é provavelmente será o item desejado.

- **Avisos.** Essas mensagens indicam condições que podem impedir que você obter os resultados desejados.

Todas as mensagens de erro têm o seguinte formato:

> *Utilitário*: *Nome do arquivo* (*linha*): {*Error_type*} (*código*): *Message_text*

em que:

*Utility*<br/>
O programa que enviou a mensagem de erro.

*Filename*<br/>
O arquivo que contém a condição de geração de erro.

*Linha*<br/>
A linha aproximada em que existe uma condição de erro.

*Error_type*<br/>
Fatal erro, erro ou aviso.

*Código*<br/>
O código de erro exclusivo com 5 ou 6 dígitos.

*Message_text*<br/>
Uma descrição curta e geral da condição de erro.

## <a name="see-also"></a>Consulte também

[Referência do Microsoft Macro Assembler](../../assembler/masm/microsoft-macro-assembler-reference.md)
