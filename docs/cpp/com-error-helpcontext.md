---
title: _com_error::HelpContext
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpContext
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
ms.openlocfilehash: a421a7fd7fa0817c74dac66946e28928b2ad82dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155079"
---
# <a name="comerrorhelpcontext"></a>_com_error::HelpContext

**Seção específica da Microsoft**

Chama a função `IErrorInfo::GetHelpContext`.

## <a name="syntax"></a>Sintaxe

```
DWORD HelpContext( ) const throw( );
```

## <a name="return-value"></a>Valor de retorno

Retorna o resultado da `IErrorInfo::GetHelpContext` para o `IErrorInfo` registrado no `_com_error` objeto. Se nenhum `IErrorInfo` é registrado, ele retorna um zero.

## <a name="remarks"></a>Comentários

Qualquer falha ao chamar o `IErrorInfo::GetHelpContext` método é ignorado.

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[Classe _com_error](../cpp/com-error-class.md)