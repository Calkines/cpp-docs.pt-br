---
title: _variant_t::SetString
ms.date: 11/04/2016
f1_keywords:
- _variant_t::SetString
helpviewer_keywords:
- SetString method [C++]
ms.assetid: 816b08e5-6830-46ca-b3d7-7689308b3be3
ms.openlocfilehash: d07e995be0ecd99974356a7516e7c4deee677637
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403263"
---
# <a name="varianttsetstring"></a>_variant_t::SetString

**Seção específica da Microsoft**

Atribui uma cadeia de caracteres a este objeto `_variant_t`.

## <a name="syntax"></a>Sintaxe

```
void SetString(const char* pSrc);
```

#### <a name="parameters"></a>Parâmetros

*pSrc*<br/>
Ponteiro para a cadeia de caracteres.

## <a name="remarks"></a>Comentários

Converte uma cadeia de caracteres ANSI em uma cadeia de caracteres Unicode `BSTR` e a atribui a este objeto `_variant_t`.

**Fim da seção específica da Microsoft**

## <a name="see-also"></a>Consulte também

[Classe _variant_t](../cpp/variant-t-class.md)