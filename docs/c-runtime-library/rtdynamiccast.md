---
title: __RTDynamicCast | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __RTDynamicCast
apilocation:
- msvcr90.dll
- msvcr110.dll
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- __RTDynamicCast
dev_langs:
- C++
helpviewer_keywords:
- __RTDynamicCast
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 85f8b31ee9faec433fa0c9f1ff64d5bfa1e9665a
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161249"
---
# <a name="rtdynamiccast"></a>__RTDynamicCast

Implementação de tempo de execução do operador [dynamic_cast](../cpp/dynamic-cast-operator.md).

## <a name="syntax"></a>Sintaxe

```cpp
PVOID __RTDynamicCast (
   PVOID inptr,
   LONG VfDelta,
   PVOID SrcType,
   PVOID TargetType,
   BOOL isReference
   ) throw(...)
```

#### <a name="parameters"></a>Parâmetros

*inptr*<br/>
Ponteiro para um objeto polimórfico.

*VfDelta*<br/>
Deslocamento do ponteiro de função virtual no objeto.

*SrcType*<br/>
O tipo estático do objeto apontado pelo parâmetro `inptr`.

*TargetType*<br/>
Resultado desejado da conversão.

*isReference*<br/>
**true** se a entrada for uma referência; **false** se a entrada for um ponteiro.

## <a name="return-value"></a>Valor retornado

Ponteiro para o subobjeto apropriado, se for bem-sucedido; caso contrário, **NULL**.

## <a name="exceptions"></a>Exceções

`bad_cast()` se a entrada para `dynamic_cast<>` for uma referência e a conversão falhar.

## <a name="remarks"></a>Comentários

Converte `inptr` em um objeto do tipo `TargetType`. O tipo de `inptr` deve ser um ponteiro se `TargetType` for um ponteiro, ou um l-value se `TargetType` for uma referência. `TargetType` deve ser um ponteiro ou uma referência a um tipo de classe previamente definido ou a um “ponteiro para nulo”.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|__RTDynamicCast|rtti.h|