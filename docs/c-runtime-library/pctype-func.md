---
title: __pctype_func
ms.date: 11/04/2016
api_name:
- __pctype_func
api_location:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: f5dae74dd601df1dc737293a181eca60f5cd23f8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944035"
---
# <a name="__pctype_func"></a>__pctype_func

Recupera um ponteiro para uma matriz de informações de classificação de caracteres.

## <a name="syntax"></a>Sintaxe

```cpp
const unsigned short *__pctype_func(
   )
```

## <a name="return-value"></a>Valor de retorno

Um ponteiro para uma matriz de informações de classificação de caracteres.

## <a name="remarks"></a>Comentários

As informações na tabela de classificação de caracteres destina-se apenas a uso interno e são usadas por várias funções que classificam caracteres do tipo `char`. Para obter mais informações, consulte a seção `Remarks` de [_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md).

## <a name="requirements"></a>Requisitos

|Rotina|Cabeçalho necessário|
|-------------|---------------------|
|__pctype_func|ctype.h|

## <a name="see-also"></a>Consulte também

[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)
