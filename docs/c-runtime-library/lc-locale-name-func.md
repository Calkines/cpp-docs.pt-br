---
title: ___lc_locale_name_func
ms.date: 11/04/2016
api_name:
- ___lc_locale_name_func
api_location:
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___lc_locale_name_func
helpviewer_keywords:
- ___lc_locale_name_func
ms.assetid: ef858308-872e-43de-95e0-9b1b4084343e
ms.openlocfilehash: abc1ade393538586ad07f57e6838591833c9948b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944237"
---
# <a name="___lc_locale_name_func"></a>___lc_locale_name_func

Função CRT interna. Recupera o nome da localidade atual do thread.

## <a name="syntax"></a>Sintaxe

```cpp
wchar_t** ___lc_locale_name_func(void);
```

## <a name="return-value"></a>Valor de retorno

Um ponteiro para uma cadeia de caracteres contendo o nome da localidade atual do thread.

## <a name="remarks"></a>Comentários

`___lc_locale_name_func` é uma função CRT interna usada por outras funções CRT para obter o nome da localidade atual do armazenamento local do thread para dados CRT. Essas informações também estão disponíveis usando a função [_get_current_locale](../c-runtime-library/reference/get-current-locale.md) ou as funções [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).

Funções CRT internas são específicas da implementação e estão sujeitas a alteração em cada versão. Não recomendamos usá-las no seu código.

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|`___lc_locale_name_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Consulte também

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
