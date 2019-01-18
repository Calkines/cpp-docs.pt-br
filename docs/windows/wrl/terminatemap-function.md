---
title: Função TerminateMap
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 17d02ea9cade0301798a5d6625f8eb9a568cb2cc
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335483"
---
# <a name="terminatemap-function"></a>Função TerminateMap

Oferece suporte a infraestrutura do WRL e não se destina a ser usado diretamente do seu código.

## <a name="syntax"></a>Sintaxe

```cpp
inline bool TerminateMap(
   _In_ ModuleBase *module,
   _In_opt_z_ const wchar_t *serverName,
    bool forceTerminate) throw()
```

### <a name="parameters"></a>Parâmetros

*module*<br/>
Um [módulo](module-class.md).

*serverName*<br/>
O nome de um subconjunto de fábricas de classe no módulo especificado pelo parâmetro *módulo*.

*forceTerminate*<br/>
**True** para encerrar a classe fábricas, independentemente de eles estão ativos; **falsos** não encerrar as fábricas de classes se qualquer fábrica estiver ativa.

## <a name="return-value"></a>Valor de retorno

**Verdadeiro** se todas as fábricas de classes foram encerradas; caso contrário, **falso**.

## <a name="remarks"></a>Comentários

Desliga as fábricas de classes no módulo especificado.

## <a name="requirements"></a>Requisitos

**Cabeçalho:** module.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Consulte também

[Namespace Microsoft::WRL::Details](microsoft-wrl-details-namespace.md)